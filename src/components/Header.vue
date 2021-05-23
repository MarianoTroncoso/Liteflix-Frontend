<template>
  <div class="header-wrapper">
    <a href="#" id="burger">
      <img src="../../static/burger.svg" alt="" />
    </a>
    <a href="#" id="brand-logo">
      <img src="../../static/liteflix.svg" alt="" />
    </a>
  </div>
</template>

<script>
export default {
  name: "Header",
};
</script>

<style lang="scss" scoped>
.header-wrapper {
  display: flex;
  justify-content: center;
}
#burger {
  position: absolute;
  left: 0;
  margin: 0.62rem 6.0625rem 0.56rem 15px;
}
#brand-logo {
  margin: 0.76rem;
}
</style>