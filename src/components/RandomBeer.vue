<template>
  <div>
    <div class="random-box">
      <div class="random-button">
        <b-button @click="randomBeer" pill variant="outline-danger"
          >Get Random!</b-button
        >
      </div>
      <div class="m-4">
        <h1 class="label mt-5">{{ name }}</h1>

        <b-container fluid class="bv-example-row">
          <v-divider></v-divider>
          <b-row>
            <b-col>
              <div class="description-box m-5">
                <h3 class="d-flex justify-content-center mb-2">Description</h3>
                <h6>{{ description }}</h6>
              </div></b-col
            >
            <v-divider vertical></v-divider>
            <b-col>
              <div class="beer-box">
                <img class="beer-img" :src="img_url" /></div
            ></b-col>
          </b-row>
        </b-container>

        <h3 class="d-flex justify-content-center mb-2">Pairing Food</h3>
        <b-container fluid class="bv-example-row">
          <v-divider></v-divider>
          <b-row>
            <b-col>
              <b-container class="food mt-3">
                <b-row>
                  <b-col v-for="item in food" :key="item">
                    <div class="mx-3">
                      <img
                        alt="Vue logo"
                        class="fork-icon"
                        src="../assets/fork.png"
                      />
                      {{ item }}
                    </div>
                  </b-col>
                </b-row>
              </b-container>
            </b-col>
          </b-row>
        </b-container>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
const API = "https://api.punkapi.com/v2/beers";

export default {
  data() {
    return {
      name: "",
      description: "",
      img_url: "",
      food: [],
    };
  },
  methods: {
    randomBeer() {
      axios.get(`${API}/random`).then((response) => {
        console.log(response.data[0].food_pairing);
        this.name = response.data[0].name;
        this.description = response.data[0].description;
        this.img_url = response.data[0].image_url;
        this.food = response.data[0].food_pairing;
      });
    },
  },
  beforeMount() {
    this.randomBeer();
  },
};
</script>
<style scoped lang="scss">
.random-box {
  width: 100%;
  justify-content: center;
  flex-direction: column;
}
.random-button {
  display: flex;
  justify-content: center;
}
.label {
  display: flex;
  justify-content: center;
}
.description-box {
  padding: 20px;

  height: 100px;
}
.beer-img {
  width: 150px;
  height: 450px;
}
.beer-box {
  display: flex;
  justify-content: center;
}
.spacing {
  border-width: 1px 0 1px 0;
  border-color: rgb(231, 229, 229) #fff rgb(231, 229, 229) #fff;
}
.food-list {
  width: 100%;
}
.fork-icon {
  width: 30px;
  height: 30px;
}
</style>
