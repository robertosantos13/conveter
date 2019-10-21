<template>
  <div class="main">
    {{moedaA}} Para {{moedaB}}
    <div class="card">
      <div class="body">
        <div class="conteudo">
          <div class="input-group">
            <input
              type="text"
              v-on:keydown="converter()"
              class="form-control"
              v-model="moedaA_value"
              v-bind:placeholder="moedaA"
            />
            <div class="input-group-append">
              <button type="button" class="btn btn-success" v-on:click="converter()">
                <span class="fa fa-usd"></span>
              </button>
            </div>
          </div>
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
.main {
  width: 100%;
  margin-right: 10%;
  margin-left: 10%;
}
.conteudo {
  display: flex;
}
.card h2 {
  margin-top: 10px;
  margin-left: 6px;
}
</style>