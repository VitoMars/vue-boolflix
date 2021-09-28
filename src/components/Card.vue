<template>
  <div class="Card">
    <div class="Card-inner">
      <!-- Front Card -->
      <img
        class="front"
        v-if="card.poster_path != null"
        :src="'https://image.tmdb.org/t/p/w342' + card.poster_path"
        alt=""
      />
      <img class="front" v-else src="@/assets/no-poster.jpeg" alt="" />
      <!-- Back Card -->
      <div class="back">
        <span><b>Titolo: </b> {{ card.title ? card.title : card.name }}</span>
        <span
          ><b>Titolo originale: </b
          >{{
            card.original_title ? card.original_title : card.original_name
          }}</span
        >
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
  </div>
</template>

<script>
export default {
  name: "Card",
  data() {
    return {
      imgUrl: "https://image.tmdb.org/t/p/w342",
      flags: ["en", "it", "fr", "es", "de", "ru", "zh", "ja"],
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

.Card {
  background-color: transparent;
  perspective: 1000px;
}

.Card-inner {
  margin: 10px;
  height: 350px;
  width: 230px;
  display: flex;
  background-size: cover;
  background-color: black;
  transition: transform 0.6s;
  transform-style: preserve-3d;
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
}

.Card:hover .Card-inner {
  transform: rotateY(180deg);
}

.front,
.back {
  width: 100%;
  height: 100%;
  -webkit-backface-visibility: hidden;
  backface-visibility: hidden;
}

.front {
  transition: transform 1s;
  transform-style: preserve-3d;
}

.back {
  display: none;
  padding: 0px 10px;
  transform: rotateY(180deg);
}

.Card-inner:hover .front {
  display: none;
}

.Card-inner:hover .back {
  display: flex;
  flex-direction: column;
  justify-content: center;
  flex-wrap: wrap;
}

.flag {
  height: 20px;
  width: 30px;
}

.star {
  color: #fbcb15;
}
</style>
