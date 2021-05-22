<template>
  <div class="homepage-container">
    <div class="pl-3">
      <Header />
      <Destacada />
    </div>
  </div>
</template>

<script>
import Header from "../components/Header";
import Destacada from "../components/Destacada";

export default {
  name: "Homepage",
  components: {
    Header,
    Destacada,
  },
  data() {
    return {};
  },
};
</script>

<style lang="scss" scoped>
.homepage-container {
  background-image: url("https://image.tmdb.org/t/p/w1280/c0izdYdnTe4uMRifHgvTA85wPz0.jpg"); // backdrop path
  background-repeat: no-repeat;
  background-size: 100%;
  padding-left: 165px;
}
</style>
