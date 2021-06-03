<template>
  <div class="mis-peliculas-wrapper">
    <div class="mis-peliculas-wrapper-mobile">
      <h1 class="animate__animated animate__fadeInLeftBig">Mis películas</h1>
      <div
        class="mis-peliculas-imagenes-mobile animate__animated animate__fadeInRightBig"
      >
        <img
          v-for="(movie, index) in movies"
          :key="index"
          :src="'https://liteflix-test-api.herokuapp.com/image/' + movie.image"
          alt=""
        />
      </div>
    </div>
    <div class="mis-peliculas-wrapper-desktop">
      <h4 class="animate__animated animate__fadeInLeftBig animate__delay-1s">
        Mis películas
      </h4>
      <div
        class="mis-peliculas-imagenes-desktop animate__animated animate__fadeInRightBig animate__delay-2s"
      >
        <ImagenMisPeliculas
          v-for="(movie, index) in movies"
          :key="index"
          :title="movie.name"
          :category="movie.category"
          :image="
            'https://liteflix-test-api.herokuapp.com/image/' + movie.image
          "
        />
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import ImagenMisPeliculas from "./ImagenMisPeliculas";

export default {
  name: "MisPeliculas",
  /*
  methods: {
    sliderScrollLeft() {
      const sliders = this.$refs.carouselbox;
      sliders.scrollTo({
        top: 0,
        left: (scrollAmount -= scrollPerClick),
        behavior: "smooth",
      });

      if (scrollAmount < 0) {
        scrollAmount = 0;
      }

      console.log("Scroll Amount: ", scrollAmount);
    },
    sliderScrollRight() {
      const sliders = this.$refs.carouselbox;
      if (scrollAmount <= sliders.scrollWidth - sliders.clientWidth) {
        sliders.scrollTo({
          top: 0,
          left: (scrollAmount += scrollPerClick),
          behavior: "smooth",
        });
      }
      console.log("Scroll Amount: ", scrollAmount);
    },
  },
  */
  components: {
    ImagenMisPeliculas,
  },
  data() {
    return {
      movies: [],
    };
  },
  mounted() {
    axios
      .get("https://liteflix-test-api.herokuapp.com/movies")
      .then((response) => {
        this.movies = response.data.slice(0, 4);
        if (response.data.length > 4) {
          this.movies = response.data.slice(
            response.data.length - 4,
            response.data.length
          );
        } else {
          this.movies = response.data;
        }
      });
  },
};
</script>

<style lang="scss" scoped>
.mis-peliculas-wrapper {
  color: white;
}
.mis-peliculas-wrapper-mobile {
  padding: 40px 0 0 14px;
}
.mis-peliculas-wrapper-mobile h1 {
  font-family: "Raleway";
  font-size: 20px;
  font-weight: 800;
  font-stretch: normal;
  font-style: normal;
  line-height: normal;
  letter-spacing: normal;
  color: white;
}
.mis-peliculas-imagenes-mobile {
  display: block;
  grid-template-columns: 100%;
  padding: 0 15.3px 10px 0;
  // border: 2px solid red;
}
.mis-peliculas-imagenes-mobile img {
  width: 100%;
  height: auto;
  margin-bottom: 10px;
  // border: 2px solid blue;
}
// ----------------- desktop -----------------
.mis-peliculas-wrapper-desktop {
  display: none;
  // padding: 17px 0 60px 164px;
  padding: 27px 0 5% 0;
  // border: 2px solid yellow;
  width: 80%;
  margin: 0 auto 0 auto;
}
.mis-peliculas-wrapper-desktop h4 {
  font-family: "Montserrat";
  font-size: 20px;
  font-weight: bold;
  margin: 0;
}
.mis-peliculas-imagenes-desktop {
  // border: 2px solid red;
  display: inline-flex;
  overflow: hidden;
  padding: 23.3px 0 0 0;
  width: 100%;
}

.mis-peliculas-imagenes-desktop img {
  width: 255px;
  height: 155px;
  // margin-right: 31px;
}

/*
.carousel {
  margin: 0;
  padding: 20.3px 0 0 0;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
}
.carouselbox {
  width: auto;
  overflow: hidden;
  white-space: nowrap;
  display: inline-block;
  text-align: center;
  display: flex;
  align-items: center;
}
.carouselbox img {
  width: 250px;
  height: 155px;
  background-size: cover;
  margin: 0 31px 0 0;
  cursor: pointer;
  transition: 0.3s ease;
  z-index: 2;
}
.carousel .switchLeft,
.carousel .switchRight {
  color: white;
  font-weight: bold;
  height: 100%;
  width: 45px;
  font-size: 25px;
  text-align: center;
  display: flex;
  align-items: center;
  font-family: sans-serif;
  z-index: 3;
}
.carousel .switchLeft {
  position: absolute;
  left: -25px;
  text-decoration: none;
}
.carousel .switchRight {
  position: absolute;
  right: -50px;
  text-decoration: none;
}

.carousel img:hover {
  // transform: scale(1.4);
  // z-index: 5;
}
*/
@media screen and (min-width: 760px) {
  .mis-peliculas-wrapper-desktop {
    display: block;
  }
  .mis-peliculas-wrapper-mobile {
    display: none;
  }
}
</style>