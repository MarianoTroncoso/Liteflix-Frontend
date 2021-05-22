<template>
  <div class="homepage-container">
    <div class="pl-3">
      <Header />
      <div>
        <p>ORIGINAL DE NETFLIX</p>
        <h1>KIDS AT SCHOOL</h1>
        <div>
          <button type="button" class="btn btn-secondary">reproducir</button>
          <button type="button" class="btn btn-secondary">mi lista</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Header from "../components/Header";
export default {
  name: "Homepage",
  components: {
    Header,
  },
  data() {
    return {};
  },
};
</script>

<style lang="scss" scoped>
.homepage-container {
  background-image: url("https://image.tmdb.org/t/p/w1280/inJjDhCjfhh3RtrJWBmmDqeuSYC.jpg");
  background-repeat: no-repeat;
  background-size: 100%;
  padding-left: 165px;
}
</style>
