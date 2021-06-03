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
      <!-- <div class="carousel">
        <div class="carouselbox" ref="carouselbox">
          <img
            v-for="(image, index) in images"
            :key="index"
            :src="image"
            alt=""
            :class="'img-' + index"
          />
        </div>
        <a class="switchLeft sliderButton" @click="sliderScrollLeft">&lt;</a>
        <a class="switchRight sliderButton" @click="sliderScrollRight">></a>
      </div> -->
    </div>
  </div>
</template>

<script>
import axios from "axios";
import ImagenProximamente from "./ImagenProximamente";
/*
var scrollPerClick = 270;
var scrollAmount = 0;
*/

export default {
  name: "Proximamente",
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
        // console.log(this.images);
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
  // border: 2px solid red;
}
.proximamente-imagenes-mobile img {
  width: 100%;
  height: auto;
  margin-bottom: 10px;
  // border: 2px solid blue;
}
// ----------------- desktop -----------------
.proximamente-wrapper-desktop {
  display: none;
  // padding: 17px 0 0px 164px;
  // border: 2px solid green;
  width: 80%;
  margin: 0 auto 0 auto;
  padding: 17px 0 0 0;
  // display: flex;
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
  // border: 2px solid red;
  width: 100%;
  // padding: 23.3px 0px 0px 0px;
  padding-top: 23px;
}
.proximamente-imagenes-desktop img {
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
  .proximamente-wrapper-desktop {
    display: block;
  }
  .proximamente-wrapper-mobile {
    display: none;
  }
}
</style>