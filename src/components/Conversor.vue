<template>
  <div class="main">
    {{moneyB}} Para {{moneyA}}
    <div class="card">
      <div class="body">
        <div class="conteudo">
          <div class="input-group">
            <input
              type="text"
              v-on:keydown="getUrlConverter()"
              class="form-control"
              v-model="moneyA_value"
              v-bind:placeholder="moneyA"
            />
            <div class="input-group-append">
              <button type="button" class="btn btn-success" v-on:click="getUrlConverter()">
                <span class="fa fa-usd"></span>
              </button>
            </div>
          </div>
        </div>
        <h2>{{moneyB_value}}</h2>
      </div>
    </div>
  </div>
</template>

<script>
import "bootstrap/dist/css/bootstrap.css";
import "font-awesome/css/font-awesome.css";
export default {
  name: "Conversor",
  props: ["moneyA", "moneyB"],
  data: function() {
    return {
      moneyA_value: "",
      moneyB_value: 0
    };
  },
  methods: {
    getUrlConverter: function() {
      let url = "https://api.exchangerate-api.com/v4/latest/" + this.moneyB;

      fetch(url)
        .then(response => {
          return response.json();
        })
        .then(data => {
          let quotation = data.rates[this.moneyA];
          this.moneyB_value = parseFloat(quotation * this.moneyA_value).toFixed(
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