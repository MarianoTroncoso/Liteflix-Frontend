<template>
  <nav class="navbar navbar-expand-lg navbar-light .bg-transparent">
    <div class="container-fluid">
      <!-- logo -->
      <a class="navbar-brand" href="#">
        <img src="../../static/liteflix-icon.svg" alt="" />
      </a>
      <!-- Inicio, Series, Peliculas, Agregados recientemente, Mi lista, + -->
      <div class="collapse navbar-collapse no-brand">
        <ul class="navbar-nav me-auto mb-2 mb-lg-0">
          <li class="nav-item active">
            <a class="nav-link" href="#">Home</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#">Link</a>
          </li>
        </ul>
        <div>
          <ul class="navbar-nav me-auto mb-2 mb-lg-0">
            <li class="nav-item active">
              <a class="nav-link" href="#">Home</a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="#">Link</a>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </nav>
</template>

<script>
export default {
  name: "Header2",
};
</script>

<style lang="scss" scoped>
.container-fluid {
  padding: 0;
  display: flex;
  align-items: center;
}
.navbar {
  padding: 0;
}
.navbar-brand {
  margin: 0;
  padding: 0;
}
.nav-link {
  padding: 0 !important;
  font-size: 14px;
  // margin-top: 20px;
}
</style>