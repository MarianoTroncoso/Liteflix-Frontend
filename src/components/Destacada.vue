<template >
  <!--MOBILE-->
  <div class="destacada-wrapper">
    <div
      class="destacada-wrapper-mobile animate__animated animate__fadeInLeftBig"
    >
      <h4>Original de <b>Liteflix</b></h4>
      <h1>{{ title }}</h1>
      <div class="buttons-mobile">
        <DestacadaButton text="Reproducir" icon="../../static/play.svg" />
        <a href="#" class="plus-circle"
          ><img src="../../static/plus-circle.svg" alt=""
        /></a>
      </div>
    </div>

    <div
      class="destacada-wrapper-desktop animate__animated animate__fadeInLeft"
    >
      <!--  bg-secondary -->
      <h4>Original de <b>Liteflix</b></h4>
      <!-- <h1>{{ title }}</h1> -->

      <h1>{{ title }}</h1>

      <div class="buttons-desktop">
        <DestacadaButton text="Reproducir" icon="../../static/play.svg" />
        <DestacadaButton text="Mi lista" icon="../../static/plus.svg" />
      </div>
      <div class="descripcion">
        <p><b>Ver temporada 1</b></p>
        <p>{{ overview }}...</p>
      </div>
    </div>
  </div>
</template>

<script>
import DestacadaButton from "../components/DestacadaButton";

export default {
  name: "Destacada",
  data() {
    return {
      destacada: {
        title: "",
        overview: "",
      },
    };
  },
  props: {
    title: {
      type: String,
    },
    overview: {
      type: String,
    },
  },
  components: {
    DestacadaButton,
  },
  methods: {},
};
</script>

<style lang="scss" scoped>
// MOBILE
.destacada-wrapper-mobile {
  // background-color: gray;
  text-align: center;
  color: white;
  padding: 178.5px 0 0 0;
}
.destacada-wrapper-mobile h4 {
  text-transform: uppercase;
  font-family: "Montserrat";
  font-size: 18px;
}
.destacada-wrapper-mobile h1 {
  font-size: 72px;
  font-family: "Roboto Slab", serif;
  font-weight: bold;
  font-stretch: normal;
  font-style: normal;
  line-height: 1;
  letter-spacing: normal;
  text-align: center;
}
.destacada-wrapper-desktop {
  display: none;
  // width: 33.5625rem;
  width: 80%;
  color: white;
  // padding: 82px 0 0 164px;
  padding: 90px 0 0 0;
  margin: 0 auto 0 auto;
  // border: 2px solid red;
}
.destacada-wrapper-desktop h4 {
  font-family: "Montserrat";
  font-size: 24px;
  text-transform: uppercase;
}
.destacada-wrapper-desktop h1 {
  font-size: 110px;
  font-family: "Roboto Slab", serif;
  font-weight: bold;
  font-stretch: normal;
  font-style: normal;
  line-height: 0.82;
  letter-spacing: normal;
  margin-top: 18px;
}
.buttons-mobile {
  display: flex;
  justify-content: center;
  position: relative;
}
.plus-circle {
  position: absolute;
  right: 0;
  margin-right: 15px;
}
.buttons-desktop {
  width: 350px;
  display: flex;
  justify-content: space-between;
  padding-top: 19px;
}
.descripcion {
  padding-top: 25px;
  // border: 2px solid red;
  width: 45%;
}
.descripcion p {
  margin-bottom: 0;
  font-family: "Montserrat";
  font-size: 18px;
}
.descripcion p:nth-child(2) {
  height: 168px;
  overflow: hidden;
  // border: 2px solid blue;
}
@media screen and (min-width: 760px) {
  .destacada-wrapper-desktop {
    display: block;
  }
  .destacada-wrapper-mobile {
    display: none;
  }
}
</style>