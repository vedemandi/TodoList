<template>
  <div id="app">
    <Header />
    <addToDo v-on:add-todo="addTodo" />
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
    
  </div>
</template>

<script>
import Header from './components/layout/Header';
import Todos from './components/Todos';
import addToDo from './components/addToDo';

export default {
  name: 'app',
  components: {
    Todos,
    Header,
    addToDo
  },
  data(){
    return{
      todos:[
        {
          id:1,
          title:"task one",
          completed:false

        },
        {
          id:2,
          title:'task two',
          completed: true
        },
        {
          id:3,
          title:'task three',
          completed:false
        }
      ]
    }
    },
    methods: {
      deleteTodo(id){
        this.todos = this.todos.filter(todo=> todo.id !==id);
      },
      addTodo(newTodo){
        this.todos =[...this.todos, newTodo];

      }
    }
  }

</script>

<style>
*{
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body{
  font-family:'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
  line-height: 1.4;
}
.btn{
  display: inline-block;
  border:none;
  background: #555;
  color:#fff;
  padding: 7px 20px;
  cursor:pointer;

}
.btn-hover{
  background: #ff3344;;
}
</style>
