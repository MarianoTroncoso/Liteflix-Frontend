<template>
  <div class="navbar-wrapper">
    <a id="logo-brand" href="#"
      ><img src="../../static/liteflix.svg" alt=""
    /></a>
    <ul class="ul-left">
      <li><a href="#">Inicio</a></li>
      <li><a href="#">Series</a></li>
      <li><a href="#">Peliculas</a></li>
      <li><a href="#">Agregados recientemente</a></li>
      <li><a href="#">Mi lista</a></li>
    </ul>
    <button class="add-movie-button" id="myBtn" @click="openModal">
      <img src="../../static/plus.svg" alt="" />
      <span>Agregar película</span>
    </button>
    <div id="myModal" ref="myModal" class="modal-container">
      <div class="modal-content">
        <div class="close-container">
          <span class="close" @click="closeModal">&times;</span>
        </div>
        <!-- FORM MOVIE -->
        <FormMovie />
      </div>
    </div>

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
            <UserMenu class="menu" ref="menu" />
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
import UserMenu from "./UserMenu";
import FormMovie from "./FormMovie";
export default {
  name: "Navbar",
  components: {
    UserMenu,
    FormMovie,
  },
  data() {
    return {};
  },
  methods: {
    openModal() {
      const modal = this.$refs.myModal;
      modal.style.display = "block";
    },
    closeModal() {
      const modal = this.$refs.myModal;
      modal.style.display = "none";
      this.showProgressBar = false; // agregado 1
      this.showAddFile = true;
      // this.progresBarWidth = 0;

      // const progresBar = this.$refs.progressBar;
      // progresBar.style.setProperty("--width", 0);
    },
  },
};
</script>

<style lang="scss" scoped>
.navbar-wrapper {
  // padding: 20px 165px 0 165px;
  display: flex;
  // border: 2px solid red;
  // width: 1300px;
  width: 80%;
  margin: 0 auto 0 auto;
  padding: 20px 0 0 0;
}
.ul-left {
  // border: 2px solid blue;
  padding: 5px 0 0 0;
}
#logo-brand {
  margin-right: 20px;
}
// ul {
//   padding: 2px 0 0 0;
// }
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
.add-movie-button:hover span {
  max-width: 7rem;
  margin: 0 17px 0 0;
}
.add-movie-button {
  background-color: red;
  // border: 2px solid green;
  border: 0;
  border-radius: 20px;
  display: flex;
  align-items: center;
  padding: 0;
  height: 40px;
  margin: 0 0 10px 0;
  img {
    margin: 0 12px 0 12px;
  }
  span {
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
}
.right-items {
  // border: 2px solid green;
  margin-left: auto;
  display: flex;
  align-items: center;
  flex-wrap: wrap;
  position: relative;
  width: auto;
  padding-bottom: 8px;
  ul {
    // border: 2px solid yellow;
    margin: 0;
  }
  li {
    // border: 2px solid black;
    margin-left: 20px;
    margin-right: 0;
  }
  li:first-child {
    margin-left: 0px;
  }
  li:last-child {
    margin-left: 0px;
  }
}
.right-items > ul {
  display: inline-flex;
}
.bell {
  background-image: url("../../static/bell.svg");
  background-repeat: no-repeat;
  padding-right: 0;
  margin-bottom: 2px;
  span {
    width: 6px;
    height: 6px;
    position: absolute;
    top: 2px;
    bottom: 8px;
    left: 8px;
  }
}
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
  img {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    object-fit: cover;
  }
}
// ----------------------------------- modal ---------------------------------------
.modal-container {
  display: none;
  position: fixed;
  z-index: 1;
  // padding-top: 100px;
  padding: 200px 0 0 0;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  overflow: auto;
  background-color: rgb(0, 0, 0);
  background-color: rgba(0, 0, 0, 0.8);
}
.modal-content {
  background-color: #fefefe;
  margin: auto;
  // padding: 20px 0 0 0;
  // padding: 20px;
  // border: 2px solid red;
  // width: 80%;
  width: 730px;
  height: 354px;

  form {
    // border: 2px solid blue;
    // padding-top: 10px;
  }
}
.close-container {
  // border: 2px solid green;
  height: auto;
  // padding: 10px 14px 0 0;
  padding: 5px 14px 5px 0;
}
.close {
  // border: 2px solid blue;
  // color: #aaaaaa;
  float: right;
  font-size: 20px;
  font-weight: bold;
}
.close:hover,
.close:focus {
  color: #000;
  text-decoration: none;
  cursor: pointer;
}
</style>