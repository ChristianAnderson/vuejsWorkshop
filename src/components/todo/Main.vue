<template>
  <div class="container">
    <h1>TO DO </h1>

    <form v-on:submit.prevent="addTodo">
      <div class="input-group">
        <input 
          v-model="newTodo"
          type="text" 
          class="form-control" 
          placeholder="Add todo..">
        <span class="input-group-btn" id="basic-addo">
           <button class="btn btn-success"> Add + </button>
        </span>
      </div>
    </form>
    <br>
    <div>
      <h3>
        Pending Todos 
      </h3>
      <ul class="list-group">
        <li 
          v-for="(todo, index) in pendingTodos"
          :key="index"
          class="list-group-item">
          {{ todo.description}} ->
          {{ todo.done ? 'yep :D ' : 'nou :v '  }}
          <button 
            v-on:click="toggle(todo)"
            class="btn btn-sm btn-primary float-right" >  
            toggle!
          </button>
          </li>
      </ul>
    </div>
    <br>
    <h3>
        Completed Todos 
    </h3
    <ul class="list-group">
      <li 
        v-for="(todo, index) in completedTodos"
        :key="index"
        class="list-group-item">
        {{ todo.description}} ->
        {{ todo.done ? 'yep :D ' : 'nou :v '  }}
        <button 
          v-on:click="toggle(todo)"
          class="btn btn-sm btn-primary float-right" >  
          toggle!
        </button>
        </li>
    </ul>
  </div>
</template>

<script>
  export default {
    methods:{
      toggle (todo){
        todo.done = !todo.done
      }, 
      addTodo(){
        if(!this.newTodo){
          return
        }
        this.todos.push({
          description: this.newTodo,
          done: false  
        });
        this.newTodo = ""
      }   
    },

    computed: {
      pendingTodos (){
        return this.todos.filter((todo) => !todo.done)
      },
      completedTodos (){
        return this.todos.filter((todo) => todo.done)
      },
    },

    data () {
      return {
        newTodo: "",
        todos: [
          { description: 'Drink a beer', done: true},
          { description: 'Learn Vue JS', done: false},
          { description: 'Deliver the workshop', done: true}
        ]
      }
    }
  }
</script>