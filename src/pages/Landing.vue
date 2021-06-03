<template>
  <div class="homepage-container" ref="home">
    <div class="">
      <Header />
      <Destacada
        :title="this.destacada.title"
        :overview="this.destacada.overview"
      />
      <Proximamente />
      <Populares />
      <MisPeliculas />
    </div>
  </div>
</template>

<script>
import axios from "axios";
import Header from "../components/Header";
import Destacada from "../components/Destacada";
import Proximamente from "../components/Proximamente";
import Populares from "../components/Populares";
import MisPeliculas from "../components/MisPeliculas";

export default {
  name: "Homepage",
  components: {
    Header,
    Destacada,
    Proximamente,
    Populares,
    MisPeliculas,
  },
  data() {
    return {
      destacada: {
        title: "",
        overview: "",
        backdropPath: "",
        posterPath: "",
      },
    };
  },
  mounted() {
    axios
      .get(
        "https://api.themoviedb.org/3/movie/now_playing?api_key=6f26fd536dd6192ec8a57e94141f8b20"
      )
      .then((response) => {
        // ordeno por fecha
        const orderByDateResults = response.data.results.sort((a, b) => {
          return new Date(b.release_date) - new Date(a.release_date);
        });

        this.destacada.title = orderByDateResults[0].title;
        this.destacada.overview = orderByDateResults[0].overview.substring(
          0,
          250
        );

        this.destacada.posterPath = orderByDateResults[0].poster_path;
        this.destacada.backdropPath = orderByDateResults[0].backdrop_path;

        this.$refs.home.style.backgroundImage = `url(https://image.tmdb.org/t/p/w1280${this.destacada.backdropPath})`;
      });
  },
  created() {
    window.addEventListener("resize", this.changeBackgroundImage);
  },
  methods: {
    changeBackgroundImage(e) {
      if (e.target.innerWidth < 760) {
        this.$refs.home.style.backgroundImage = `url(https://image.tmdb.org/t/p/w1280${this.destacada.posterPath})`;
      }
    },
  },
};
</script>

<style lang="scss" scoped>
.homepage-container {
  background: no-repeat, #000000 no-repeat;
  background-size: 100% 760px;
}
@media screen and (min-width: 760px) {
  .homepage-container {
    background: url("https://image.tmdb.org/t/p/w1280/nz8xWrTKZzA5A7FgxaM4kfAoO1W.jpg")
        no-repeat,
      #000000 no-repeat;
    background-size: 100%;
  }
}
</style>
