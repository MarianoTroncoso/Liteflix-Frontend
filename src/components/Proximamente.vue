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

    <div class="proximamente-wrapper-desktop">
      <!-- <h4>Próximamente</h4>
      <div class="carousel">
        <div class="carouselbox">
          <img
            v-for="(image, index) in images"
            :key="index"
            :src="image"
            alt=""
            :class="'img-' + index"
          />
          
        </div>
      </div> -->
      <div class="carousel">
        <h1>Hola</h1>
        <div class="carouselbox">
          <!-- imagenes -->
        </div>
        <a class="switchLeft sliderButton">&lt;</a>
        <a class="switchRight sliderButton">></a>
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
.proximamente-imagenes-mobile {
  display: grid;
  grid-template-columns: 100%;
  padding: 0 15.3px 10px 0;
}
.proximamente-imagenes-mobile img {
  width: 100%;
  height: auto;
  margin-bottom: 10px;
}
.proximamente-wrapper-desktop {
  display: none;
  padding: 80px 224px 0 164px; // 80px 155px 0 164px
}
.proximamente-wrapper-desktop h4 {
  font-family: "Montserrat";
  font-size: 20px;
  font-weight: bold;
  margin: 0;
}

/* video */
.carousel {
  margin: 0;
  padding: 0;
  background-color: #262626;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
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