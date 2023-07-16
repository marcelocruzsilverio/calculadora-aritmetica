<script setup>
const props = defineProps(['alternateOperationSymbol', 'operations', 'unhideResult', 'getFilterValue', 'getFirstInputValue', 'getSecondInputValue'])
</script>


<template>
    <form>
        <h2>Escolha a operação desejada</h2>
        <select @change="props.getFilterValue">
            <option value="choose" selected disabled>Selecionar</option>
            <option value="sum">Somar</option>
            <option value="subtract">Subtrair</option>
            <option value="multiply">Multiplicar</option>
            <option value="divide">Dividir</option>
        </select>
        <input @keyup="props.getFirstInputValue" type="number" placeholder="digite o primeiro valor">
        <span v-text="props.alternateOperationSymbol"></span>
        <input @keyup="props.getSecondInputValue" type="number" placeholder="digite o segundo valor">
        <label>Resultado: </label>
        <span class="result" v-text="props.operations" v-if="props.unhideResult !== 'choose'"></span>
    </form>
</template>

<style scoped>
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
    form h2 {
        font-size: 1.2rem;
    }
}
</style>