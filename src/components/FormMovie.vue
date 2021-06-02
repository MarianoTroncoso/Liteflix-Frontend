<template>
  <div>
    <!-- action-->
    <!-- <form @submit="postMovie" method="POST" enctype="multipart/form-data"> -->
    <form enctype="multipart/form-data" action="">
      <!----------------------------- SUBIR ARCHIVO: showAddFile ----------------------------->
      <div
        class="add-file"
        ref="addFile1"
        @dragover="onDragOver"
        @dragleave="onDragLeave"
        @drop="onDrop"
        v-show="showAddFile"
      >
        <img src="../../static/clip.png" alt="" />
        <input
          type="file"
          id="file"
          name="file"
          ref="file"
          hidden
          @change="actualizarImagen"
        />
        <label for="file"
          ><span>Agregar archivo</span> o arrastrarlo y soltarlo aquí</label
        >
      </div>

      <!----------------------------- PROGRESS BAR: showProgressBar ----------------------------->
      <div
        class="add-file progress-bar-container"
        ref="addFile2"
        v-show="showProgressBar"
      >
        <span>Cargando {{ parseInt(progresBarWidth) }} %</span>
        <div class="progress-bar" ref="progressBar" style="--width: 0"></div>
        <div class="cancel-button">
          <button @click="cancelar">Cancelar</button>
        </div>
      </div>

      <!----------------------------- ERROR: showError ----------------------------->
      <div
        class="add-file progress-bar-container-error"
        ref=""
        v-show="showError"
      >
        <span><b>Error!</b> No se pudo cargar la película</span>
        <div class="progress-bar-error" style=""></div>
        <div class="tryagain-button">
          <button @click="reintentar">Reintentar</button>
        </div>
      </div>

      <!----------------------------- FILM Y CATEGORIA ----------------------------->
      <div class="film-name-category">
        <div class="film-name">
          <span>Nombre de la Pelicula</span>
          <input
            type="text"
            name="name"
            v-model="movie.name"
            @change="checkMovieName"
          />
        </div>
        <div class="film-category">
          <span>Categoría</span>
          <!-- <select
            name="category"
            id=""
            v-model="movie.category"
            class="select-category"
          >
            <option selected disabled></option>

            <option
              :value="category"
              v-for="(category, index) in categories"
              :key="index"
            >
              {{ category }}
            </option>
          </select> -->
          <form
            action=""
            style="
              display: flex;
              align-items: center;
              border-bottom: 2px solid #0076ff;
            "
          >
            <div class="selectbox">
              <div class="select" ref="select" @click="activateSelect">
                <div class="contenido-select">
                  <p class="cateory-title" ref="cateoryTitle">
                    Seleccionar categoría
                  </p>
                </div>
              </div>
              <!-- opciones -->
              <!--  <div |tions" ref="options">
                <a
                  href="#"
                  class="option"
                  v-for="(category, index) in categories"
                  :key="index"
                  @click="actualizarCategoria"
                >
                  <div class="contenido-option">{{ category }}</div>
                </a>
              </div> -->
              <div class="options-container" ref="optionsContainer">
                <div class="options">
                  <ul>
                    <li
                      class="option"
                      @click="actualizarCategoria"
                      v-for="(category, index) in categories"
                      :key="index"
                    >
                      {{ category }}
                    </li>
                  </ul>
                </div>
              </div>
            </div>
            <input
              type="hidden"
              name="category"
              id=""
              ref="inputSelect"
              :value="this.movie.category"
            />
          </form>
        </div>
      </div>
      <button
        class="upload-film"
        :class="{ enable: this.enableUploadMovieButton }"
        :disabled="!this.enableUploadMovieButton"
        type="submit"
        @click="postMovie"
      >
        <!-- :disabled="!this.enableUploadMovieButton" -->
        Subir Película
      </button>
    </form>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "FormMovie",
  components: {},
  data() {
    return {
      showAddFile: true, // por defecto mostrar "Agregar archivo..."
      showProgressBar: false, // barra cargando sin error
      showError: false,
      progresBarWidth: 0,
      // enable button
      validMovieName: false,
      validMovieCategory: false,
      validMovieImage: false,
      // enableUploadMovieButton: validMovieName,

      // form data
      movie: {
        name: "",
        category: "",
        image: "",
      },
      categories: [
        "Acción",
        "Animación",
        "Aventuras",
        "Ciencia Ficción",
        "Comedia",
        "Documentales",
        "Drama",
        "Amor",
      ],
    };
  },
  computed: {
    enableUploadMovieButton() {
      return (
        this.validMovieName && this.validMovieCategory && this.validMovieImage
      );
    },
  },
  methods: {
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

      const file = e.dataTransfer.files[0];

      this.checkFormat(file);
    },
    actualizarImagen(e) {
      e.preventDefault();

      this.movie.image = this.$refs.file.files[0];

      this.checkFormat(this.movie.image);
    },
    checkFormat(file) {
      console.log("check format");
      console.log(file);

      const fileType = file.type;

      let validExtensions = ["image/jpeg", "image/jpg", "image/png"];

      if (validExtensions.includes(fileType)) {
        this.validMovieImage = true;

        console.log("this.enableUploadMovieButton");
        console.log(this.enableUploadMovieButton);

        let fileReader = new FileReader();

        fileReader.onload = () => {
          this.showProgressBar = true;
          this.showAddFile = false;
          this.progresBarWidth = 0;
          this.activateProgressBar();
        };

        fileReader.readAsDataURL(file);
      } else {
        //! NO VALIDO
        this.$refs.addFile1.classList.remove("add-file-active");
        this.showAddFile = false;
        this.showError = true;
      }
    },
    activateProgressBar() {
      const progresBar = this.$refs.progressBar;

      let interval = setInterval(() => {
        if (this.progresBarWidth < 100 && this.showProgressBar) {
          // aumento la progress bar
          const computedStyle = getComputedStyle(progresBar);
          this.progresBarWidth =
            parseFloat(computedStyle.getPropertyValue("--width")) || 0;
          progresBar.style.setProperty("--width", this.progresBarWidth + 1); //! 0.1
        } else if (!this.progresBarWidth < 100) {
          clearInterval(interval);
        }
      }, 5);
    },
    cancelar(e) {
      e.preventDefault();
      this.showProgressBar = false;
      this.showAddFile = true;

      const progresBar = this.$refs.progressBar;
      progresBar.style.setProperty("--width", 0);
    },
    reintentar(e) {
      e.preventDefault();
      this.showError = false;
      this.showAddFile = true;
    },
    postMovie(e) {
      console.log("post movie");
      let formData = new FormData();
      formData.append("file", this.movie.image);
      formData.append("name", this.movie.name);
      formData.append("category", this.movie.category);

      axios
        .post("http://localhost:5000/movies", formData, {
          headers: {
            "Content-Type": "multipart/form-data",
          },
        })
        .then(function () {
          console.log("todo bien :D");
        })
        .catch(function () {
          console.log("todo mal D:");
        });
    },
    activateSelect() {
      const select = this.$refs.select;
      select.classList.toggle("active");

      const optionsContainer = this.$refs.optionsContainer;
      optionsContainer.classList.toggle("active");

      // const options = this.$refs.options;
      // options.classList.toggle("active");
    },
    actualizarCategoria(e) {
      e.preventDefault();

      this.movie.category = e.currentTarget.innerText;

      if (typeof this.movie.category === "string") {
        this.validMovieCategory = true;

        console.log("this.validMovieImage");
        console.log(this.validMovieImage);
      }

      // actualizar arriba
      const cateoryTitle = this.$refs.cateoryTitle;
      cateoryTitle.innerHTML = e.currentTarget.innerText;

      // cierro
      const optionsContainer = this.$refs.optionsContainer;
      optionsContainer.classList.toggle("active");
    },
    checkMovieName(e) {
      if (typeof e.target.value === "string") {
        this.validMovieName = true;
        console.log("this.enableUploadMovieButton");
        console.log(this.enableUploadMovieButton);
      }
    },
    checkMovieCategory(e) {
      console.log("checkMovieCategory");
    },
  },
};
</script>

