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
        <div>
          Lingua:
          <img
            class="flag"
            :src="require(`../assets/flags/${card.original_language}.png`)"
            alt=""
          />
        </div>
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
      imgUrl: "https://image.tmdb.org/t/p/w342",
      // flags: ["it", "en", "fr", "es", "de"],
    };
  },
  props: ["card"],
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.flag {
  height: 30px;
  width: 30px;
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
