<template>
  <div class="main">
    {{moedaA}} Para {{moedaB}}
    <div class="card">
      <div class="body">
        <div class="conteudo">
          <input
            type="text"
            class="form-control"
            v-model="moedaA_value"
            v-bind:placeholder="moedaA"
          />
          <input type="button" class="btn btn-danger" v-on:click="converter" value="converter" />
        </div>
        <h2>{{moedaB_value}}</h2>
      </div>
    </div>
  </div>
</template>

<script>
import "bootstrap/dist/css/bootstrap.css";
import "font-awesome/css/font-awesome.css";
export default {
  name: "Conversor",
  props: ["moedaA", "moedaB"],
  data: function() {
    return {
      moedaA_value: "",
      moedaB_value: 0
    };
  },
  methods: {
    converter: function() {
      let url = "https://api.exchangerate-api.com/v4/latest/" + this.moedaB;

      fetch(url)
        .then(response => {
          return response.json();
        })
        .then(json => {
          let cotacao = json.rates[this.moedaA];
          this.moedaB_value = parseFloat(cotacao * this.moedaA_value).toFixed(
            2
          );
        });
    }
  }
};
</script>

<style scoped>
.conteudo {
  display: flex;
}
.card h2 {
  margin-top: auto;
}
</style>