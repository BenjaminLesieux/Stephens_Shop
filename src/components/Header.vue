<template>
  <div id="header">
    <img id="logo" src="../assets/cart_logo.png" alt="cart logo">
    <img id="sas" src="../assets/logo_ss.png" alt="logo">
    <div></div>
  </div>
</template>

<script>
export default {
  name: "Header"
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
  width: 50px;

  align-self: center;
}

#sas {
  height: 150px;
  align-self: center;
}
</style>