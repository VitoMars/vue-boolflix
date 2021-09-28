<template>
  <div class="Card">
    <!-- Front Card -->
    <img
      class="poster"
      v-if="card.poster_path != null"
      :src="'https://image.tmdb.org/t/p/w342' + card.poster_path"
      alt=""
    />
    <img class="poster" v-else src="@/assets/no-poster.jpeg" alt="" />
    <!-- Back Card -->
    <div class="retro">
      <span><b>Titolo: </b> {{ card.title }}</span>
      <span><b>Titolo originale: </b>{{ card.original_title }}</span>
      <span
        ><b>Voto: </b>
        <span v-for="n in 5" :key="n">
          <i class="star fa-star" :class="n <= getVote() ? 'fas' : 'far'"></i
        ></span>
      </span>
      <span>
        <b>Lingua: </b>
        <img
          class="flag"
          v-if="flags.includes(card.original_language)"
          :src="require(`../assets/flags/${card.original_language}.png`)"
          alt=""
        />
        <span v-else>{{ card.original_language.toUpperCase() }}</span>
      </span>
    </div>
  </div>
</template>

<script>
export default {
  name: "Card",
  data() {
    return {
      imgUrl: "https://image.tmdb.org/t/p/w342",
      flags: ["it", "en", "fr", "es", "de"],
    };
  },
  props: ["card"],
  methods: {
    getVote() {
      return Math.ceil(this.card.vote_average / 2);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@import "~@fortawesome/fontawesome-free/css/all.min.css";

.flag {
  height: 20px;
  width: 30px;
}

.Card {
  margin: 10px;
  height: 350px;
  width: 230px;
  display: flex;
  background-size: cover;
  background-color: black;
}

.poster {
  height: 350px;
  width: 230px;
}

.retro {
  display: none;
  padding: 0px 10px;
}

.Card:hover .poster {
  display: none;
}

.Card:hover .retro {
  display: flex;
  flex-direction: column;
  justify-content: center;
  flex-wrap: wrap;
}

.star {
  color: #fbcb15;
}

.main {
  height: 100%;
  width: 100%;
  padding: 0px 50px;
}
</style>
