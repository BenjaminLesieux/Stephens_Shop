<template>
  <div id="header">
    <img id="logo" src="https://upload.wikimedia.org/wikipedia/commons/thumb/3/35/Znak_graficzny_AGH.svg/1024px-Znak_graficzny_AGH.svg.png" alt="cart logo">
    <img id="sas" src="../assets/logo_ss.png" alt="logo">

    <div id="sidebar">
      <p>
        {{totalPurchased}} 🛍️
      </p>
      <p>
        {{totalPrices}} 💶
      </p>
    </div>
  </div>
</template>

<script>

export default {
  name: "Header",
  data() {
    return {
      showPopup: Boolean
    }
  },
  methods: {
    togglePopup() {
      this.showPopup = !this.showPopup
      console.log("updated popup..." + this.showPopup)
    }
  },
  props: {
    totalPrices: Number,
    totalPurchased: Number
  }
}
</script>

<style scoped>

@import url('https://fonts.googleapis.com/css2?family=Poppins:ital,wght@0,100;0,900;1,900&display=swap');

* {
  font-family: "Poppins", serif;
}

#header {
  height: 80px;
  width: 100%;

  display: flex;
  justify-content: space-between;

  background-color: #904E55;
}

#logo {
  height: 50px;

  align-self: center;
  margin-left: 10px !important;
}

#sas {
  height: 150px;
  align-self: center;
  margin-left: 20px !important;
}

#basket {
  align-self: center;
}

#popup {
  position: absolute;
  background-color: whitesmoke;
}

#sidebar {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;

  width: 95px;

  border-radius: 2px;
}

#btn-sidebar {
  width: 60px;
  font-size: 45px;
  border-radius: 2px;
  background-color: #904E55;
}

#sidebar p {
  padding-left: 1px !important;
  font-size: 14.6px;
  font-weight: normal;
  color: white;
}

#btn-sidebar:hover{
  font-size: 46px;
}
</style>