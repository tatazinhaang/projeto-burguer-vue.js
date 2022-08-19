<template>
   <div>
   <Message :msg="msg" v-show="msg" />
   </div>
   <div>
    <form id="burger-form" @submit="createBurger">
        <div class="input-container">
            <label for="name">Nome do cliente:</label>
            <input type="text" id="name" name="name" v-model="name" placeholder="Digite o seu nome">
        </div>
        <div class="input-container">
            <label for="pao">Escolha o pão:</label>
            <select name="pao" id="pao" v-model="pao">
                <option value="">Selecione o seu pão</option>
                <option v-for="pao in paes" :key="pao.id" :value="pao.tipo">{{ pao.tipo }}</option>
            </select>
        </div>
        <div class="input-container">
            <label for="carne">Escolha a carne:</label>
            <select name="carne" id="carne" v-model="carne">
                <option value="">Selecione o tipo de carne</option>
                <option v-for="carne in carnes" :key="carne.id" :value="carne.tipo">{{ carne.tipo }}</option>
            </select>
        </div>
        <div id="opcionais-container" class="input-container">
            <label id="opcionais-title" for="opcionais">Adicionar opcionais:</label>
            <div class="checkbox-container" v-for="opcional in opcionaisdata" :key="opcional.id">
                <input type="checkbox" name="opcionais" v-model="opcionais" :value="opcional.tipo">
                <span>{{ opcional.tipo }}</span>
            </div>
        </div>
        <div class="input-container">
           <input type="submit" class="submit-btn" value="Criar meu Burger">
        </div>
    </form>
   </div>
</template>

<script>

import Message from './Message.vue';

export default {
    name: "BurgerForm",
    data() {
        return {
            paes: null,
            carnes: null,
            opcionaisdata: null,
            name: null,
            pao: null,
            carne: null,
            opcionais: [],
            msg: null
        }
    },
    methods: {
       async getIngredientes() {
        const req = await fetch("http://localhost:3000/ingredientes");
        const data = await req.json();

       this.paes = data.paes;
       this.carnes = data.carnes;
       this.opcionaisdata = data.opcionais;
       
       },
       async createBurger(e) {
        e.preventDefault();

        const data = {
            name: this.name,
            carne: this.carne,
            pao: this.pao,
            opcionais: Array.from(this.opcionais),
            status: "Solicitado"
        }

        const dataJson = JSON.stringify(data);

        const req = await fetch("http://localhost:3000/burgers", {
            method: "POST",
            headers: {"Content-Type": "application/json"},
            body: dataJson
        });
        
        const res = await req.json();

        this.msg = `Pedido Nº ${res.id} realizado com sucesso`;

        setTimeout(() => this.msg = "", 3000);

        this.name = "";
        this.carne = "";
        this.pao = "";
        this.opcionais = [];

       }
    },
    mounted() {
        this.getIngredientes();
    },
    components: {
        Message
    }
}
</script>

<style scoped>
    #burger-form {
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
        border-left: 4px solid #bd9937;
    }

    input, select {
        padding: 5px 10px;
        width: 400px;
    }

    #opcionais-container {
        flex-direction: row;
        flex-wrap: wrap;
    }

    #opcionais-title {
        width: 100%;
    }

    .checkbox-container {
        display: flex;
        align-items: flex-start;
        width: 50%;
        margin-bottom: 20px;
    }

    .checkbox-container span,
    .checkbox-container input {
        width: auto;
    }

     .checkbox-container span {
        margin-left: 6px;
        font-weight: bold;
        color: #222;
    }

    .submit-btn {
        background-color: #e2b167;
        color: #222;
        font-weight: bold;
        border: 1px solid #222;
        font-size: 16px;
        padding: 7px;
        letter-spacing: 1px;
        margin: 0 auto;
        cursor: pointer;
        transition: .5s;
    }

     .submit-btn:hover {
        background-color: transparent;
        color: rgb(7, 7, 7);
     }
</style>