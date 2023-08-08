<template>
    <div id="app">
        <div class="nav-bar"></div>
        <div class="cart">Cart({{ cart.length }})</div>
        
<ProductDisplay :premium="premium" @add-to-cart="updateCart"></ProductDisplay>
<ReviewList v-if="reviews.length" :reviews="reviews"></ReviewList>
<ReviewForm @review-submitted="addReview"></ReviewForm>
    </div>
  </template>
  
  <script >

import ProductDisplay from "./ProductDisplay.vue";
import ReviewForm from "./ReviewForm.vue"
import ReviewList from "./ReviewList.vue"
  export default {
    data() {
      return {
        cart: [],
        premium: false,
        reviews:[]

      };
    },
    components: {
    ProductDisplay, 
    ReviewList,
    ReviewForm
  },
    methods:{
     updateCart(id){
      this.cart.push(id)
     },
     addReview(review){
      this.reviews.push(review)
     }
    },
    
    
  };


  </script>
  
  <style>


  </style>
  