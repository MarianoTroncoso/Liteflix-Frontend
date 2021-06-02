<template>
  <div class="mis-peliculas-wrapper">
    <div class="mis-peliculas-wrapper-desktop">
      <h1>Mis películas</h1>
      <div class="mis-peliculas-imagenes-desktop">
        <img
          v-for="(image, index) in images"
          :key="index"
          :src="image"
          alt=""
        />
      </div>
    </div>
    <div class="mis-peliculas-wrapper-mobile">
      <h1>Mis películas</h1>
      <div class="mis-peliculas-imagenes-mobile">
        <img
          v-for="(image, index) in images"
          :key="index"
          :src="image"
          alt=""
        />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      images: [
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
.mis-peliculas-wrapper-desktop {
  // border: 2px solid white;
  display: none;
  color: white;
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