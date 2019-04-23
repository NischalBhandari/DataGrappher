<template>
  <div id="app">
    <Header />
<!--     catch the add-todo event from AddTodo component 
 -->    
<!-- 
    <AddTodo v-on:add-todo="addTodo" />

    <router-view/>  -->

    <searching v-on:foundthis="addfounddata" />
    <!-- catch the  event del-todo method from Todos component  
    -->
<!--     <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
 -->    <graphworld v-bind:graphdata="graphdata" />
  <p>
    <Calculator />
  </p>
  <picker />

    <Footer />

  </div>
</template>

<script>
  /*import all the components */
  import Header from './components/layout/Header';
import Todos from './components/Todos';
import AddTodo from './components/AddTodo';
import axios from 'axios';
import graphworld from './components/graphs';
import Footer from './components/layout/Footer';
import Calculator from './components/Calculator';
import picker from './components/picker';
import searching from './components/search';

export default {
  name: 'App',
  components: {
    /*it defines all the components present */
    Header,
    Todos,
    AddTodo,
    graphworld,
    Footer,
    Calculator,
    picker,
    searching,
  },
  data(){
    /*define data as a function in a component */

    return {

      todos:
      [],
      graphdata:[]
    }
  },
  methods: {

    deleteTodo(id){
      /*filter the id got from the todos component */
      /*here logic is meant to keep all the todos except which matches the id */
      this.todos = this.todos.filter(todo => todo.id !== id );
    },
    addTodo(newTodo){
    /*  copy with the ...  spread operator from todos(copies newTodo to this.todos )*/
      this.todos = [...this.todos, newTodo];
    },
    find_rising(graphdata){

      console.log(graphdata)
    },
    addfounddata(values){

     this.graphdata = JSON.parse(JSON.stringify(values));
  },
/*    created(){
      axios.get('http://localhost:5000/jsonshow')
      .then(response => (this.ghardata = response))
      .then(res=> this.graphdata = res.data)
      .catch(err => console.log(err));
*//*      axios.get('https://jsonplaceholder.typicode.com/todos')
     .then(res => this.todos = res.data)
      .catch(err=>console.log(err));*/

    
  //}
}
}

</script>

<style>
  *{
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }
  body {
    font-family: Arial, Helvetica, sans-serif;
    line-height: 1.4;
  }
  .btn{
    display: inline-block;
    border: none;
    background: #555;
    color: #fff;
    padding: 7px 20px;
    cursor: pointer;
  }
  .btn:hover{
    background: #666;
  }
</style>
