<template>
  <div class="main">
    <h2>Films</h2>
    <ul class="cards">
      <li v-for="(card, index) in movieCards" :key="index">
        {{ card.title }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "Main",
  props: ["movieCards"],
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.main {
  display: flex;
  align-items: center;
  height: 90vh;
  width: 100%;
  padding: 0px 50px;
  background-color: grey;
}
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
