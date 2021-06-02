<template>
  <div class="container">
    <div class="content">
      <a href="#" target="">
        <div class="content-overlay"></div>
        <img class="content-image" :src="image" />
        <div class="content-details fadeIn-bottom grid-container">
          <div class="hover-content">
            <div class="row-1">
              <a href="#"><img src="../../static/play-2.svg" alt="" /></a>
            </div>
            <div class="row-2">
              <div class="movie-info">
                <p class="title">
                  <b>{{ title }}</b>
                </p>
                <p class="desc">
                  98% Coincidencia <span class="min-age">+16</span> 1h 30 min
                </p>
                <p class="category">Suspenso</p>
              </div>
              <a href="#" class="like-a">
                <img src="../../static/like.png" alt="" />
              </a>
            </div>
            <img src="../../static/arrow-down.svg" alt="" class="arrow-down" />
          </div>
        </div>
      </a>
    </div>
  </div>
</template>

<script>
export default {
  name: "ImagenPopulares",
  props: {
    title: {
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
  // float: left;
  // width: 50%;

  margin-right: 23px;
}

.content {
  position: relative;
  // width: 90%;
  // max-width: 400px;
  //margin: auto;
  overflow: hidden; //! cuidado
  // nuevo
  width: 100%;
  min-width: 255px;
  // height: 100%;
  // border: 2px solid blue;
}

.content .content-overlay {
  // background: rgba(0, 0, 0, 0.7); //! difuminado
  box-shadow: 0 -150px 80px -60px black inset;
  position: absolute;
  height: 100%; //! estaba en 99%
  width: 100%;
  // left: 0;
  // top: 0;
  // bottom: 0;
  // right: 0;
  opacity: 0;
  -webkit-transition: all 0.4s ease-in-out 0s;
  -moz-transition: all 0.4s ease-in-out 0s;
  transition: all 0.4s ease-in-out 0s;
}

.content:hover .content-overlay {
  opacity: 1;
}

.content-image {
  width: 100%;
  height: 507px;
  // margin-right: 31.4px;
}

.content-details {
  position: absolute;
  // text-align: center;
  // padding-left: 1em;
  // padding-right: 1em;
  width: 100%;
  // top: 50%;
  left: 50%;
  opacity: 0;
  -webkit-transform: translate(-50%, -50%);
  -moz-transform: translate(-50%, -50%);
  transform: translate(-50%, -50%);
  -webkit-transition: all 0.3s ease-in-out 0s;
  -moz-transition: all 0.3s ease-in-out 0s;
  transition: all 0.3s ease-in-out 0s;
  padding: 336px 0 0 0;
}

.grid-container {
  // border: 1px solid green;
  display: grid;
  grid-template-columns: auto;
  grid-template-rows: auto auto auto;
  margin: 0;
  height: 100%;
  font-family: "Montserrat";
  font-size: 12px;
}

.hover-content {
  display: grid;
  color: white;

  p {
    margin: 0;
  }
}
.content:hover .content-details {
  top: 50%;
  // left: 50%;
  opacity: 1;
}
.row-1 {
  // border: 2px solid green;
  padding: 0 0 0 12px;
}
.row-2 {
  // border: 2px solid blue;
  display: grid;
  grid-template-columns: 50% 50%;

  .movie-info {
    // background-color: red;
    font-family: "Montserrat";
    font-size: 12px;
    padding: 0 0 0 12px;
    .title {
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
  }
  .like-a {
    width: 32px;
    height: 32px;
    border: 1.5px solid white;
    border-radius: 17px;
    display: flex;
    align-items: center;
    justify-content: center;
    // margin-left: 50px;
    margin: 3px 0 0 50px;

    img {
      width: 20px;
      height: 18px;
      margin-bottom: 4px;
    }

    // display: flex;
    // align-items: center;
    // justify-content: center;
  }
}
.content-details p {
  // color: #fff;
  // font-size: 0.8em;
}

.fadeIn-bottom {
  top: 80%;
}

// .fadeIn-top {
//   top: 20%;
// }

// .fadeIn-left {
//   left: 20%;
// }

// .fadeIn-right {
//   left: 80%;
// }
.arrow-down {
  display: none;
  border: 2px solid green;
  margin-top: 80px;
  position: absolute;
  z-index: 3;
  bottom: 0;
}
</style>