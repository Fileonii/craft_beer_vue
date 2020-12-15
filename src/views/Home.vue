<template>
  <div class="home">
    <RandomBeer />
  </div>
</template>

<script>
// @ is an alias to /src

import RandomBeer from "@/components/RandomBeer.vue";

export default {
  name: "Home",
  components: {
    RandomBeer,
  },
};
</script>

<style lang="scss">
.logo {
  width: 300px;
  height: 300px;
}
</style>
