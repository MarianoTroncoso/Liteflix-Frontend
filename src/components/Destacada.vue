<template >
  <!--MOBILE-->
  <div class="destacada-wrapper">
    <div class="destacada-wrapper-mobile">
      <h4>Original de <b>Liteflix</b></h4>
      <h1>{{ title }}</h1>
      <div class="buttons-mobile">
        <DestacadaButton text="Reproducir" icon="../../static/play.svg" />
        <a href="#" class="plus-circle"
          ><img src="../../static/plus-circle.svg" alt=""
        /></a>
      </div>
    </div>
    <div class="destacada-wrapper-desktop">
      <!--  bg-secondary -->
      <h4>Original de <b>Liteflix</b></h4>
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

  <!-- DESKTOP
    <div class="jumbotron">
    <h4 class="text-uppercase">Original de <b>liteflix</b></h4>
    <h1>Kids at school</h1>
    <div>
      <DestacadaButton text="Reproducir" icon="../../static/play.svg" />
      <DestacadaButton text="Mi lista" icon="../../static/plus.svg" />
    </div>
    <div class="desc">
      <b>Ver temporada 1</b>
      <p>
        Lorem ipsum dolor sit amet consectetur adipisicing elit. At quo
        recusandae repellendus nisi eaque repellat est consequuntur non nesciunt
        eos doloribus officia labore odio dolores nulla quas, incidunt rem
        natus?
      </p>
    </div>
  </div> 
  -->
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
// DESKTOP
/*
.jumbotron {
  color: white;
  font-family: "Montserrat";
  margin-top: 109px;
  width: 537px; // !cuidado
}

.jumbotron h4 {
  font-size: 24px;
}

.jumbotron h1 {
  font-size: 110px;
  font-family: "Roboto Slab", serif;
  font-weight: bold;
  font-stretch: normal;
  font-style: normal;
  line-height: 0.82;
  letter-spacing: normal;
  margin: 18px 0 19px 0;
}

.desc {
  font-family: "Montserrat";
  font-size: 18px;
  font-weight: normal;
  font-stretch: normal;
  font-style: normal;
  line-height: normal;
  letter-spacing: normal;
  color: white;
  margin: 25px 0 0 0; //!cuidado, mr es 574
  height: 168px;
}
*/
</style>