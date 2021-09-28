<template>
  <div class="Card">
    <!-- Front Card -->
    <img
      class="poster"
      :src="'https://image.tmdb.org/t/p/w342' + card.poster_path"
      alt=""
    />
    <!-- Back Card -->
    <div class="retro">
      <span><b>Titolo: </b> {{ card.title }}</span>
      <span><b>Titolo originale: </b>{{ card.original_title }}</span>
      <span><b>Voto: </b>{{ card.vote_average }}</span>
      <span>
        Lingua:
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
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
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

.main {
  height: 100%;
  width: 100%;
  padding: 0px 50px;
}
</style>
