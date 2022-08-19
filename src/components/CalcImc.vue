<template>
  <div class="main">
    <div class="body">
      <p class="title">Calcule seu IMC</p>
      <div class="division-title">
        <div class="inputPeso">
          <div class="labelPeso">
            <p class="peso">Peso</p>
            <p id="resultadoPeso"> Kg </p>
          </div>
          <input type="range" min="0" max="150" value="0" class="estilo" id="valorPeso">
        </div>
        <br>


        <div class="inputAltura">
          <div class="labelAltura">
            <p class="altura">Altura</p>
            <p id="resultadoAltura"></p>
          </div>
          <input type="range" min="1.0" max="2.2" value="1.0" step="0.01" class="estilo" id="valorAltura">
        </div>
      </div>
      <div class="footer">
        <button class="button" v-on:click="CalcImc">Calcular</button>

        <p class="resultadoFinal">IMC: {{ this.result }} {{ imc }}</p>
      </div>
    </div>
  </div>
</template>


<script>
export default {

  mounted() {


    function rangePeso() {
      let resultadoPeso = document.getElementById("resultadoPeso");
      let valorPeso = document.getElementById("valorPeso").value;
      resultadoPeso.innerHTML = valorPeso + 'Kg'
    }

    rangePeso()
    document.addEventListener("change", rangePeso);

    function rangeAltura() {
      let resultadoAltura = document.getElementById("resultadoAltura");
      let valorAltura = document.getElementById("valorAltura").value;
      resultadoAltura.innerHTML = valorAltura + 'm'
    }

    rangeAltura()
    document.addEventListener("change", rangeAltura);
  },
  data() {
    return {
      result: "",
      imc: ""
    }
  },
  methods: {
    CalcImc() {
      let valorAltura = document.getElementById("valorAltura").value;
      let valorPeso = document.getElementById("valorPeso").value;

      this.result = valorPeso / (valorAltura * valorAltura)
      if (valorAltura == 1 && valorPeso == 0) {
        this.imc = "invalid"
        this.result = null
      }
      else if (valorPeso == 0) {
        this.imc = "invalid"
        this.result = null
      }
      else if (this.result <= 18.5) {
        this.imc = "(Abaixo do Peso).";
      } else if (this.result <= 24.9) {
        this.imc = "(Peso Normal).";
      } else if (this.result <= 29.9) {
        this.imc = "(Sobrepeso).";
      } else if (this.result <= 34.9) {
        this.imc = "(Obesidade Grau I).";
      } else if (this.result <= 39.9) {
        this.imc = "(Obesidade Grau II).";
      } else if (this.result > 40) {
        this.imc = "(Obesidade Mórbida).";
      }
      this.result = this.result.toFixed(2)
    }
  },
};
</script>

<style scoped>
@import './CalcImc.css'
</style>


