<template>
  <div class="container">
    <div class="content">
      <a href="#" target="">
        <div class="content-overlay"></div>
        <img class="content-image" :src="image" />
        <div class="content-details fadeIn-bottom grid-container">
          <div class="row-1">
            <a href="#">
              <img
                src="../../static/add-list.svg"
                alt=""
                class="add-list-img"
              />
            </a>
            <a href="#" class="like-a">
              <img src="../../static/like.png" alt="" />
            </a>
          </div>
          <div class="row-2">
            <a href="#"><img src="../../static/play-2.svg" alt="" /></a>
          </div>
          <div class="row-3">
            <p class="title">
              <b>{{ title }}</b>
            </p>
            <p class="desc">
              98% Coincidencia <span class="min-age">+16</span> 1h 30 min
            </p>
            <p class="category">{{ category }}</p>
          </div>
          <img src="../../static/arrow-down.svg" alt="" class="arrow-down" />
        </div>
      </a>
    </div>
  </div>
</template>

<script>
export default {
  name: "ImagenMisPeliculas",
  props: {
    title: {
      type: String,
    },
    category: {
      type: String,
    },
    image: {
      type: String,
    },
  },
};
</script>

<style lang="scss" scoped>
.container {
  padding: 0;

  margin-right: 23px;
}

.content {
  position: relative;
  overflow: hidden; //! cuidado
  width: 100%;
  min-width: 255px;
  max-width: 400px;
  height: 100%;
  max-height: 200px;
}

.content .content-overlay {
  box-shadow: 0 -130px 80px -60px black inset;
  position: absolute;
  height: 100%; //! estaba en 99%
  width: 100%;
  opacity: 0;
  -webkit-transition: all 0.4s ease-in-out 0s;
  -moz-transition: all 0.4s ease-in-out 0s;
  transition: all 0.4s ease-in-out 0s;
  padding: 0;
}

.content:hover .content-overlay {
  opacity: 1;
}

.content-image {
  width: 100%;
  height: 100%;
}

.content-details {
  position: absolute;
  width: 100%;
  left: 50%;
  opacity: 0;
  -webkit-transform: translate(-50%, -50%);
  -moz-transform: translate(-50%, -50%);
  transform: translate(-50%, -50%);
  -webkit-transition: all 0.3s ease-in-out 0s;
  -moz-transition: all 0.3s ease-in-out 0s;
  transition: all 0.3s ease-in-out 0s;
}

.grid-container {
  display: grid;
  grid-template-columns: auto;
  grid-template-rows: auto auto auto;
  margin: 0;
  height: 100%;
  font-family: "Montserrat";
  font-size: 12px;
}

.row-1 {
  display: grid;
  grid-template-columns: auto auto;
  justify-content: end;
  align-content: center;
  padding: 8px 8px 0 0;
}

.add-list-img {
  width: 32px;
  height: 32px;
}

.like-a {
  width: 32px;
  height: 32px;
  border: 1.5px solid white;
  border-radius: 17px;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-left: 10px;
  padding: 15px;
}

.like-a img {
  width: 20px;
  height: 18px;
  margin-bottom: 4px;
}

.row-2 {
  display: grid;
  grid-template-columns: auto;
  justify-items: center;
  padding: 0 0 0 0;
}
.row-3 {
  color: white;
  padding: 0 0 10px 10px;
}
.row-3 p {
  margin: 0;
  font-size: 12px;
}
.row-3 .title {
  font-size: 15px;
}
.min-age {
  width: 35px;
  height: 16px;
  border-radius: 9.5px;
  background-color: gray;
  padding: 0 2px 0 2px;
  font-family: "Montserrat";
  padding: 0 8px 0 8px;
}

.arrow-down {
  display: none;
  margin: 10px auto 0 auto;
}

.content:hover .content-details {
  top: 50%;
  opacity: 1;
}

.fadeIn-bottom {
  top: 80%;
}
</style>