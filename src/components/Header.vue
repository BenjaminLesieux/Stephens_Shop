<template>
  <div id="header">
    <img id="logo" src="https://lh3.googleusercontent.com/proxy/kbU_bEBNup2LcdUBjiRnafhnECZsyTxOB1KN6nj6UmkRWo2OJdlwiLklv_eNmSQ4ImQAAYIrKyEqGL6E5y30Px-NEvdiN4i9XPDYK-u7hE736PZqlj2bQDlOqWTrvdxh" alt="cart logo">
    <img id="sas" src="../assets/logo_ss.png" alt="logo">

    <button id="btn-sidebar" v-on:click="togglePopup">
      🛍️
    </button>
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
  }
}
</script>

<style scoped>
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
}

#basket {
  align-self: center;
}

#popup {
  position: absolute;
  background-color: whitesmoke;
}

#btn-sidebar {
  width: 60px;
  font-size: 45px;
  border-radius: 2px;
  background-color: #904E55;
  border-left: 1px dashed black;
}

#btn-sidebar:hover{
  font-size: 50px;
}
</style>