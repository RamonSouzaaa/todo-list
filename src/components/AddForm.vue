<template>
    <div id="addForm">
        <form @submit.prevent="add(nome)">
            <div class="column-input">
                <input 
                    type="text" 
                    v-model="nome"
                    maxlength="50"
                    placeholder="Digite o nome do item"
                />
            </div>
            <div class="column-button">
                <button>Adicionar</button>
            </div>
        </form>
    </div>
</template>

<script>
    export default {
        name: 'AddForm',
        data() {
            return {
                nome: ''
            }
        },
        methods: {
            add(nome){
                this.$emit('addItem', nome)
                this.nome = ''
            }
        }
    }
</script>

<style scoped>
    @font-face {
      font-family: 'Rubik-Bold';
      src: url('../fonts/Rubik/Rubik-Bold.ttf');
    }
   
    @font-face {
        font-family: 'Rubik-Regular';
        src: url('../fonts/Rubik/Rubik-Regular.ttf');
    }

    #addForm > form {
        display: flex;
        flex-direction: row;
    }

    #addForm > form > .column-input { 
        width:467px;
        height:55px;
        display:flex;
    }

    #addForm > form > .column-input > input { 
        width:100%;
        border:0;
        outline-style: none;
        justify-content: center;
        background-color:#D5DBE3;
        border-top-left-radius: 10px;
        border-end-start-radius: 10px;
        font-family: Rubik-Regular;
        font-size: 16px;
        padding-left:15px;

    }
    
    #addForm > form > .column-button { 
        width:101px;
        display:flex;
    }

    #addForm > form > .column-button > button{ 
        width:100%;
        justify-content: center;
        border:0;
        background-color:#43B883;
        border-top-right-radius: 10px;
        border-end-end-radius: 10px;
        color:white;
        font-family: Rubik-Bold;
        font-size:16px;
    }

</style>