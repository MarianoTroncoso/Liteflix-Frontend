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
    <button type="button" class="circle-button"></button>
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
  // align-items: baseline;
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
  // font-weight: bold;
  font-stretch: normal;
  font-style: normal;
  line-height: normal;
  letter-spacing: normal;
}
.circle-button {
  display: block;
  width: 40px;
  height: 40px;
  background: red;
  border-radius: 20px;
  border: 0;
  // moz-border-radius: 20px;
  // -webkit-border-radius: 20px;
  background-image: url("../../static/plus.svg");
  background-position: 50% 50%;
  background-repeat: no-repeat;
  cursor: pointer;
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