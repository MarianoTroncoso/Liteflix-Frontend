<template>
  <div class="header-wrapper">
    <!-- mobile -->
    <div class="header-wrapper-mobile">
      <!-- logo y sidebar-->
      <SideBar />
    </div>
    <div class="header-wrapper-desktop">
      <!-- navbar -->
      <h1>hola</h1>
    </div>
  </div>
</template>

<script>
import SideBar from "./Sidebar";
export default {
  name: "Header",
  components: {
    SideBar,
  },
};
</script>

<style lang="scss" scoped>
// desktop
.header-wrapper-desktop {
  display: none;
}

@media screen and (min-width: 769px) {
  .header-wrapper-desktop {
    display: block;
  }
  .header-wrapper-mobile {
    display: none;
  }
}
</style>