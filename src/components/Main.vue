<template>
  <div class="main">
    <!-- Film -->
    <section>
      <h1>Films</h1>
      <ul class="cards">
        <Card v-for="(card, index) in movieCards" :key="index" :card="card" />
      </ul>
    </section>
    <!-- Series -->
    <section>
      <h1>Series</h1>
      <ul class="cards">
        <Card v-for="(card, index) in seriesCards" :key="index" :card="card" />
      </ul>
    </section>
  </div>
</template>

<script>
import Card from "./Card.vue";
export default {
  name: "Main",
  components: {
    Card,
  },
  props: ["movieCards", "seriesCards"],
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h1 {
  margin-top: 20px;
  padding: 30px 10px;
  // background-color: black;
}

section {
  margin: 0px 50px;
  border-bottom: 1px solid black;
}

.main {
  height: 100%;
  width: 100%;
  // padding: 0px 50px;
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
