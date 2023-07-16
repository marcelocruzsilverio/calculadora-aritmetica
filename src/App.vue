<script setup>
import { reactive } from 'vue';
import Header from './components/Header.vue';
import Form from './components/Form.vue';


const state = reactive({
  filter: 'choose',
  firstNumber: '',
  secondeNumber: '',
  clean: null,
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

const unhideResult = () => {
  const filter = state.filter
  if (filter === 'choose') {
    return 'choose'
  } else {
    return '';
  }
}




function clearFirstInput() {
  const clean = state.clean
  return state.firstNumber = clean
}

function clearSecondInput() {
  const clean = state.clean
  return state.secondeNumber = clean
}


</script>

<template>
  <div class="container container-flex">
    <div class="content">
      <Header />
      <Form :alternate-operation-symbol="alternateOperationSymbol()" :operations="operations()"
        :unhide-result="unhideResult()" :get-filter-value="event => state.filter = event.target.value"
        :get-first-input-value="event => state.firstNumber = event.target.value"
        :get-second-input-value="event => state.secondeNumber = event.target.value" :clear-first-input="clearFirstInput"
        :clear-first-number="state.firstNumber" :clear-second-input="clearSecondInput"
        :clear-second-number="state.secondeNumber" />
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

@media (max-width: 700px) {
  .content {
    width: 90%;
  }
}
</style>
