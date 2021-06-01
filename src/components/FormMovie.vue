<template>
  <div>
    <form @submit="postMovie" method="post" enctype="multipart/form-data">
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
          id="add-file-input"
          hidden
          @change="onFileSelected"
        />
        <label for="add-file-input"
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
          <input type="text" name="name" v-model="movie.name" />
        </div>
        <div class="film-category">
          <span>Categoría</span>
          <select name="category" id="" v-model="movie.category">
            <option selected disabled></option>
            <!-- <option v-for="index in 50" :key="index">Opcion X</option> -->
            <option
              value=""
              v-for="(category, index) in categories"
              :key="index"
            >
              {{ category }}
            </option>
          </select>
        </div>
      </div>
      <button class="upload-film" type="submit">Subir Película</button>
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

      const fileType = file.type;

      let validExtensions = ["image/jpeg", "image/jpg", "image/png"];

      if (validExtensions.includes(fileType)) {
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

        // console.log("formato no valido");
        this.$refs.addFile1.classList.remove("add-file-active");

        // this.showAddFile = true; // mostrar de nuevo para subir archivo
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
          progresBar.style.setProperty("--width", this.progresBarWidth + 0.1);
        } else if (!this.progresBarWidth < 100) {
          clearInterval(interval);
        }
      }, 5);
    },
    cancelar() {
      this.showProgressBar = false;
      this.showAddFile = true;

      const progresBar = this.$refs.progressBar;
      progresBar.style.setProperty("--width", 0);
    },
    reintentar() {
      this.showError = false;
      this.showAddFile = true;
    },
    postMovie(e) {
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
    onFileSelected(e) {
      // console.log(e.target.files[0]);
      this.movie.image = e.target.files[0];
      console.log(this.movie.image);
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