<template>
  <div id="app">
    <div class="text-center text-warning">
      <h1>
        Conversor de moedas
        <span class="fa fa-money text-success" arial-hidden="true"></span>
      </h1>
      <p
        class="text-secondary"
      >Este é um simples projeto de conversor de moedas para desenvolvimento pessoal.</p>
    </div>
    <div class="container">
      <Conversor moedaA="USD" moedaB="BRL" />
      <Conversor moedaA="BRL" moedaB="USD" />
    </div>
    <div class="container">
      <Conversor moedaA="EUR" moedaB="BRL" />
      <Conversor moedaA="BRL" moedaB="EUR" />
    </div>
    <div class="container">
      <Conversor moedaA="CAD" moedaB="BRL" />
      <Conversor moedaA="BRL" moedaB="CAD" />
    </div>
  </div>
</template>

<script>
import Conversor from "./components/Conversor";
export default {
  name: "app",
  components: {
    Conversor
  }
};
</script>
  
<style>
body {
  background: #f1f1f1;
  font-family: "Trebuchet MS", "Lucida Sans Unicode", "Lucida Grande",
    "Lucida Sans", Arial, sans-serif;
}
.container {
  display: flex;
  justify-content: space-around;
  margin-bottom: 25px;
}
.text-center {
  margin-bottom: 60px;
  margin-top: 30px;
}
</style>
