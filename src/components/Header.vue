<template>
  <div class="header-wrapper">
    <!-- mobile -->
    <div class="header-wrapper-mobile">
      <!-- logo y sidebar-->
      <SideBar />
    </div>
    <div class="header-wrapper-desktop">
      <!-- navbar -->
      <Navbar />
    </div>
  </div>
</template>

<script>
import Navbar from "./Navbar";
import SideBar from "./Sidebar";
export default {
  name: "Header",
  components: {
    SideBar,
    Navbar,
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