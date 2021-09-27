<template>
  <div class="main">
    <h2>Films</h2>
    <ul class="cards">
      <li v-for="(card, index) in movieCards" :key="index">
        <div
          class="img"
          style="background-size: cover"
          :style="{
            'background-image': 'url(' + imgUrl + card.poster_path + ')',
          }"
        >
          Titolo: {{ card.title }}
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
}
.main {
  height: 100%;
  max-width: 100%;
  padding: 0px 50px;
  background-color: grey;
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
