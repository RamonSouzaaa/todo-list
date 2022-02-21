<template>
  <div id="main">
    <div class="title">
      <h1>Todo List</h1>
    </div>
    <div class="container">
      <div class="list">
        <ItemList class="item" :lista="lista" @checkItem="check($event)" @delItem="del($event)"/>      
      </div>
      <AddForm class="form" @addItem="add($event)"/>
    </div>  
  </div>
</template>

<script>
  import AddForm from './components/AddForm'
  import ItemList from './components/ItemList'

  export default {
    name: 'Main',
    data(){
      return {
        lista: []
      }
    },
    methods: {

      add(item){
        this.lista.push({
          id: this.getLastId()+1,
          nome: item,
          isFinalizado: false
        })
      },

      check(id){
        this.lista.filter((item) => {
          if(item.id === id){
            item.isFinalizado = true
          }
        })
      },

      del(id){
        this.lista = this.lista.filter((item) => {
          return item.id !== id
        })
      },

      getLastId(){
        let id = 0;
        if(this.lista.length > 0){
          this.lista.filter((item) => {
            if(item.id > id){
              id = item.id
            }
          })
        }

        return id
      }
    },
    components: {
      AddForm,
      ItemList
    }
  }
</script>

<style scoped>
   @font-face {
     font-family: 'Rubik-SemiBold';
     src: url('fonts/Rubik/Rubik-SemiBold.ttf');
   }

   #main {
     display:flex;
     flex-direction: column;
     align-items: center;
     justify-content: center;
     height:98vh;
   }

   #main > .title {
     background-color: #43B883;
     width: 650px;
     height:64px;
     border-top-right-radius: 20px;
     border-top-left-radius: 20px;
   }

   #main > .title > h1 {
     color:#FFFFFF;
     font-family: Rubik-SemiBold;
     text-align: center;
     font-size:36px;
     margin-top:10px;
   }

   #main > .container {
     background-color: #374151;
     width: 650px;
     height:600px;
     border-end-start-radius: 20px;
     border-end-end-radius: 20px;
     display:flex;
     flex-direction: column;
     align-items: center;
   }

   #main > .container > .form {
    padding-bottom: 30px;
   }

   #main > .container > .list{
      width: 100%;
      height:100%;
   }
</style>
