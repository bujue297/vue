<template>
    <div class="custom-checkbox">
      <input 
        type="checkbox" 
        :id="id" 
        :checked="isDone" 
        class="checkbox" 
        @change="toggleDone" 
      />
      <label 
        :for="id" 
        class="checkbox-label"
        :class="{'checkbox-label--done': isDone}"
      >
        {{ label }}
      </label>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      id: String,
      label: String,
      isDone: Boolean,
    },
    methods: {
      toggleDone() {
        this.$emit('toggle', this.id);
      }
    }
  }
  </script>
  
  <style scoped>
  .checkbox-label--done {
    text-decoration: line-through;
    color: #d3d3d3;
  }
  </style>
  