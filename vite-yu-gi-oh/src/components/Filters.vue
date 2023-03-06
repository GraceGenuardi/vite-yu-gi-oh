<template>
    <div class="filters">
      <input v-model="filterName" @input="emitFilterEvent" placeholder="FILTER BY NAME"/> 
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        filterName: ""
      };
    },
    methods: {
      emitFilterEvent() {
        this.$emit("filter", this.filterName);
      }
    }
  };
  </script>
  
  <style scoped>
  .filters {
    display: flex;
    width: 500px;
    
  }
  
  .filters input {
    padding: 5px;
    border-radius: 5px;
    border: 1px solid #ccc;
    
    
  }
  </style>