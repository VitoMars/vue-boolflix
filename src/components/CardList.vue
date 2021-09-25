<template>
  <div class="flex">
    <div class="cardList" v-for="(card, index) in getCards()" :key="index">
      <Card :info="card" />
    </div>
  </div>
</template>

<script>
import axios from "axios";
import Card from "./Card.vue";
export default {
  name: "CardList",
  props: {
    msg: String,
    filter: String,
  },
  components: {
    Card,
  },
  data() {
    return {
      myApiKey: "77044b3f5f3cf322ff14c15889b611bc",
      APIUrl: "https://api.themoviedb.org/3/movie/550?api_key=",
      cardList: [],
    };
  },
  created() {
    this.getCard();
  },
  methods: {
    getCard() {
      axios
        .get(`${this.APIUrl}${this.myApiKey}&query=${query}`)
        .then((res) => {
          this.cardList = res.data.response;
        })
        .catch((err) => {
          console.log("Error ", err);
        });
    },
    getCards() {
      if (!this.filter) {
        return this.cardList;
      }
      let filteredList = this.cardList.filter((card) => {
        if (card.genre == this.filter) {
          return true;
        }
        return false;
      });
      return filteredList;
    },
  },
};
</script>

<style scoped lang="scss">
@import "@/style/mixins";
.flex {
  @include center-content();
  @include center();
  flex-wrap: wrap;
}
</style>
