<template>
  <div id="card" :class="number-counter > 10 ? activeClass : errorClass">
    <img id="obj-img" :src=imgSrc :alt=imgAlt>
    <div id="container">
      <div id="basket">
        <Basket :number=number :counter=counter></Basket>
      </div>
      <h4><b>{{ productName }} - <span style="color:navajowhite">{{productPrice}} €</span></b></h4>
      <p id="desc">{{ productDescription }}</p>
      <p v-if="counter>=0 && numCounter > 3">
        Qty: {{numCounter}}/{{number}}
      </p>
      <p v-if="(numCounter) <= 3" style="color:red">Qty: {{numCounter}}/{{number}}</p>
      <p id="un-available" v-if="counter===number" style="color: red">{{productName}} is no more available</p>
      <div id="btn-container">
        <button class="btn red" v-if="counter>0" v-on:click="downCounter()">-</button>
        <button class="btn green" v-if="counter<number" v-on:click="upCounter()">+</button>
      </div>
      <div id="price-indicator" v-if="cheap">
        <p>CHEAPEST</p>
      </div>
      <div id="expensive-indicator" v-if="expensive">
        <p>EXPENSIVE</p>
      </div>

    </div>
  </div>
</template>

<script>

import Basket from "../components/Basket"

export default {
  name: "Product",
  props: {
    productName: String,
    productPrice: Number,
    number: Number,
    productDescription: String,
    imgSrc: String,
    imgAlt: String,
    cheap: Boolean,
    expensive: Boolean,
  },
  components: {
    Basket
  },
  data(){
    return {
      counter: 0,
      numCounter: this.number,
      activeClass: "green-card",
      errorClass: "red-card",
    }
  },
  methods: {
    upCounter() {
      this.counter++
      this.numCounter--
      this.$emit('update-qty', 1, this.productPrice)
    },
    downCounter() {
      this.counter--
      this.numCounter++
      this.$emit('update-qty', -1, -this.productPrice)
    }
  }
}

</script>

<style scoped>

@import url('https://fonts.googleapis.com/css2?family=Poppins:ital,wght@0,100;0,900;1,900&display=swap');

* {
  color: white;
  font-family: "Poppins", serif;
}

#un-available {
  font-style: italic;
  font-weight: lighter;
  font-size: 8px;
}

#desc {
  font-style: italic;
  font-weight: lighter;
  font-size: 10px;
}


#btn-container {
  display: flex;
  flex-direction: row;
  justify-content: space-evenly;
  width: 300px;
}

.btn {
  height: 50px;
  width: 50px;
  align-self: center;
  border-radius: 50%;
}

.red {
  background-color: #904E55;
}

.green {
  background-color: #4E9089;
}

#basket {
  position: absolute;

  right: 0;
  top: -88%;
}

#card {
  /* Add shadows to create the "card" effect */
  border-radius: 5px;
  box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
  transition: 0.3s;
  backdrop-filter: blur(9px);
  margin-top: 10px !important;
  display: flex;
  justify-content: space-evenly;
  flex-direction: column;
  align-items: center;
  width: 300px;
  height: 300px;
}

.green-card {
  border: 2px solid #4E9089;
}

.red-card {
  border: 2px solid #904E55;
}

/* On mouse-over, add a deeper shadow */
#card:hover {
  box-shadow: 0 8px 16px 0 rgba(0,0,0,0.4);
}

#obj-img {
  height: 90px;
  width: 90px;
}

/* Add some padding inside the card container */
#container {
  position: relative;
  padding: 2px 16px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  text-align: center;
  height: 50%;
}

#price-indicator {
  position: absolute;
  border-radius: 2px;
  top:-90%;
  height: 120px;
  width: 30px;

  display: flex;
  align-items: center;
  justify-content: flex-start;
  margin-top: 10px !important;
}

#expensive-indicator {
  position: absolute;
  border-radius: 2px;
  top:-90%;
  height: 120px;
  width: 30px;

  display: flex;
  align-items: center;
  justify-content: flex-start;
  margin-top: 10px !important;
}


#price-indicator p {
  writing-mode: vertical-rl;
  text-orientation: upright !important;
  font-size: 9px;
  font-weight: bolder;
  color: greenyellow;
}

#expensive-indicator p {
  writing-mode: vertical-rl;
  text-orientation: upright !important;
  font-size: 9px;
  font-weight: bolder;
  color: red;
}
</style>