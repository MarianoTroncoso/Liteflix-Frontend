<template>
  <nav class="navbar navbar-expand-lg navbar-light .bg-transparent">
    <div class="container-fluid">
      <a class="navbar-brands" href="#"
        ><img src="../../static/liteflix-icon.svg" alt=""
      /></a>
      <div class="collapse navbar-collapse" id="navbarSupportedContent">
        <ul class="navbar-nav me-auto mb-2 mb-lg-0">
          <li class="nav-item">
            <a class="nav-link active" aria-current="page" href="#">Inicio</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#">Series</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#">Películas</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#">Agregados recientemente</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#">Mi lista</a>
          </li>
          <li class="nav-item item-circle">
            <button type="button" class="bg-danger btn-circle text-white">
              <img class="plus" src="../../static/plus.svg" alt="" />
            </button>
          </li>
        </ul>
        <!-- derecha -->
        <div>
          <ul class="navbar-nav me-auto mb-2 mb-lg-0">
            <li class="nav-item">
              <a class="nav-link" href="#">Niños</a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="#">
                <img class="bell" src="../../static/bell-icon.svg" alt="" />
              </a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="#">
                <img src="../../static/user-01-icon.svg" alt="" />
              </a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="#">
                <img src="../../static/arrow-icon.svg" alt="" />
              </a>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </nav>
</template>

<script>
export default {
  name: "Header",
};
</script>

<style lang="scss" scoped>
#navbarSupportedContent {
  padding-top: 12px;
}

.container-fluid {
  padding: 0 165px 0 0;
}

.plus {
  width: 15.9px;
  height: 15px;
  margin-bottom: 5px;
}

.bell {
  width: 14px;
  height: 16px;
}

.item-circle {
  margin-left: 10px;
}

.btn-circle {
  padding: 0px;
  border: 0px;
  width: 40px;
  height: 40px;
  border-radius: 20px;
  padding: 0px;
}

.active {
  font-weight: bold !important;
}
.navbar-brands img {
  margin-right: 11px;
}

.navbar-light .navbar-nav .nav-link {
  color: white;
  font-size: 14px;
  padding: 12px 9px;
  font-family: "Montserrat";
}
</style>