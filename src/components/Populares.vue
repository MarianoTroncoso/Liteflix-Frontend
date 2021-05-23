<template>
  <div class="populares">
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
.populares {
  margin-top: 40.7px;
}

img {
  width: 253px;
  height: 507px;
  // margin: 9.3px 31.4px 3px 0.9px;
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
</style>