<template>
  <div class="populares-wrapper">
    <div class="populares-wrapper-desktop">
      <h4>Populares de Liteflix</h4>
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
    <div class="populares-wrapper-mobile">
      <h1>Populares de Liteflix</h1>
      <div class="populares-imagenes">
        <img
          v-for="(image, index) in images"
          :key="index"
          :src="image"
          alt=""
        />
      </div>
    </div>
  </div>
  <!-- <div class="populares">
    <h4 class="text-uppercase">Populares de Liteflix</h4>
    <div>
      <img
        class="col-3 layer"
        v-for="(image, index) in images"
        :key="index"
        :src="image"
        alt=""
      />
    </div>
  </div> -->
</template>

<script>
export default {
  name: "Populares",
  data() {
    return {
      images: [
        "https://cdn.zeplin.io/5d1a67242bdce756be65f5f6/assets/1940B1C9-498A-499B-B30C-D77251124177.png",
        "https://cdn.zeplin.io/5d1a67242bdce756be65f5f6/assets/19511682-3234-4CDF-AB50-9B8331D8314E.png",
        "https://cdn.zeplin.io/5d1a67242bdce756be65f5f6/assets/BA2C81CF-CC66-4797-9A32-858676807134.png",
        "https://cdn.zeplin.io/5d1a67242bdce756be65f5f6/assets/3616C539-3984-499F-A5E7-9E517C58F465.png",
        "https://cdn.zeplin.io/5d1a67242bdce756be65f5f6/assets/1940B1C9-498A-499B-B30C-D77251124177.png",
        "https://cdn.zeplin.io/5d1a67242bdce756be65f5f6/assets/19511682-3234-4CDF-AB50-9B8331D8314E.png",
        "https://cdn.zeplin.io/5d1a67242bdce756be65f5f6/assets/BA2C81CF-CC66-4797-9A32-858676807134.png",
        "https://cdn.zeplin.io/5d1a67242bdce756be65f5f6/assets/3616C539-3984-499F-A5E7-9E517C58F465.png",
      ],
    };
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
.populares-imagenes {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  grid-gap: 3px;
}
.populares-imagenes img {
  width: 100%;
  height: auto;
}
.populares-wrapper-desktop {
  display: none;

  padding: 40.7px 224px 0 165px; // 40.7px 164.8px 0 165px
}
.populares-wrapper-desktop h4 {
  font-family: "Montserrat";
  font-size: 20px;
  font-weight: bold;
  text-transform: uppercase;
  margin: 0;
}

/*
.populares {
  margin-top: 40.7px;
}
img {
  width: 253px;
  height: 507px;
  margin: 9.3px 31.4px 0 0;
  object-fit: contain;
  background-color: #000000;
}
p {
  margin: 0 29.2px 9px 0;
  font-family: Montserrat;
  font-size: 20px;
  font-weight: bold;
  font-stretch: normal;
  font-style: normal;
  line-height: normal;
  letter-spacing: normal;
}
*/
.carousel {
  // height: 250px;
  // width: 80%;
  position: relative;
  padding: 9px 0 0 0;
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
  // padding: 23px 0 0 0;
  display: flex;
  align-items: center;
}
.carouselbox img {
  // width: 255px;
  // height: 155px;
  background-size: cover;
  margin-right: 29.2px;
  transition: 0.5s ease;
  z-index: 2;
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