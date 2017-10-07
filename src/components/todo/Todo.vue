<template>
    <li 
        class="list-group-item">
        <button>
            x
        </button>
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
          required: true,
          validator: (value) => value.length
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

