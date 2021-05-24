<template>
  <!-- <div class="proximamente">
    <p>Próximamente</p>
    <img
      class="col-3"
      v-for="(image, index) in images"
      :key="index"
      :src="image"
      alt=""
    />
  </div> -->
  <div class="proximamente-wrapper-mobile">
    <h1>Proxímamente</h1>
    <div class="proximamente-imagenes">
      <img v-for="(image, index) in images" :key="index" :src="image" alt="" />
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
      ],
    };
  },
};
</script>

<style lang="scss" scoped>
.proximamente-wrapper-mobile {
  // background-color: gray;
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
  // margin-left: 14px;
}
.proximamente-imagenes {
  display: grid;
  grid-template-columns: 100%;
  padding: 0 15.3px 10px 0;
}
.proximamente-imagenes img {
  width: 100%;
  height: auto;
  margin-bottom: 10px;
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