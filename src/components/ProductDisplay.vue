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