<style lang="scss" scoped>
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
.add-file {
  .progress-bar::before {
    content: attr(data-label);
    position: absolute;
    // left: 0.5em;
    // top: 0.5em;
    // bottom: 0.5em;
    width: calc(var(--width, 0) * 1%);
    min-width: 2rem;
    max-width: calc(100%); //- 1em
    background-color: #7ed321;
    border-radius: 10px;
    padding: 10px;
    // border: 2px solid red;
  }
  .progress-bar-error::before {
    content: attr(data-label);
    position: absolute;
    // left: 0.5em;
    // top: 0.5em;
    // bottom: 0.5em;
    width: 82%;
    // min-width: 2rem;
    // max-width: calc(100%);
    background-color: red;
    border-radius: 10px;
    padding: 10px;
    // border: 2px solid red;
    margin-top: 5px;
  }
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
.progress-bar-container-error {
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
    text-transform: uppercase;
  }
  .tryagain-button {
    // background-color: red;
    display: flex;
    justify-content: center;
    // margin: 20px;
    padding: 33px 0 0 0;
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

  select:focus {
    // border: 2px solid blue;
    // background-color: lightgrey;

    // border-radius: 10px;
    // color: white;
  }
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
.cateory-title {
  font-weight: bold;
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
.enable {
  background-color: black;
}
// --------------------------------------- SELECT ---------------------------------
.selectbox {
  // border: 2px solid green;
  // padding: 0 15px 0 0;

  margin: 0;
  box-sizing: border-box;
  position: relative;
  p {
    margin: 0;
  }
  a {
    text-decoration: none;
    // color: black;
  }
  // scroll bar
  ::-webkit-scrollbar {
    width: 11px;
  }
  ::-webkit-scrollbar-track {
    background: #f3f3f3;
    border-radius: 5.5px;
  }
  ::-webkit-scrollbar-thumb {
    background: #9b9b9b;
    border-radius: 5.5px;
  }
  ::-webkit-scrollbar-thumb:hover {
    background: gray;
  }
}
.select {
  // border: 2px solid blue;
  cursor: pointer;
  display: flex;
  align-items: center;
  transition: 0.2s ease all;
  // position relative
  z-index: 200; //!CAMBIAR
  font-family: "Montserrat";
  font-size: 16px;
}
.select.active,
.select:hover {
  // border: 2px solid red;
}
.options-container {
  background-color: white;
  padding: 20px 30px 25px 0;
  border-radius: 10px;
  box-shadow: 0 0 30px 0 rgba(0, 0, 0, 0.1);
  display: none;
}
.options {
  // border: 2px solid orange;
  // box-shadow: 0 0 30px 0 rgba(0, 0, 0, 0.1);
  background-color: white;
  border-radius: 10px;
  z-index: 100; //!CAMBIAR
  // display: none;
  width: 300px;
  height: 230px;
  padding: 0px 30px 0 20px;
  overflow-y: scroll;
  // margin: 10px 0 0 0;

  ul {
    list-style-type: none;
    padding: 0;
    li {
      cursor: pointer;
      color: #9b9b9b;
      font-family: "Montserrat";
      font-size: 16px;
      line-height: 2.5;
      border-bottom: 1px solid #cccccc;
    }
    li:hover {
      color: black;
      font-weight: bold;
    }
  }
}
.options-container.active {
  display: block;
}
</style>