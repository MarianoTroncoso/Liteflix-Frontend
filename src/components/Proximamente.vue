<template>
  <div class="proximamente">
    <p>Próximamente</p>
    <img
      class="col-3"
      v-for="(image, index) in images"
      :key="index"
      :src="image"
      alt=""
    />
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
</style>