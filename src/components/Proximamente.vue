<template>
  <div class="proximamente-wrapper">
    <div class="proximamente-wrapper-mobile">
      <h1>Proxímamente</h1>
      <div class="proximamente-imagenes-mobile">
        <img
          v-for="(image, index) in images"
          :key="index"
          :src="image"
          alt=""
        />
      </div>
    </div>
    <!--
    <div class="proximamente-wrapper-desktop bg-secondary">
      <h4>Próximamente</h4>
      <img
        class="col-3"
        v-for="(image, index) in images"
        :key="index"
        :src="image"
        alt=""
      />
    </div>
    -->
    <div class="proximamente-wrapper-desktop">
      <h4>Próximamente</h4>
      <div class="carousel">
        <div class="carouselbox">
          <img
            v-for="(image, index) in images"
            :key="index"
            :src="image"
            alt=""
            :class="'img-' + index"
          />
          <a class="switchLeft sliderButton">&lt;</a>
          <!-- :onClick="sliderScrollLeft()" -->
          <a class="switchRight sliderButton">></a>
          <!-- :onClick="sliderScrollRight()" -->
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Proximamente",
  data() {
    return {
      images: [
        "https://image.tmdb.org/t/p/w1280/6ELCZlTA5lGUops70hKdB83WJxH.jpg",
        "https://image.tmdb.org/t/p/w1280/inJjDhCjfhh3RtrJWBmmDqeuSYC.jpg",
        "https://image.tmdb.org/t/p/w1280/ouOojiypBE6CD1aqcHPVq7cJf2R.jpg",
        "https://image.tmdb.org/t/p/w1280/lkInRiMtLgl9u9xE0By5hqf66K8.jpg",
        "https://image.tmdb.org/t/p/w1280/6ELCZlTA5lGUops70hKdB83WJxH.jpg",
        "https://image.tmdb.org/t/p/w1280/inJjDhCjfhh3RtrJWBmmDqeuSYC.jpg",
        "https://image.tmdb.org/t/p/w1280/ouOojiypBE6CD1aqcHPVq7cJf2R.jpg",
        "https://image.tmdb.org/t/p/w1280/lkInRiMtLgl9u9xE0By5hqf66K8.jpg",
      ],
    };
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
// .proximamente-imagenes-mobile {
//   display: grid;
//   grid-template-columns: 100%;
//   padding: 0 15.3px 10px 0;
// }
// .proximamente-imagenes-mobile img {
//   width: 100%;
//   height: auto;
//   margin-bottom: 10px;
// }
.proximamente-wrapper-desktop {
  display: none;
  padding: 80px 155px 0 164px;
}
.proximamente-wrapper-desktop h4 {
  font-family: "Montserrat";
  font-size: 20px;
  font-weight: bold;
  margin: 0;
}

@media screen and (min-width: 760px) {
  .proximamente-wrapper-desktop {
    display: block;
  }
  .proximamente-wrapper-mobile {
    display: none;
  }
}
/* video */
.carousel {
  height: 250px;
  // width: 80%;
  position: relative;
}
.carousel .switchLeft,
.carousel .switchRight {
  color: white;
  font-weight: bold;
  // height: 100%;
  // width: 45px;
  // line-height: 250px;
  font-size: 25px;
  text-align: center;
  // top: 0;
  z-index: 3;
  text-decoration: none;
}
.carousel .switchLeft {
  position: absolute;
  left: 0; //!cuidado
}
.carousel .switchRight {
  position: absolute;
  right: 0; //!cuidado
}
.carouselbox {
  // height: 250px;
  width: auto;
  overflow: hidden; //scroll
  white-space: nowrap;
  display: inline-block;
  text-align: center;
  // padding-bottom: 10px !important;
  padding: 23px 0 0 0;
  display: flex;
  align-items: center;
}
.carouselbox img {
  width: 255px;
  height: 155px;
  background-size: cover;
  // margin: 5px 10px;
  margin: 0 31px 0 0;
  transition: 0.5s ease;
  z-index: 2;
}
.carouselbox img:hover {
  // transform: scale(1.4);
  // z-index: 5;
}
/*
img {
  width: 255px;
  height: 155px;
  margin: 20.3px 31px 0 0;
}

.container {
  margin: 0;
}

.col-3 {
  padding: 0;
}

p {
  font-family: Montserrat;
  font-size: 20px;
  font-weight: bold;
  font-stretch: normal;
  font-style: normal;
  line-height: normal;
  letter-spacing: normal;
  color: white;
  margin-bottom: 0;
}
*/
</style>