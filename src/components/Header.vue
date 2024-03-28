<template>
    <header class="header">
      <img alt="Vue logo" class="logo" src="./assets/tatto.jpg" width="125" height="125" />
      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
        
      </nav>
    </header>
  </template>
  
  <script>
  export default {
    name: 'Header',
  };
  </script>
  
  <style scoped>
  
  .header {
    background-color: #f0f0f0; 
  }
  </style>
  