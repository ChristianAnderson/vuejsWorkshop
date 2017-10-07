<template>
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
</template>

<script>
export default {
  data (){
      return{
          newTodo:''
      }
  },
  methods:{
      addTodo(){
          this.$emit('addTodo')
      }
  }
}
</script>
