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
    <button class="add-movie-button" id="myBtn" @click="openModal">
      <img src="../../static/plus.svg" alt="" />
      <span>Agregar película</span>
    </button>
    <div id="myModal" ref="myModal" class="modal-container">
      <div class="modal-content">
        <form @submit="postMovie" method="post">
          <div class="close-container">
            <span class="close" @click="closeModal">&times;</span>
          </div>
          <div
            class="add-file"
            ref="addFile1"
            @dragover="onDragOver"
            @dragleave="onDragLeave"
            @drop="onDrop"
            v-show="!showProgressBar"
          >
            <img src="../../static/clip.png" alt="" />
            <input type="file" id="add-file-input" hidden />
            <label for="add-file-input"
              ><span>Agregar archivo</span> o arrastrarlo y soltarlo aquí</label
            >
          </div>

          <div
            class="add-file progress-bar-container"
            ref="addFile2"
            v-show="showProgressBar"
          >
            <span>Cargando {{ parseInt(progresBarWidth) }} %</span>
            <div
              class="progress-bar"
              ref="progressBar"
              style="--width: 10"
            ></div>
            <div class="cancel-button">
              <button @click="cancelar">Cancelar</button>
            </div>
          </div>
          <div class="film-name-category">
            <div class="film-name">
              <span>Nombre de la Pelicula</span>
              <input type="text" name="name" v-model="movie.name" />
            </div>
            <div class="film-category">
              <span>Categoría</span>
              <select name="category" id="" v-model="movie.category">
                <option selected disabled></option>
                <option v-for="index in 50" :key="index">Opcion X</option>
              </select>
            </div>
          </div>
          <button class="upload-film" type="submit">Subir Película</button>
        </form>
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
import axios from "axios";

