<template>
  <div class="navbar-wrapper">
    <a id="logo-brand" href="#"
      ><img src="../../static/liteflix.svg" alt=""
    /></a>
    <ul>
      <li><a href="#">Inicio</a></li>
      <li><a href="#">Series</a></li>
      <li><a href="#">Peliculas</a></li>
      <li><a href="#">Agregados recientemente</a></li>
      <li><a href="#">Mi lista</a></li>
    </ul>
    <button class="add-movie-button">
      <img src="../../static/plus.svg" alt="" />
      <span>Agregar película</span>
    </button>
    <!-- <div class="action">
      <div class="profile" @click="menuToggle">
        <img src="../../static/user-01.svg" alt="" />
      </div>
      <div class="menu" ref="menu">
        <ul>
          <li>
            <img src="../../static/fill-1.svg" alt="" /><a href="#"
              >Ernesto G…</a
            >
          </li>
          <li>
            <img src="../../static/fill-1.svg" alt="" /><a href="#">User 03</a>
          </li>
          <li>
            <img src="../../static/fill-1.svg" alt="" /><a href="#">User 04</a>
          </li>
        </ul>
      </div>
    </div> -->
    <div class="right-items">
      <ul>
        <li><a href="#">Niños</a></li>
        <li>
          <a href="#"
            ><div class="btn position-relative bell">
              <span class="rounded-circle bg-danger"></span></div
          ></a>
        </li>
        <li>
          <a href="#"><img src="../../static/user-01.svg" alt="" /></a>
        </li>
        <li>
          <a href="#"><img src="../../static/arrow.svg" alt="" /></a>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: "Navbar",
  methods: {
    menuToggle() {
      const toggleMenu = this.$refs.menu;
      toggleMenu.classList.toggle("active");
    },
  },
};
</script>

<style lang="scss" scoped>
.navbar-wrapper {
  padding: 20px 165px 0 165px;
  display: flex;
}
#logo-brand {
  margin-right: 20px;
}
ul {
  padding: 2px 0 0 0;
}
li {
  display: inline;
  margin-right: 18px;
}
a {
  text-decoration: none;
  color: white;
  font-family: "Montserrat";
  font-size: 14px;
  font-stretch: normal;
  font-style: normal;
  line-height: normal;
  letter-spacing: normal;
}

.add-movie-button span {
  max-width: 0;
  -webkit-transition: max-width 1s;
  transition: max-width 0.5s;
  display: inline-block;
  vertical-align: top;
  white-space: nowrap;
  overflow: hidden;
  font-family: "Montserrat";
  font-size: 16px;
  color: white;
}
.add-movie-button:hover span {
  max-width: 7rem;
  margin: 0 17px 0 0;
}
.add-movie-button {
  background-color: red;
  border: 0;
  border-radius: 20px;
  display: flex;
  align-items: center;
  padding: 0;
  height: 40px;
}
.add-movie-button img {
  margin: 0 12px 0 12px;
}
.right-items {
  margin-left: auto;
  display: flex;
}
.right-items li {
  margin-left: 20px;
  margin-right: 0;
}
.right-items li:first-child {
  margin-left: 0px;
}
.right-items li:last-child {
  margin-left: 0px;
}
.bell {
  background-image: url("../../static/bell.svg");
  background-repeat: no-repeat;
  padding-right: 0;
  margin-bottom: 2px;
}
.bell span {
  width: 6px;
  height: 6px;
  position: absolute;
  top: 2px;
  bottom: 8px;
  left: 8px;
}
// ---------------------------- TOGGLE MENU ----------------------------
/*
.action {
  margin: 0px;
  padding: 0;
  position: fixed;
  top: 20px;
  right: 30px;
  background-color: red;
}
.action .profile {
  position: relative;
  width: 25px;
  height: 25px;
  border-radius: 50%;
  overflow: hidden;
  cursor: pointer;
}
.action .profile img {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
}
.action .menu {
  position: absolute;
  top: 120px;
  right: -10px;
  padding: 5px 10px;
  background-color: #fff;
  width: 130px;
  box-sizing: 0 5px 25px rgba(0, 0, 0, 0.1);
  border-radius: 15px;
  transition: 0.3s;
  visibility: hidden;
  opacity: 0;
}
.action .menu.active {
  top: 80px;
  visibility: visible;
  opacity: 1;
}
.action .menu::before {
  content: "";
  position: absolute;
  top: -5px;
  right: 28px;
  width: 20px;
  height: 20px;
  background-color: #fff;
  transform: rotate(45deg);
  border-radius: 3px;
}

.action .menu ul li {
  margin: 0;
  list-style: none;
  padding: 10px 0;
  border-bottom: 1px solid rgba(0, 0, 0, 0.1);
  display: flex;
  align-items: center;
  justify-content: center;
}
.action .menu ul li img {
  max-width: 20px;
  margin-right: 20px;
  opacity: 0.5;
  transition: 0.5s;
}
.action .menu ul li:hover img {
  opacity: 1;
}
.action .menu ul li a {
  display: inline-block;
  color: #555;
  font-weight: 500;
  transition: 0.5s;
}
.action .menu ul li:hover a {
  color: #ff5d94;
}
*/
</style>