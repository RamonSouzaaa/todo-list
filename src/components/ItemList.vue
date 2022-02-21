<template>
    <div id="itemList">
        <div class="item" v-for="item in lista" :key="item.id">
            <span :class="{itemFinish: item.isFinalizado}">{{item.nome}}</span>
            <button v-if="!item.isFinalizado" @click.prevent="check(item.id)">
                <i class="fas fa-check"></i>
            </button>
            <button v-else @click.prevent="del(item.id)">
                <i class="fas fa-trash"></i>
            </button>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'itemList',
        props: {
            lista: {
                type: Array,
                required:true
            }
        },
        methods: {
            check(id){
                if(confirm('Deseja realmente concluir esse item?')){
                    this.$emit('checkItem', id)
                }
            },

            del(id){
                if(confirm('Deseja realmente excluir esse item?')){
                    this.$emit('delItem', id)
                }
            },
        }
    }
</script>

<style scoped>

    @font-face {
        font-family: 'Rubik-Regular';
        src: url('../fonts/Rubik/Rubik-Regular.ttf');
    }
    #itemList {
        display:flex;
        flex-direction: column;
        align-items: center;
    }

    #itemList > .item {
        width: 568px;
        height:55px;
        background-color: #2D333E;
        color:white;
        margin-top:11px;
        font-family: Rubik-Regular;
        display:flex;
        flex-direction: row;
        justify-content: space-between;
        border-radius:10px;
    }

    #itemList > .item:first-child {
        margin-top:50px;
    }

    #itemList > .item > span{
        align-self: center;
        margin-left:20px;
    }

    #itemList > .item > button{
        border:0;
        outline-style: none;
        background-color:transparent;
        font-size: 20px;
        color:white;
        margin-right:20px;
    }

    .itemFinish {
        color:#646464;
        text-decoration: line-through;
    }

</style>