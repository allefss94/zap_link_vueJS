<template>
  <div class="container">
    <div class="row">
      <div class="col-12">
        <form v-on:submit.prevent="onSubmit">
          <div class="form-group">
            <label for="">Número</label>
            <input type="text" class="form-control" v-model="input.numero" />
            <small>O número que irá receber as mensagens.</small>
          </div>
        </form>
        <form v-on:submit.prevent="onSubmit">
          <div class="form-group">
            <label for="">Menssagem</label>
            <input type="text" class="form-control" v-model="input.menssagem" />
            <small>A menssagem padrão.</small>
          </div>
        </form>
      </div>
      <div class="col-12" v-show="link.numero.length === 11">
        <textarea :value="link.url" id="link" class="form-control"></textarea>
        <button class="btn mr-3 btn-primary" v-clipboard="() => link.url">
          Copiar
        </button>
        <a :href="link.url" target="_blank" class="btn btn-primary text-white"
          >Testar link</a
        >
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "GeradorDeLink",
  data: function() {
    return {
      input: {
        numero: "",
        menssagem: "",
      },
    };
  },
  computed: {
    link: function() {
      let numero = this.input.numero.replace(/[^0-9]+/g, "");
      let menssagem = this.input.menssagem.replace(/ /g, "%20");
      let url = `https://api.whatsapp.com/send?phone=55${numero}&text=${menssagem}`;
      return { url, numero };
    },
  },
};
</script>
