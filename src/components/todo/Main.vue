<template>
  <div class="container">
    <h1>TO DO </h1>

    <addTodo @onAddTodo="addTodo()"/>

    
    <br>

    <div>
      <h3>
        Pending Todos 
      </h3>
      <ul class="list-group">
        <todo 
          v-for="(todo, index) in pendingTodos"
          :key="index"
          :description="todo.description"
          :done="todo.done"
          @onToggle="pendingToggle(todo)" />
      </ul>
    </div>
    <br>
    <h3>
        Completed Todos 
    </h3
    <ul class="list-group">
      <todo 
        v-for="(todo, index) in completedTodos"
        :key="index"
        :description="todo.description"
        :done="todo.done"
        @onToggle="completedToggle(todo)"/> 
    </ul>

    <br>
    <h3>
        All Todos 
    </h3
    <ul class="list-group">
      <todo 
        v-for="(todo, index) in todos"
        :key="index"
        :description="todo.description"
        :done="todo.done"
        @onToggle="completedToggle(todo)"/> 
    </ul>
  </div>
</template>

<script>
  import addTodo from "./addTodo"
  import Todo from "./Todo"
  export default {
    components:{
      Todo,
      addTodo 
    },
    methods:{
      pendingToggle (todo){
        todo.done = !todo.done
      }, 
      completedToggle (todo){
        todo.done = !todo.done
      }, 
      addTodo(){
        console.log(this.newTodo);
        if(!this.newTodo){
          return
        }
        this.todos.push({
          description: this.newTodo,
          done: false  
        });
        this.newTodo = ""
      },
      remove (todo) {
        this.todos.splice(this.todos.indexOf(todo), 1)
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