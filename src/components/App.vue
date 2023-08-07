<template>
    <div id="app">
        <div class="nav-bar"></div>
        <div class="cart">Cart({{ cart }})</div>
        <div class="product-display">
            <div class="product-container">
                <div class="product-image">
<img alt="balloon-image" v-bind:src="image">
                </div>
                <div class="product-info">
                    <h1>{{ product }}</h1>
                    <p v-if="inventory > 10">In Stock</p>
                    <p v-else-if="inventory <= 10 && inventory > 0">Almost Sold Out!</p>
                    <p v-else>Out of Stock</p>
                    <ul>
                        <li v-for="detail in details">{{ detail }}</li>
                    </ul>
                    <div :key="variant.id" v-for="variant in variants">{{ variant.color }}</div>
                    <button v-on:click="addToCart" class="button">Add to Cart</button>
                </div>
            </div>
        </div>
   
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        cart: 0,
        product: "Balloon ",
        image: "src/assets/images/Pink.svg",
        inventory: 100,
        details:["Inflatable", "Colorful", "Festive"],
        variants:[
            {id: 2234, color: 'pink'},
            {id: 2235, color: 'blue'}
        ]

      };
    },
    methods:{
      addToCart(){
        this.cart +=1
      }
    }
  };
  </script>
  
  <style>
body {
  background-color: #f2f2f2;
  margin: 0px;
  font-family: tahoma;
  color: #282828;
}

img {
  border: 2px solid #d8d8d8;
  width: 40%;
  margin: 40px;
  padding: 15px;
  -webkit-box-shadow: 0px 2px 15px -12px rgba(0, 0, 0, 0.57);
  -moz-box-shadow: 0px 2px 15px -12px rgba(0, 0, 0, 0.57);
  box-shadow: 2px 15px -12px rgba(0, 0, 0, 0.57);
}

.nav-bar {
  background: linear-gradient(-90deg, #84cf6a, #16c0b0);
  height: 60px;
  margin-bottom: 25px;
  -webkit-box-shadow: 0px 2px 15px -12px rgba(0, 0, 0, 0.57);
  -moz-box-shadow: 0px 2px 15px -12px rgba(0, 0, 0, 0.57);
  box-shadow: 1px 1px 5px rgba(0, 0, 0, 0.57);
}

.product-display {
  display: flex;
  flex-direction: column;
  padding: 1rem;
}

.product-container {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
}

.product-image,
.product-info {
  width: 50%;
}
  </style>
  