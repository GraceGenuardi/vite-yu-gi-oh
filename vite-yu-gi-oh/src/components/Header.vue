<template>
    <header class="main-header">
      <div class="container">
        <span class="logo"><img src="../assets/logo.jpg" alt="Logo"></span>
        <h1>{{ title }}</h1>
      </div>
  
    </header>
  </template>
  
  <script>
    export default {
      data() {
        return {
          title: 'Yu-Ghi-Oh API'
        }
      }
      
    }
  </script>
  
  <style lang="scss" scoped>
  @use '../style/partials/variables' as *;
  .main-header {
    text-align: left;
    font-size: 10px;
    background-color: $bg-color;
    padding: 5px;
    font-size: 15px;
    color: black;
    
  }
  .logo {
    width: 100px;
    padding-right: 10px;
  }
  </style>