<template>
  <div class="header-wrapper">
    <a id="burger" class="openbtn" v-on:click="openNav">
      <img src="../../static/burger.svg" alt="" />
    </a>
    <a id="brand-logo">
      <img src="../../static/liteflix.svg" alt="" />
    </a>
    <!-- sidebar -->
    <div id="mySidebar" class="sidebar">
      <div class="d-flex">
        <a>
          <img src="../../static/burger.svg" alt="" />
        </a>
        <a> <img src="../../static/liteflix.svg" alt="" /> </a>
      </div>
      <div class="user-sidebar">
        <div class="circle"><img src="../../static/fill-1.svg" alt="" /></div>
        <span>Ernesto Garmendia</span>
      </div>
      <a href="#">About</a>
      <a href="#">Services</a>
    </div>
  </div>
</template>

<script>
export default {
  name: "Header",
  methods: {
    openNav() {
      document.getElementById("mySidebar").style.width = "250px";
      // document.getElementById("main").style.marginLeft = "250px";
      // alert("abrir");
    },
    closeNav() {
      document.getElementById("mySidebar").style.width = "0";
      // document.getElementById("main").style.marginLeft = "0";
      // alert("cerrar");
    },
  },
};
</script>

<style lang="scss" scoped>
.header-wrapper {
  display: flex;
  justify-content: center;
  transition: margin-left 0.5s;
  // padding: 16px;
}
#burger {
  position: absolute;
  left: 0;
  margin: 0.62rem 6.0625rem 0.56rem 15px;
}
#brand-logo {
  margin: 0.76rem;
}

// collapse sidebar
.sidebar {
  height: 100%;
  width: 0;
  position: fixed;
  z-index: 1;
  top: 0;
  left: 0;
  background-color: #000000;
  overflow-x: hidden;
  transition: 0.5s;
  // padding-top: 60px;
}
.sidebar a {
  padding: 0.5rem 0px 0px 0.65rem;
  text-decoration: none;
  font-size: 25px;
  color: #818181;
  display: block;
  transition: 0.3s;
}
.sidebar a:hover {
  color: #f1f1f1;
}
.sidebar .closebtn {
  position: absolute;
  top: 0;
  right: 25px;
  font-size: 36px;
  margin-left: 50px;
}

.openbtn {
  font-size: 20px;
  cursor: pointer;
  // background-color: #111;
  color: white;
  padding: 10px 15px;
  border: none;
}
.user-sidebar {
  background: #222222;
  color: white;
  width: 12.06rem;
  height: 2.31rem;
  border-radius: 1.15rem;
  font-size: 12px;
  font-family: "Montserrat";
  display: flex;
  // justify-content: center;
  align-items: center;
}
.circle {
  width: 1.56rem;
  height: 1.56rem;
  background: #ce00ff;
  border-radius: 0.93rem;
}
.circle img {
  width: 0.83rem;
  height: 0.93rem;
}

@media screen and (min-width: 769px) {
  .sidebar {
    background: blue;
  }
}
</style>