<template>
  <div class="container">
    <div class="content">
      <a href="#" target="">
        <div class="content-overlay"></div>
        <img
          class="content-image"
          src="https://image.tmdb.org/t/p/w1280/6ELCZlTA5lGUops70hKdB83WJxH.jpg"
        />
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
            <p class="title"><b>Black Mirror</b></p>
            <p class="desc">
              98% Coincidencia <span class="min-age">+16</span> 1h 30 min
            </p>
            <p class="category">Suspenso</p>
          </div>
          <img src="../../static/arrow-down.svg" alt="" class="arrow-down" />
        </div>
      </a>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
.container {
  padding: 0;
  // float: left;
  // width: 50%;
  // border: 2px solid green;
  margin-right: 23px;
}

// .container .title {
//   color: #1a1a1a;
//   text-align: center;
//   margin-bottom: 10px;
// }

.content {
  // border: 2px solid red;
  position: relative;
  // width: 90%;
  // max-width: 400px;
  //margin: auto;
  overflow: hidden; //! cuidado
  // nuevo
  width: 255px;
  // height: 155px;
}

.content .content-overlay {
  // border: 2px solid blue;
  // background: rgba(0, 0, 0, 0.7); //! difuminado
  box-shadow: 0 -130px 80px -60px black inset;
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
  padding: 0;
}

.content:hover .content-overlay {
  opacity: 1;
}

.content-image {
  width: 100%;
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
  // background-color: blue;
  display: grid;
  grid-template-columns: auto;
  justify-items: center;
  padding: 0 0 0 0;
}
.row-3 {
  // background-color: green;
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
  margin: 10px auto 0 auto;
}

.content:hover .content-details {
  top: 50%;
  // left: 50%;
  opacity: 1;
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
</style>