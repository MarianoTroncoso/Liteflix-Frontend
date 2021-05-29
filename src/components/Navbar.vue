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
    <!-- RIGHT ITEMS -->
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
          <div class="action">
            <div class="profile">
              <img src="../../static/user-01.svg" alt="" />
            </div>
            <div class="menu" ref="menu">
              <!-- perfiles -->
              <ul class="ul-perfiles">
                <li>
                  <button class="selected-user-button">
                    <div class="selected-user-image">
                      <img src="../../static/fill-1.svg" alt="" />
                    </div>
                    <span>Ernesto G…</span>
                  </button>
                </li>
                <li>
                  <button class="not-selected-user-button">
                    <div class="not-selected-user-image">
                      <img src="../../static/fill-2.svg" alt="" />
                    </div>
                    <span>User 03</span>
                  </button>
                </li>
                <li>
                  <button class="not-selected-user-button">
                    <div class="not-selected-user-image">
                      <img src="../../static/fill-2.svg" alt="" />
                    </div>
                    <span>User 04</span>
                  </button>
                </li>
              </ul>
              <!-- settings -->
              <ul class="ul-settings">
                <li>
                  <a href="#">Configuración</a>
                </li>
                <li>
                  <a href="#">Ayuda</a>
                </li>
                <li>
                  <a href="#"><b>Log out</b></a>
                </li>
              </ul>
            </div>
          </div>
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
    // menuShow() {
    //   const toggleMenu = this.$refs.menu;
    //   toggleMenu.classList.toggle("active");
    // },
    // menuHide() {
    //   const toggleMenu = this.$refs.menu;
    //   toggleMenu.classList.remove("active");
    // },
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
  flex-wrap: wrap;
  position: relative;
  width: auto;
}
.right-items > ul {
  display: inline-flex;
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

.action {
  margin: 5px 5px 0 0;
  padding: 0;
  // border: 2px solid red;
  //position: absolute;
  top: 0;
  right: 0;
  // background-color: red;
}

.action:hover .menu {
  top: 50px;
  visibility: visible;
  opacity: 1;
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
  top: 20px;
  right: -8px;
  padding: 11px 9px 4px 10px;
  background-color: #fff;
  width: 100%;
  box-sizing: 0 5px 25px rgba(0, 0, 0, 0.1);
  border-radius: 5px;
  transition: 0.3s;
  visibility: hidden;
  opacity: 0;
}
// .action .menu.active {
//   top: 50px;
//   visibility: visible;
//   opacity: 1;
// }
.action .menu::before {
  content: "";
  position: absolute;
  top: -5px;
  right: 28px;
  width: 20px;
  height: 20px;
  background-color: #fff;
  transform: rotate(45deg);
  border-radius: 4px;
}

.action .menu ul li {
  margin: 0;
  list-style: none;

  display: flex;
  align-items: center;
  justify-content: center;
}
.action .menu ul li img {
  transition: 0.5s;
}

.action .menu ul li a {
  display: inline-block;
  color: #555;
  font-size: 12px;
  font-weight: 500;
  transition: 0.5s;
}

.ul-perfiles li {
  padding-top: 5px;
}
.ul-perfiles button {
  width: 111px;
  height: 37px;
  padding: 6px 6px 6px 7px;
  border: 0;
  border-radius: 18.5px;
  // box-shadow: 0 0 10px 0 rgba(0, 0, 0, 0.1);
  background-color: white;
  display: flex;
  // justify-content: center;
  align-items: center;
  position: relative;
}

.selected-user-image {
  // border: 2px solid red;
  background-color: #ce00ff;
  width: 25px;
  height: 25px;
  border-radius: 15px;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 0 0 0 2px;
}
.selected-user-button {
  box-shadow: 0 0 10px 0 rgba(0, 0, 0, 0.1);
}
.not-selected-user-button {
  color: #9b9b9b;
}
.not-selected-user-image {
  // border: 2px solid red;
  background-color: #9b9b9b;
  width: 25px;
  height: 25px;
  border-radius: 15px;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 0 0 0 2px;
}
.ul-perfiles span {
  font-family: "Montserrat";
  font-size: 12px;
  margin-left: 5px;
}
.ul-settings {
  // border: 2px solid blue;
}
.ul-settings li {
  // border: 2px solid blue;
  display: flex !important;
  justify-content: left !important;
  padding: 7px 0 7px 0;
  border-bottom: 1px solid rgba(0, 0, 0, 0.1);
}
.ul-settings li:last-child {
  border-bottom: 0;
}
</style>