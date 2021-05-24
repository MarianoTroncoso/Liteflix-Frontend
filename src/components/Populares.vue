<template>
  <!-- <div class="populares">
    <p class="text-uppercase">Populares de Liteflix</p>
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
  <div class="populares-wrapper-mobile">
    <h1>Populares de Liteflix</h1>
    <div class="populares-imagenes">
      <img v-for="(image, index) in images" :key="index" :src="image" alt="" />
    </div>
  </div>
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
      ],
    };
  },
};
</script>

<style lang="scss" scoped>
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
  color: white;
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
  color: white;
}
*/
</style>