import UserMenu from "./UserMenu";
export default {
  name: "Navbar",
  components: {
    UserMenu,
  },
  data() {
    return {
      showProgressBar: false,
      progresBarWidth: 0,
      // form data
      movie: {
        name: "",
        category: "",
        image: "",
      },
    };
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
      // this.progresBarWidth = 0;
      const progresBar = this.$refs.progressBar;
      progresBar.style.setProperty("--width", 0);
    },
    onDragOver(e) {
      e.preventDefault();
      this.$refs.addFile1.classList.add("add-file-active");
    },
    onDragLeave() {
      this.$refs.addFile1.classList.remove("add-file-active");
    },
    onDrop(e) {
      e.preventDefault();

      this.$refs.addFile1.classList.remove("add-file-active");

      // si sube varios, me quedo con el primero
      const file = e.dataTransfer.files[0];

      const fileType = file.type;

      let validExtensions = ["image/jpeg", "image/jpg", "image/png"];

      if (validExtensions.includes(fileType)) {
        let fileReader = new FileReader();

        fileReader.onload = () => {
          this.showProgressBar = true;
          this.progresBarWidth = 0;
          this.activateProgressBar();
        };

        fileReader.readAsDataURL(file);
      } else {
        //! NO VALIDO

        console.log("formato no valido");
        this.$refs.addFile1.classList.remove("add-file-active");
      }
    },
    activateProgressBar() {
      const progresBar = this.$refs.progressBar;

      console.log("this.progresBarWidth en activate");
      console.log(this.progresBarWidth);

      let interval = setInterval(() => {
        if (this.progresBarWidth < 100 && this.showProgressBar) {
          // aumento la progress bar
          const computedStyle = getComputedStyle(progresBar);
          this.progresBarWidth =
            parseFloat(computedStyle.getPropertyValue("--width")) || 0;

          progresBar.style.setProperty("--width", this.progresBarWidth + 0.1);
        } else if (!this.progresBarWidth < 100) {
          // corto el interval

          clearInterval(interval);
        }
      }, 5);
    },
    cancelar() {
      // console.log("cancelar");
      // console.log("this.showProgressBar puesto a false");
      this.showProgressBar = false;
      //  progress bar puesta a 0
      //console.log("progress bar with a 0");
      const progresBar = this.$refs.progressBar;
      progresBar.style.setProperty("--width", 0);
    },
    postMovie(e) {
      // console.log(this.movie);
      axios({
        url: "http://localhost:5000/movies",
        method: "post",
        data: this.movie,
      })
        .then((response) => {
          console.log(response);
        })
        .catch((error) => {
          console.log(error);
        });
      e.preventDefault();
      // http://localhost:5000/movies
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
  // padding: 20px;
  border: 2px solid red;
  // width: 80%;
  width: 730px;
  height: 354px;

  form {
    border: 2px solid blue;
  }
}
.close-container {
  // border: 2px solid green;
  height: auto;
  padding: 10px 14px 0 0;
}
.close {
  // border: 2px solid blue;
  // color: #aaaaaa;
  float: right;
  font-size: 17px;
  font-weight: bold;
}
.close:hover,
.close:focus {
  color: #000;
  text-decoration: none;
  cursor: pointer;
}
.add-file {
  width: 660px;
  height: 100px;
  margin: 0 35px 0 35px;
  display: flex;
  justify-content: center;
  align-items: center;
  border: 2px dashed #9b9b9b;
  border-radius: 10px;
}
.add-file label {
  font-size: 16px;
  font-family: "Montserrat";
}
.add-file label span {
  color: #0076ff;
  font-weight: bold;
}
.add-file img {
  width: 20px;
  height: 20px;
  margin-right: 7px;
}
.add-file-active {
  // background: red;
  border: 2px solid #0076ff;
}
.add-file .progress-bar {
  // display: none;
  position: relative;
  width: 100%;
  height: 30px;
  background-color: #f3f3f3;
  // border-radius: 10px;
  // color: green;
  // padding: 0 0 0 12px;
  // border: 2px solid blue;
}
.add-file .progress-bar::before {
  content: attr(data-label);
  position: absolute;
  // left: 0.5em;
  // top: 0.5em;
  // bottom: 0.5em;
  width: calc(var(--width, 0) * 1%);
  min-width: 2rem;
  max-width: calc(100% - 1em);
  background-color: #7ed321;
  border-radius: 10px;
  padding: 10px;
  // border: 2px solid red;
}
.progress-bar-container {
  background-color: #f3f3f3;
  // border: 2px solid green;
  display: block;
  padding: 0 31px 15px 29px;

  span {
    font-family: "Montserrat";
    font-size: 12px;
    font-weight: bold;
  }

  button {
    font-family: "Montserrat";
    font-size: 12px;
    font-weight: bold;
    border: 0;
    background-color: #f3f3f3;
  }
  .cancel-button {
    // background-color: red;
    display: flex;
    justify-content: center;
  }
}
.film-name-category {
  // border: 2px solid red;
  display: grid;
  grid-template-columns: 345px 345px;
  padding: 30px 35px 44px 35px;
}
.film-name,
.film-category {
  // border: 2px solid blue;
  display: grid;
  grid-template-rows: auto auto;
  padding-right: 30px;
}
.film-name span,
.film-category span {
  font-family: "Montserrat";
  font-size: 12px;
  font-weight: 500;
  font-stretch: normal;
  font-style: normal;
  line-height: normal;
  letter-spacing: 5px;
  color: #9b9b9b;
  text-transform: uppercase;
}
.film-name input,
.film-category select {
  border: 0;
  border-bottom: 2px solid #0076ff;
  font-family: "Montserrat";
  font-size: 16px;
  margin-top: 12px;
  color: #000000;
  font-weight: 550;
}
.film-category select {
  -webkit-appearance: none;
  appearance: none;
}
*:focus {
  outline: none;
}
.upload-film {
  // border: 2px solid green;
  border-radius: 35px;
  border: 0;
  width: 350px;
  height: 70px;
  margin: 0 auto 27px auto;
  display: flex;
  align-items: center;
  justify-content: center;
  font-family: "Montserrat";
  font-size: 16px;
  color: white;
  background-color: #dedede;
}
</style>