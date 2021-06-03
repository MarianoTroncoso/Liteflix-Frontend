<template>
  <div class="proximamente-wrapper">
    <div class="proximamente-wrapper-mobile">
      <h1 class="animate__animated animate__fadeInLeftBig">Proxímamente</h1>
      <div
        class="proximamente-imagenes-mobile animate__animated animate__fadeInRightBig"
      >
        <img
          v-for="(image, index) in images"
          :key="index"
          :src="'https://image.tmdb.org/t/p/w1280' + image.backdrop_path"
          alt=""
        />
      </div>
    </div>

    <div class="proximamente-wrapper-desktop">
      <h4 class="animate__animated animate__fadeInLeftBig animate__delay-1s">
        Próximamente
      </h4>

      <div
        class="proximamente-imagenes-desktop animate__animated animate__fadeInRightBig animate__delay-2s"
      >
        <ImagenProximamente
          v-for="(image, index) in images"
          :key="index"
          :title="image.title"
          :image="'https://image.tmdb.org/t/p/w1280' + image.backdrop_path"
        />
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import ImagenProximamente from "./ImagenProximamente";

export default {
  name: "Proximamente",
  components: {
    ImagenProximamente,
  },
  data() {
    return {
      images: [],
    };
  },
  mounted() {
    axios
      .get(
        "https://api.themoviedb.org/3/movie/upcoming?api_key=6f26fd536dd6192ec8a57e94141f8b20"
      )
      .then((response) => {
        this.images = response.data.results.slice(0, 4);
      });
  },
};
</script>

<style lang="scss" scoped>
.proximamente-wrapper {
  color: white;
}
.proximamente-wrapper-mobile {
  padding: 40px 0 0 14px;
}
.proximamente-wrapper-mobile h1 {
  font-family: "Raleway";
  font-size: 20px;
  font-weight: 800;
  font-stretch: normal;
  font-style: normal;
  line-height: normal;
  letter-spacing: normal;
  color: white;
}
.proximamente-imagenes-mobile {
  display: block;
  grid-template-columns: 100%;
  padding: 0 15.3px 10px 0;
}
.proximamente-imagenes-mobile img {
  width: 100%;
  height: auto;
  margin-bottom: 10px;
}
// ----------------- desktop -----------------
.proximamente-wrapper-desktop {
  display: none;
  width: 80%;
  margin: 0 auto 0 auto;
  padding: 17px 0 0 0;
  justify-content: center;
}
.proximamente-wrapper-desktop h4 {
  font-family: "Montserrat";
  font-size: 20px;
  font-weight: bold;
  margin: 0;
}
.proximamente-imagenes-desktop {
  display: inline-flex;
  overflow: hidden;
  width: 100%;
  padding-top: 23px;
}
.proximamente-imagenes-desktop img {
  width: 255px;
  height: 155px;
}

@media screen and (min-width: 760px) {
  .proximamente-wrapper-desktop {
    display: block;
  }
  .proximamente-wrapper-mobile {
    display: none;
  }
}
</style>