<template>
    <Content></Content>
</template>

<script>

import Content from "@/Content";

export default {
  name: 'App',

  components: {
    Content,
  },

  data: () => ({
  }),
};
</script>

<style>
* {
  margin: 0 !important;
  padding: 0 !important;
}
body {
  background: url(https://i.pinimg.com/originals/d7/d8/db/d7d8dbf3811c797e5d2cc364743ae3a7.gif) center center fixed;
  -webkit-background-size: cover;
  -moz-background-size: cover;
  -o-background-size: cover;
  background-size: cover;
}
</style>
