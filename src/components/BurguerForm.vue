<template>
  <div>
    <p>Componente de mensagem</p>
    <div>
        <form id="BurguerForm" @submit="createBurger">
            <div class="input-container">
                <label for="name">Nome:</label>
                <input type="text" id="nome" name="name" v-model="nome" placeholder="Digite o seu nome">
            </div>
            <div class="input-container">
                <label for="pao">Escolha o seu pão:</label>
                <select name="pao" id="pao" v-model="pao">
                    <option value="">Selecione seu pão</option>
                    <option v-for="pao in paes" :key="pao.id" :value="pao.tipo">{{ pao.tipo }}</option>
                </select>
            </div>
            <div class="input-container">
                <label for="carne">Escolha a carne do seu Burguer:</label>
                <select name="carne" id="carne" v-model="carne">
                    <options>Selecione a carne</options>
                    <option v-for="carne in carnes" :key="carne.id" :value="carne.tipo">{{ carne.tipo }}</option>
                </select>
            </div>
            <div id="opcionais-container" class="input-container">
                <label id="opcionais-title" for="opcionais">Selecione os opcionais:</label>
                <div class="checkbox-container" v-for="opcional in opcionaisdata" :key="opcional.id">
                    <input type="checkbox" name="opcionais" v-model="opcionais" :value="opcional.tipo">
                    <span>{{opcional.tipo}}</span>
                </div>
            </div>
            <div class="input-container">
                <input type="submit" class="submit-btn" value="Criar Meu Burguer">               
            </div>

        </form>
    </div>
  </div>
</template>

<script>
export default {
    name: 'BurguerForm',
    data(){
        return {
            paes: null,
            carnes: null,
            opcionaisdata: null,
            nome: null,
            pao: null,
            carne: null,
            opcionais: [],
            msg: null
        }
    },
    methods: {
        async getIngredientes(){

            const req = await fetch("http://localhost:3000/ingredientes")
            const data = await req.json();

            this.paes = data.paes;
            this.carnes = data.carnes;
            this.opcionaisdata = data.opcionais;
        },

        async createBurger(e){
        e.preventDefault(); 

        const data = {
            nome: this.nome,
            carne: this.carne,
            pao: this.pao,
            opcionais: Array.from(this.opcionais),
            status: "Solicitado"  
        }

        const dataJson = JSON.stringify(data);

        const req = await fetch("http://localhost:3000/burgers", {
            method: "POST",
             headers: {"Content-Type": "aplication/json"},
            body: dataJson
        });

        const res = await req.json();

        //Colocar msg de sistema

        //limpar Campos
        this.nome ="";
        this.carne ="";
        this.pao ="";
        this.opcionais ="";
    }

    },
    mounted(){
        this.getIngredientes() 
    }
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
    #opcionais-title{
        width: 100%;
    }
    .checkbox-container{
        font-weight: bold;
        display: flex;
        align-items: flex-start;
        width: 50%;
        margin-bottom: 20px;
    }
    .checkbox-container span,
    .checkbox-container input {
        width: auto;
    }

    .submit-btn {
        background-color: #000;
        color: #FCBA03;
        font-weight: bold;
        border: 2px solid #000;
        padding: 10px;
        font-size: 10px;
        margin: 0 auto;
        cursor: pointer;
        transition: -5s;
    }

    .submit-btn:hover {
        background-color: transparent;
        color:#000;
    }
</style>