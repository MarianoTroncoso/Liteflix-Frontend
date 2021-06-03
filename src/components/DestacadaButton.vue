<template>
  <span class="boton">
    <img :src="icon" alt="" /> <a href="#">{{ text }}</a>
  </span>
</template>

<script>
export default {
  name: "DestacadaButton",
  props: {
    text: {
      type: String,
    },
    icon: {
      type: String,
    },
  },
};
</script>

<style lang="scss" scoped>
.boton {
  width: 160px;
  height: 40px;
  border-radius: 20px;
  background-color: rgba(#000000, 0.5);
  display: flex;
  align-items: center;
  padding: 10px 39px 11px 12px;
}
.boton a {
  text-decoration: none;
  font-family: "Montserrat";
  font-size: 16px;
  font-weight: normal;
  font-stretch: normal;
  font-style: normal;
  line-height: normal;
  letter-spacing: normal;
  color: white;
  margin-left: 6px;
}
</style>