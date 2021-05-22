<template>
  <button type="button">
    <img :src="icon" alt="" />
    {{ text }}
  </button>
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
button {
  width: 160px;
  height: 40px;
  opacity: 0.5;
  border-radius: 20px;
  background-color: #000000;
  font-family: Montserrat;
  font-size: 16px;
  border: 0px;
  // font-weight: normal;
  // font-stretch: normal;
  // font-style: normal;
  // line-height: normal;
  // letter-spacing: normal;
  color: white;
  text-align: left;
}

button img {
  padding: 11px 0px 11px 12px;
}
</style>