<template>
  <div class="main">
    <h2>Films</h2>
    <ul class="cards">
      <li v-for="(card, index) in movieCards" :key="index">
        <div class="img">
          <img
            :src="'https://image.tmdb.org/t/p/w342' + card.poster_path"
            alt=""
          />
          <div class="retro">
            <span><b>Titolo: </b> {{ card.title }}</span>
            <span><b>Titolo originale: </b>{{ card.original_title }}</span>
            <span><b>Voto: </b>{{ card.vote_average }}</span>
            <span><b>Overview: </b>{{ card.overview }}</span>
          </div>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "Main",
  props: ["movieCards"],
  data() {
    return {
      imgUrl: "https://image.tmdb.org/t/p/w342",
      hover: false,
    };
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h2 {
  padding: 30px 0px;
}
.img {
  height: 350px;
  width: 230px;
  display: flex;
  background-size: cover;
  background-color: black;
}

img {
  height: 350px;
  width: 230px;
}

.retro {
  display: none;
  padding: 0px 10px;
}

.img:hover img {
  display: none;
}

.img:hover .retro {
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.main {
  height: 100%;
  width: 100%;
  padding: 0px 50px;
}
.cards {
  display: flex;
  flex-wrap: wrap;
}
li {
  margin: 10px;
}
ul {
  list-style-type: none;
  padding: 0;
  margin: 0;
}
a {
  color: #42b983;
}
</style>
