<template>
    <div id="app">
        <div class="nav-bar"></div>
        <div class="cart">Cart({{ cart }})</div>
        
<ProductDisplay :premium="premium"></ProductDisplay>

    </div>
  </template>
  
  <script >

import ProductDisplay from "./ProductDisplay.vue";
  export default {
    data() {
      return {
        cart: 0,
        premium: false

      };
    },
    components: {
    ProductDisplay, 
  },
    methods:{
     
    },
    
    
  };


  </script>
  
  <style>


  </style>
  