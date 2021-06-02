<template>
  <div class="mis-peliculas-wrapper">
    <div class="mis-peliculas-wrapper-desktop">
      <h1>Mis películas</h1>
      <div class="mis-peliculas-imagenes-desktop">
        <img
          v-for="(movie, index) in movies"
          :key="index"
          :src="'http://localhost:5000/image/' + movie.image"
          alt=""
        />
      </div>
    </div>
    <div class="mis-peliculas-wrapper-mobile">
      <h1>Mis películas</h1>
      <div class="mis-peliculas-imagenes-mobile">
        <img
          v-for="(movie, index) in movies"
          :key="index"
          :src="'http://localhost:5000/image/' + movie.image"
          alt=""
        />
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      movies: [],
    };
  },
  mounted() {
    axios.get("http://localhost:5000/movies").then((response) => {
      // this.images = response.data.results.slice(0, 4);

      // console.log(response.data);
      this.movies = response.data;

      this.movies.forEach((m) => console.log(m));
    });
  },
};
</script>

<style lang="scss" scoped>
.mis-peliculas-wrapper-desktop {
  // border: 2px solid white;
  display: none;
  // color: white;
  padding: 0 20px 0 164px;
  h1 {
    font-family: "Montserrat";
    font-size: 20px;
    font-weight: bold;
    margin: 0;
  }
}
.mis-peliculas-imagenes-desktop {
  // border: 2px solid red;
  padding: 20.3px 0 100px 0;

  display: flex;
  img {
    width: 255px;
    height: 155px;
    // margin: 20.3px 31px 0 0;
    object-fit: contain;
    margin: 0 31px 0 0;
  }
}
.mis-peliculas-wrapper-mobile {
  border: 2px solid white;
  color: white;
  padding: 0 14px 0 14px;

  h1 {
    font-family: "Raleway";
    font-size: 20px;
    font-weight: 800;
  }

  .mis-peliculas-imagenes-mobile {
    img {
      width: 100%;
      height: auto;
      // height: 201px;
      object-fit: contain;
      margin-bottom: 10px;
    }
  }
}
@media screen and (min-width: 760px) {
  .mis-peliculas-wrapper-desktop {
    display: block;
  }
  .mis-peliculas-wrapper-mobile {
    display: none;
  }
}
</style>