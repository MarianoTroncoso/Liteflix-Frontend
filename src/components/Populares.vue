<template>
  <div class="populares-wrapper">
    <div class="populares-wrapper-mobile">
      <h1 class="animate__animated animate__fadeInLeftBig">
        Populares de Liteflix
      </h1>
      <div
        class="populares-imagenes-mobile animate__animated animate__fadeInRightBig"
      >
        <img
          v-for="(image, index) in images"
          :key="index"
          :src="'https://image.tmdb.org/t/p/w1280' + image.poster_path"
          alt=""
        />
      </div>
    </div>
    <div class="populares-wrapper-desktop">
      <h4 class="animate__animated animate__fadeInLeftBig animate__delay-1s">
        Populares de Liteflix
      </h4>
      <div
        class="populares-imagenes-desktop animate__animated animate__fadeInRightBig animate__delay-2s"
      >
        <ImagenPopulares
          v-for="(image, index) in images"
          :key="index"
          :title="image.title"
          :image="'https://image.tmdb.org/t/p/w1280' + image.poster_path"
        />
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import ImagenPopulares from "./ImagenPopulares";

export default {
  name: "Populares",
  mounted() {
    axios
      .get(
        "https://api.themoviedb.org/3/movie/popular?api_key=6f26fd536dd6192ec8a57e94141f8b20"
      )
      .then((response) => {
        this.images = response.data.results.slice(0, 4);
      });
  },
  data() {
    return {
      images: [],
    };
  },
  components: {
    ImagenPopulares,
  },
};
</script>

<style lang="scss" scoped>
.populares-wrapper {
  color: white;
}
.populares-wrapper-mobile {
  padding: 0 0 0 15px;
}
.populares-wrapper-mobile h1 {
  font-family: "Raleway";
  font-size: 20px;
  font-weight: 800;
  font-stretch: normal;
  font-style: normal;
  line-height: normal;
  letter-spacing: normal;
  text-transform: uppercase;
}
.populares-imagenes-mobile {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  grid-gap: 3px;
}
.populares-imagenes-mobile img {
  width: 100%;
  height: auto;
}
.populares-wrapper-desktop {
  display: none;
  padding: 40px 0 0 0;
  width: 80%;
  margin: 0 auto 0 auto;
}
.populares-wrapper-desktop h4 {
  font-family: "Montserrat";
  font-size: 20px;
  font-weight: bold;
  text-transform: uppercase;
  margin: 0;
}
.populares-imagenes-desktop {
  display: inline-flex;
  padding-top: 9.3px;
  position: relative;
  width: 100%;
  overflow: hidden;
}

@media screen and (min-width: 760px) {
  .populares-wrapper-desktop {
    display: block;
  }
  .populares-wrapper-mobile {
    display: none;
  }
}
</style>