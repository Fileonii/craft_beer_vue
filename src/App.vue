<template>
  <div class="app">
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </div>
    <div class="d-flex justify-content-center my-3">
      <img alt="Vue logo" class="logo" src="./assets/logo.png" />
    </div>
    <router-view />
  </div>
</template>

<script>
export default {
  data() {
    return {
      drawer: true,
    };
  },
};
</script>
<style lang="scss"></style>
