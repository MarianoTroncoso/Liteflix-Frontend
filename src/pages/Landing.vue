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
  // poster
  background: url("https://image.tmdb.org/t/p/w1280/13B6onhL6FzSN2KaNeQeMML05pS.jpg")
      no-repeat,
    #000000 no-repeat;
  background-size: 100% 760px;
}
@media screen and (min-width: 760px) {
  .homepage-container {
    // backdrop
    background: url("https://image.tmdb.org/t/p/w1280/nz8xWrTKZzA5A7FgxaM4kfAoO1W.jpg")
        no-repeat,
      #000000 no-repeat;
    background-size: 100%;
  }
}
</style>
