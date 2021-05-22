<template >
  <div class="jumbotron">
    <h4 class="text-uppercase">Original de <b>liteflix</b></h4>
    <h1>Kids at school</h1>
    <div>
      <DestacadaButton text="Reproducir" icon="../../static/play.svg" />
      <DestacadaButton text="Mi lista" icon="../../static/plus.svg" />
    </div>
    <div class="desc bg-primary">
      <b>Ver temporada 1</b>
      <!-- TODO: fetch de la descripcion -->
      <p>
        Lorem ipsum dolor sit amet consectetur adipisicing elit. At quo
        recusandae repellendus nisi eaque repellat est consequuntur non nesciunt
        eos doloribus officia labore odio dolores nulla quas, incidunt rem
        natus?
      </p>
    </div>
  </div>
</template>

<script>
import DestacadaButton from "../components/DestacadaButton";

export default {
  name: "Destacada",
  components: {
    DestacadaButton,
  },
};
</script>

<style lang="scss" scoped>
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
  font-family: "RobotoSlab";
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
</style>