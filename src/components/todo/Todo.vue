<template>
    <li 
        class="list-group-item">
        {{ description}} ->
        {{ done ? 'yep :D ' : 'nou :v '  }}
        <button 
        v-on:click="toggle()"
        class="btn btn-sm btn-primary float-right" >  
        toggle!
        </button>
    </li>
</template>
<script>
export default {
  props: {
      description:{
          type: String,
          required: true
      },
      done:{
          type: Boolean,
          default: false
      }
  },
  methods:{
      toggle (){
          this.$emit('onToggle')
      }
  }
}
</script>

