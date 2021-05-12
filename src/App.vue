<template>
  <div>
    <h3>Cálculo de IMC</h3>
    <p>
      Digite seu peso (em kg):
      <input type='number' id='peso' >
    </p>
    <p>
      Digite sua altura (em cm):
      <input autofocus type='number' id='altura' >
    </p>

    <p>
      <input type="button" value="Calcular" v-on:click="calcularImc()">
    </p>
    <p>
      IMC:
      {{ resultado }}
    </p>
    <br /><br />

    <p>
      Abaixo de 18,5 = abaixo do peso ideal <br>
      Entre 18,5 e 24,9 = peso ideal <br>
      Entre 25,0 e 29,9 = sobrepeso <br>
      Entre 30,0 e 34,9 = obesidade grau I <br>
      Entre 35,0 e 39,9 = obesidade grau II <br>
      Entre 40 e acima = obesidade grau III <br>
    </p>

  </div>
</template>

<script>
export default {
  name: 'app',
  methods: {
    calcularImc : function() {
				// event.preventDefault();

        const peso = this.$el.querySelector('#peso');
        const altura = this.$el.querySelector('#altura');
        let total = this.$el.querySelector('#total');

				let calculo = (parseInt(peso.value) / (parseInt(altura.value) * parseInt(altura.value))) * 10000;
        console.log(calculo);

				this.resultado += calculo.toFixed(1);
			}

  },
  data () {
    return {
      resultado: 'Seu IMC é '
    }
  }
}
</script>

<style>
</style>
