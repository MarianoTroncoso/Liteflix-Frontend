<template>
  <div class="sidebar-wrapper">
    <a id="burger" class="openbtn" v-on:click="openNav">
      <img src="../../static/burger.svg" alt="" />
    </a>
    <a id="brand-logo">
      <img src="../../static/liteflix.svg" alt="" />
    </a>
    <div id="mySidebar" class="sidebar">
      <div class="d-flex">
        <a v-on:click="closeNav">
          <img src="../../static/burger.svg" alt="" />
        </a>
        <a> <img src="../../static/liteflix.svg" alt="" /> </a>
      </div>
      <div class="sidebar-user">
        <div class="sidebar-user-image">
          <img src="../../static/fill-1.svg" alt="" />
        </div>
        <div class="sidebar-user-name"><span>Ernesto Garmendia</span></div>
      </div>
      <div class="sidebar-settings">
        <a href="#">Cambiar Usuario</a>
        <div class="line"></div>
        <a href="#">Configuración</a>
        <div class="line"></div>
        <a href="#">Ayuda</a>
        <div class="line"></div>
      </div>
      <div class="sidebar-sections">
        <div class="d-flex novedades">
          <div class="btn position-relative bell">
            <span class="rounded-circle bg-danger"></span>
          </div>
          <a href="#">Novedades</a>
        </div>
        <ul>
          <li>Series</li>
          <li>Peliculas</li>
          <li>Mi lista</li>
          <li>Niños</li>
        </ul>
      </div>
      <div class="button sidebar-add-button">
        <a href="#">
          <img src="../../static/plus.svg" alt="" />
          <span>Agregar película</span></a
        >
      </div>
      <div class="sidebar-logout"><a href="#">Log out</a></div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Sidebar",
  methods: {
    openNav() {
      document.getElementById("mySidebar").style.width = "250px";
      // document.getElementById("brand-logo").style.display = "none";
    },
    closeNav() {
      document.getElementById("mySidebar").style.width = "0";
      // document.getElementById("brand-logo").style.display = "block";
    },
  },
};
</script>

<style lang="scss" scoped>
.sidebar-wrapper {
  display: flex;
  justify-content: center;
  transition: margin-left 0.5s;
}
#brand-logo {
  margin: 0.76rem;
}
#burger {
  position: absolute;
  left: 0;
}
.sidebar {
  height: 100%;
  width: 0;
  position: fixed;
  z-index: 1;
  top: 0;
  left: 0;
  background-color: #000000;
  overflow-x: hidden;
  transition: 0.7s;
}
.sidebar a {
  padding: 0.5rem 0px 0px 0.65rem;
  text-decoration: none;
  color: white;
  transition: 0.3s;
}
.sidebar a:hover {
  color: #f1f1f1;
}
.sidebar .closebtn {
  position: absolute;
  top: 0;
  right: 1.56rem;
  font-size: 36px;
  margin-left: 50px;
}
.openbtn {
  font-size: 20px;
  cursor: pointer;
  color: white;
  padding: 10px 15px;
  border: none;
}
.sidebar-user {
  width: 193px;
  height: 37px;
  padding: 6px 0px 6px 7px;
  border-radius: 18.5px;
  box-shadow: 0 0 10px 0 rgba(0, 0, 0, 0.1);
  background-color: #222222;
  display: flex;
  margin: 22px 20px 0 15px;
}
.sidebar-user-image {
  width: 25px;
  height: 25px;
  background: #ce00ff;
  margin: 0 8px 0 0;
  padding: 0.3125rem 0.3563rem 0.3125rem 0.375rem;
  border-radius: 0.9375rem;
  display: flex;
  justify-content: center;
  align-content: center;
}
.sidebar-user-name {
  margin: 5px 0 5px 8px;
  font-family: "Montserrat";
  font-size: 12px;
  font-weight: normal;
  font-stretch: normal;
  font-style: normal;
  line-height: normal;
  letter-spacing: normal;
  color: white;
}
.sidebar-settings {
  margin: 20px 20px 0 15px;
}
.sidebar-settings a {
  margin: 0 94px 7px 0;
  padding: 0;
  font-family: "Montserrat";
  font-size: 12px;
  font-weight: normal;
  font-stretch: normal;
  font-style: normal;
  line-height: normal;
  letter-spacing: normal;
  color: white;
}
.line {
  width: 193px;
  height: 2px;
  margin: 7px 0 6px;
  border: solid 1px #222222;
}
.sidebar-sections {
  padding: 25px 0 0 0;
}
.novedades {
  color: white;
  margin: 0 116px 12px 15px;
}
.novedades a {
  padding: 0;
  margin: 1px 0 0 5px;
  font-family: "Montserrat";
  font-size: 14px;
  font-weight: normal;
  font-stretch: normal;
  font-style: normal;
  line-height: normal;
  letter-spacing: normal;
  color: white;
}
.novedades button {
  border: 0;
  padding: 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
ul li {
  color: white;
  font-size: 14px;
  font-family: "Montserrat";
  margin-top: 12px;
}
.sidebar-sections ul {
  margin: 0 0 0 14px;
}
.sidebar-add-button {
  background-color: red;
  width: 193px;
  height: 40px;
  margin: 22px 0 0 14px;
  padding: 10px 42px 12px 11px;
  border-radius: 20px;
  font-size: 14px;
  color: white;
}
.sidebar-add-button a {
  padding: 0;
  display: flex;
}
.sidebar-add-button span {
  margin-left: 8px;
}
.sidebar-logout {
  padding: 27px 0 0 15px;
}
.sidebar-logout a {
  padding: 0;
  font-size: 12px;
  font-weight: bold;
  font-stretch: normal;
  font-style: normal;
  line-height: normal;
  letter-spacing: normal;
}
.bell {
  background-image: url("../../static/bell.svg");
  background-repeat: no-repeat;
  padding-right: 0;
}

.bell span {
  width: 6px;
  height: 6px;
  position: absolute;
  top: 2px;
  bottom: 8px;
  left: 8px;
}
</style>