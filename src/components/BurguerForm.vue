<template>
  <div>
    <p>Componente de mensagem</p>
    <div>
        <form id="BurguerForm">
            <div class="input-container">
                <label for="name">Nome:</label>
                <input type="text" id="nome" name="name" v-model="nome" placeholder="Digite o seu nome">
            </div>
            <div class="input-container">
                <label for="pao">Escolha o seu pão:</label>
                <select name="pao" id="pao" v-model="pao">
                    <option value="">Selecione seu pão</option>
                    <option value="integral">Integral</option>
                </select>
            </div>
            <div class="input-container">
                <label for="carne">Escolha a carne do seu Burguer:</label>
                <select name="carne" id="carne" v-model="carne">
                    <option value="">Selecione a carne</option>
                    <option value="boi">Boi</option>
                </select>
            </div>
            <div class="input-container">
                <label id="opcionais-title" for="opcionais">Selecione os opcionais:</label>
                <div class="checkbox-container">
                    <input type="checkbox" name="opcionais" v-model="opcionais" value="salame">
                    <span>salame</span>
                </div>
            </div>
            <div class="input-container">
                <input type="submit" class="submit.btn" value="Criar Meu Burguer">               
            </div>

        </form>
    </div>
  </div>
</template>

<script>
export default {
    name: 'BurguerForm',

}
</script>

<style>
    #BurguerForm {
        max-width: 400px;
        margin: 0 auto;
    }
    .input-container {
        display: flex;
        flex-direction: column;
        margin-bottom: 20px;

    }
    label {
        font-weight: bold;
        margin-bottom: 15px;
        color: #222;
        padding: 5px 10px;
        border-left: 4px solid #FCBA03;
    }

    input, select {
        padding: 5px 10px;
        width: 300px;
    }
    #opcionais-container{
        flex-direction: row;
        flex-wrap: wrap;
    }

</style>