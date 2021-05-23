<template>
  <div class="homepage-container">
    <div class="pl-3">
      <!-- <Header /> -->
      <Header />
      <Destacada />
      <Proximamente />
      <Populares />
    </div>
  </div>
</template>

<script>
// import Header from "../components/Header";
import Header from "../components/Header";
import Destacada from "../components/Destacada";
import Proximamente from "../components/Proximamente";
import Populares from "../components/Populares";

export default {
  name: "Homepage",
  components: {
    // Header,
    Header,
    Destacada,
    Proximamente,
    Populares,
  },
  data() {
    return {};
  },
};
</script>

<style lang="scss" scoped>
.homepage-container {
  background: url("https://image.tmdb.org/t/p/w1280/inJjDhCjfhh3RtrJWBmmDqeuSYC.jpg")
      no-repeat,
    #000000 no-repeat;
  // background-repeat: no-repeat;
  background-size: 100% 760px;
  // padding-left: 165px;
}
</style>
