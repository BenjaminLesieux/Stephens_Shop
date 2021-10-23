<template>
  <div id="container" :class="number-counter > 10 ? activeClass : errorClass">
    <img id="basket" src="https://png-3.vector.me/files/images/2/9/293452/shopping_basket_preview" alt="basket">
    <p>{{counter}}</p>
  </div>
</template>

<script>
export default {
  name: "Basket",
  props: {
    counter: Number,
    number: Number
  },
  data () {
    return {
      activeClass: "green",
      errorClass: "red"
    }
  }
}
</script>

<style scoped>

  * {
    color: white;
  }

  #basket {
    height: 35px;
  }

  #container {
    height: 40px;
    width: 60px;

    display: flex;
    justify-content: start;
    align-items: center;

    border-radius: 2px;
    background-image: linear-gradient(top, #4E9089, #904E55);;
  }

  .green {
    border: 1px solid #4E9089 !important;
  }

  .red {
    border: 1px solid #904E55 !important;
  }
</style>