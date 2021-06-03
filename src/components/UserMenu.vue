<template>
  <div class="menu-container">
    <ul class="ul-perfiles">
      <li>
        <button class="selected-user-button">
          <div class="selected-user-image">
            <img src="../../static/fill-1.svg" alt="" />
          </div>
          <span>Ernesto G…</span>
        </button>
      </li>
      <li>
        <button class="not-selected-user-button">
          <div class="not-selected-user-image">
            <img src="../../static/fill-2.svg" alt="" />
          </div>
          <span>User 03</span>
        </button>
      </li>
      <li>
        <button class="not-selected-user-button">
          <div class="not-selected-user-image">
            <img src="../../static/fill-2.svg" alt="" />
          </div>
          <span>User 04</span>
        </button>
      </li>
    </ul>

    <ul class="ul-settings">
      <li>
        <a href="#">Configuración</a>
      </li>
      <li>
        <a href="#">Ayuda</a>
      </li>
      <li>
        <a href="#"><b>Log out</b></a>
      </li>
    </ul>
  </div>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
ul {
  padding: 0 0 0 10px;
}
a {
  text-decoration: none;
}
.menu-container {
  position: absolute;
  top: 20px;
  right: -8px;
  padding: 11px 9px 4px 0px;
  background-color: #fff;
  width: 100%;
  box-sizing: 0 5px 25px rgba(0, 0, 0, 0.1);
  border-radius: 5px;
  transition: 0.3s;
  visibility: hidden;
  opacity: 0;
}

.menu-container::before {
  content: "";
  position: absolute;
  top: -5px;
  right: 28px;
  width: 20px;
  height: 20px;
  background-color: #fff;
  transform: rotate(45deg);
  border-radius: 4px;
}

.menu-container ul li {
  margin: 0;
  list-style: none;

  display: flex;
  align-items: center;
  justify-content: center;
}
.menu-container ul li img {
  transition: 0.5s;
}

.menu-container ul li a {
  display: inline-block;
  color: #555;
  font-size: 12px;
  font-weight: 500;
  transition: 0.5s;
}

.ul-perfiles li {
  padding-top: 5px;
}
.ul-perfiles button {
  width: 111px;
  height: 37px;
  padding: 6px 6px 6px 7px;
  border: 0;
  border-radius: 18.5px;
  background-color: white;
  display: flex;
  align-items: center;
  position: relative;
}

.selected-user-image {
  background-color: #ce00ff;
  width: 25px;
  height: 25px;
  border-radius: 15px;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 0 0 0 2px;
}
.selected-user-button {
  box-shadow: 0 0 10px 0 rgba(0, 0, 0, 0.1);
}
.not-selected-user-button {
  color: #9b9b9b;
}
.not-selected-user-image {
  background-color: #9b9b9b;
  width: 25px;
  height: 25px;
  border-radius: 15px;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 0 0 0 2px;
}
.ul-perfiles span {
  font-family: "Montserrat";
  font-size: 12px;
  margin-left: 5px;
}
.ul-settings {
}
.ul-settings li {
  display: flex !important;
  justify-content: left !important;
  padding: 7px 0 7px 0;
  border-bottom: 1px solid rgba(0, 0, 0, 0.1);
}
.ul-settings li:last-child {
  border-bottom: 0;
}
</style>