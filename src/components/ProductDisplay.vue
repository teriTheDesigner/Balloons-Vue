<template>
    <div class="product-display">
    <div class="product-container">
        <div class="product-image">
<img alt="balloon-image" v-bind:src="image">
        </div>
        <div class="product-info">
            <h1>{{ title }}</h1>
            <p v-if="InStock > 10">In Stock</p>
            <p v-else-if="InStock <= 10 && InStock > 0">Almost Sold Out!</p>
            <p v-else>Out of Stock</p>
            <p>Shipping: {{ shipping }}</p>
            <ul>
                <li v-for="detail in details">{{ detail }}</li>
            </ul>
            <div  v-for="(variant, index) in variants" :key="variant.id" class="color-circle"  @mouseover="updateVariant(index)" :style="{backgroundColor: variant.color}"></div>
            <button  v-on:click="addToCart" class="button" :class="{disabledButton: !InStock}" :disabled="!InStock">Add to Cart</button>
        </div>
    </div>
</div>
</template>

<script>
export default {
    props:{
premium:{
    type: Boolean,
    required: true
}
    },
    data() {
    return {
      brand: "BreezBalloons",
      product: "Balloon ",
      selectedVariant: 0,

      details: ["Inflatable", "Colorful", "Festive"],
      variants: [
        {
          id: 2234,
          color: "pink",
          image: "src/assets/images/Pink.svg",
          quantity: 50,
        },
        {
          id: 2235,
          color: "blue",
          image: "src/assets/images/Blue.svg",
          quantity: 0,
        },
        {
          id: 2236,
          color: "orange",
          image: "src/assets/images/Orange.svg",
          quantity: 2,
        },
        {
          id: 2237,
          color: "yellow",
          image: "src/assets/images/Yellow.svg",
          quantity: 35,
        },
        {
          id: 2238,
          color: "green",
          image: "src/assets/images/Green.svg",
          quantity: 7,
        },
      ],
    };
  },

  methods: {
    addToCart() {
      this.cart += 1;
    },
    updateVariant(index) {
      this.selectedVariant = index;
      console.log(index);
    },
  },
  computed: {
    title() {
      return this.brand + " " + this.product;
    },
    image() {
      return this.variants[this.selectedVariant].image;
    },
    InStock() {
      return this.variants[this.selectedVariant].quantity;
    },
    shipping(){
        if (this.premium){
            return 'Free'
        }
        return 29.99
    }
  },
}
</script>
<style>
img {
  border: 2px solid #d8d8d8;
  width: 40%;
  margin: 40px;
  padding: 15px;
  -webkit-box-shadow: 0px 2px 15px -12px rgba(0, 0, 0, 0.57);
  -moz-box-shadow: 0px 2px 15px -12px rgba(0, 0, 0, 0.57);
  box-shadow: 2px 15px -12px rgba(0, 0, 0, 0.57);
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

.color-circle {
  width: 50px;
  height: 50px;
  margin-top: 8px;

  border-radius: 50%;
}
.button {
  margin: 30px;
  background-color: #39495c;
  border-radius: 5px;
  font-size: 18px;
  width: 160px;
  height: 60px;
  color: white;
  padding: 20px;
  box-shadow: inset 0 -0.6em 1em -0.35em rgba(0, 0, 0, 0.17),
    inset 0 0.6em 2em -0.3em rgba(255, 255, 255, 0.15),
    inset 0 0 0em 0.05em rgba(255, 255, 255, 0.12);
  text-align: center;
  cursor: pointer;
}
.disabledButton {
  background-color: #d8d8d8;
  cursor: not-allowed;
}
</style>