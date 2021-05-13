<template>
  <div>
    <h3>Cálculo de IMC</h3>
    <p>
      Digite seu peso (em kg):
      <input autofocus type='text' placeholder='Ex: 85' id='peso' v-model="peso">
    </p>
    <p>
      Digite sua altura (em metros):
      <input type='text' placeholder='Ex: 1.71' id='altura' v-model="altura">
    </p>

    <p>
      <input type="button" value="Calcular" @click="calcularImc()">
      <input type="button" value="Novo Cálculo" @click="limpar()">
    </p>
    <div v-if="resultado_imc" class="resultadoImc">
      <p>
        IMC: {{ resultado_imc }}
        <br />
        Classificação: {{ resultado_classificacao }}
      </p>
    </div>
    <br /><br />

  </div>
</template>

<script>
export default {
  name: 'app',
  methods: {
    calcularImc : function() {
      if(this.peso == null){
        alert("Digite um peso");
        peso.focus();
      }else if(this.altura == null){
        alert("Digite uma altura");
        altura.focus();
      }else if(this.altura == '0'){
        alert("Altura não pode ser zero");
        this.altura = null,
        altura.focus();
      }else{
        const altura = this.altura.replace(",",".");
        const peso = this.peso.replace(",",".");
        let calculo = (peso / (altura * altura));

        this.resultado_imc = calculo.toFixed(1);
        this.calcularResultado();
      }
      
    },
    calcularResultado : function(){
      if (this.resultado_imc < 18.5) {
        this.resultado_classificacao = "abaixo do peso ideal";
      } else if (this.resultado_imc >= 18.5 && this.resultado_imc <= 24.9) {
        this.resultado_classificacao = "Peso ideal";
      } else if (this.resultado_imc >= 25 && this.resultado_imc < 30) {
        this.resultado_classificacao = "Sobrepeso";
      } else if (this.resultado_imc >= 30 && this.resultado_imc < 35) {
        this.resultado_classificacao = "Obesidade grau I";
      }else if (this.resultado_imc >= 35 && this.resultado_imc < 40) {
        this.resultado_classificacao = "Obesidade grau II";
      } else {
        this.resultado_classificacao = "Obesidade grau III";
      }

    },
    limpar: function() {
      this.altura = null,
      this.peso = null,
      this.resultado_imc = "",
      this.resultado_classificacao = ""
    }
  },
  data() {
    return{
      altura: null,
      peso: null,
      resultado_imc: "",
      resultado_classificacao: ""
    }

  },
}
</script>

<style>
  body{
    margin: 10px;
  }
  .resultadoImc{
    background-color: #94EBC5;
    padding: 3px;
    font-weight: bold;
    float: center;
  }
  h3{
    text-align: center;
  }
</style>
