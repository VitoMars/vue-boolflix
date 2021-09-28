<template>
  <div class="carta">
    <div class="img">
      <img
        class="poster"
        :src="'https://image.tmdb.org/t/p/w342' + card.poster_path"
        alt=""
      />
      <div class="retro">
        <span><b>Titolo: </b> {{ card.title }}</span>
        <span><b>Titolo originale: </b>{{ card.original_title }}</span>
        <span><b>Voto: </b>{{ card.vote_average }}</span>
        <span><b>Overview: </b></span>
      </div>
    </div>
    <!-- <img
      class="flag"
      v-if="flags.includes(item.original_language)"
      :src="require(`../assets/flags/${item.original_language}.png`)"
      alt=""
    />
    <p v-else>{{ item.original_language }}</p> -->
  </div>
</template>

<script>
export default {
  name: "Card",
  data() {
    return {
      // flags: ["it", "en", "fr", "es", "de"],
      imgUrl: "https://image.tmdb.org/t/p/w342",
    };
  },
  props: ["item"],
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.flag {
  height: 100px;
  width: 150px;
}

.img {
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

.img:hover img {
  display: none;
}

.img:hover .retro {
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
.cards {
  display: flex;
  flex-wrap: wrap;
}
</style>
