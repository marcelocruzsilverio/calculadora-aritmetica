<script setup>

</script>

<template>
  <div class="container container-flex">
    <div class="content">

      <header>
        <h1>Calculadora Aritmética</h1>
      </header>
      <form>
        <h2>Escolha a operação desejada</h2>
        <select>
          <option value="somar">Somar</option>
          <option value="subtrair">Subtrair</option>
          <option value="multiplicar">Multiplicar</option>
          <option value="dividir">Dividir</option>
        </select>
        <input type="number" placeholder="digite o primeiro número">
        <span>+</span>
        <input type="number" placeholder="digite o segundo número">
        <label for="">Resultado: </label>
        <input type="number">
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

body {}

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

}


form input:hover {
  background-color: #77a2f3;
}

form input::placeholder {
  font-size: 1rem;
  color: #072f79;
}

form input[type="number"]::-webkit-inner-spin-button {
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
}

span {
  font-size: 1.5rem;
  color: #fff;
}
</style>
