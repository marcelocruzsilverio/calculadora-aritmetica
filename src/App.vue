<script setup>
import { reactive } from 'vue';


const state = reactive({
  filter: 'choose',
  firstNumber: 0,
  secondeNumber: 0,
  message: 'Digite um valor'
})


const alternateOperationSymbol = () => {
  const filter = state.filter;

  switch (filter) {
    case 'sum':
      return '+';
    case 'subtract':
      return '-';
    case 'multiply':
      return '*'
    case 'divide':
      return '/'
  }
}

const sum = () => Number(state.firstNumber) + Number(state.secondeNumber);
const subtract = () => Number(state.firstNumber) - Number(state.secondeNumber);
const multiply = () => Number(state.firstNumber) * Number(state.secondeNumber);
const divide = () => {
  if (state.firstNumber > 0) {
    let result = 0
    result = Number(state.firstNumber) / Number(state.secondeNumber);
    return result.toFixed(2)
  } else {
    return '0'
  }
}

const operations = () => {
  const filter = state.filter;


  switch (filter) {
    case 'sum':
      return sum();
    case 'subtract':
      return subtract();
    case 'multiply':
      return multiply();
    case 'divide':
      return divide();
  }

}

const showResult = () => {
  const filter = state.filter
  if (filter === 'choose') {
    return 'choose'
  } else {
    return '';
  }
}


</script>

<template>
  <div class="container container-flex">
    <div class="content">
      <header>
        <h1>Calculadora Aritmética</h1>
      </header>
      <form>
        <h2>Escolha a operação desejada</h2>
        <select @change="event => state.filter = event.target.value">
          <option value="choose" selected>Selecionar</option>
          <option value="sum">Somar</option>
          <option value="subtract">Subtrair</option>
          <option value="multiply">Multiplicar</option>
          <option value="divide">Dividir</option>
        </select>
        <input @keyup="event => state.firstNumber = event.target.value" type="number"
          placeholder="digite o primeiro valor">
        <span v-text="alternateOperationSymbol()"></span>
        <input @keyup="event => state.secondeNumber = event.target.value" type="number"
          placeholder="digite o segundo valor">
        <label>Resultado: </label>
        <!-- <input type="number" v-model="operations"> -->
        <span class="result" v-text="operations()" v-if="showResult() !== 'choose'"></span>
      </form>
    </div>
  </div>
</template>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: Roboto, sans-serif;

}


.container {
  max-width: 1024px;
  width: 100%;
  margin: 0 auto;
  height: 100vh;


}

.container-flex {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.content {
  background-color: #07245a;
  padding: 24px;
  border-radius: 16px;
  width: 70%;
}

header h1 {
  margin-bottom: 24px;
  text-align: center;
  font-size: 2.5rem;
  color: #fff;

}

select {
  margin-bottom: 16px;
  padding: 8px;
  border-radius: 12px;
  outline-color: #77a2f3;
  border: none;
  font-size: 1rem;
  color: #072f79;
  font-weight: bold;
  text-align: center;
  appearance: none;
}

select option {
  font-size: 1rem;
  color: #072f79;
}

form {
  display: flex;
  flex-direction: column;
  /* justify-content: center; */
  align-items: center;
}

form input {
  outline-color: #77a2f3;
  margin: 16px 0;
  padding: 16px;
  border-radius: 12px;
  border: none;
  font-size: 1rem;
  text-align: center;
  -moz-appearance: textfield;
  appearance: textfield;

}


form input:hover {
  background-color: #77a2f3;
}

form input::placeholder {
  font-size: 1rem;
  color: #072f79;
}

form input[type="number"]::-webkit-inner-spin-button,
input[type="number"]::-webkit-outer-spin-button {
  -webkit-appearance: none;
}

form h2 {
  text-align: center;
  margin-bottom: 16px;
  color: #c3c3c3;
  font-size: 1.5rem;
}

form label {
  color: #fff;
  border-bottom: 1px solid #fff;
  margin-bottom: 8px;
}

span {
  font-size: 1.5rem;
  color: #fff;
}

.result {
  border: 1px solid #77a2f3;
  padding: 16px;
  background-color: #12e752;
  color: #07245a;
}

@media (max-width: 700px) {
  .content {
    width: 90%;
  }

  header h1 {
    font-size: 2rem;
  }

  form h2 {
    font-size: 1.2rem;
  }
}
</style>
