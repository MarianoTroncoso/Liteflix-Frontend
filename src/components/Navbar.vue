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
/* .circle-button {
  display: block;
  width: 40px;
  height: 40px;
  background: red;
  border-radius: 20px;
  border: 0;
  background-image: url("../../static/plus.svg");
  background-position: 50% 50%;
  background-repeat: no-repeat;
  cursor: pointer;
} */

/*
.add-movie-button {
  display: flex; 
  align-items: center;
  justify-content: center;
  height: 40px;
  background-color: red;
  border: 0;
  border-radius: 20px;
}
.add-movie-button span {
  display: none;
  font-family: "Montserrat";
  font-size: 16px;
  color: white;
  margin-left: 8px;
}
.add-movie-button img {
  margin: 0 6px 0 6px;
}
.add-movie-button:hover {
  padding-right: 17px;
}
.add-movie-button:hover span {
  display: block;
}
*/
// ----------------
.add-movie-button span {
  max-width: 0;
  -webkit-transition: max-width 1s;
  transition: max-width 1s;
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
</style>