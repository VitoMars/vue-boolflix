<template>
  <div class="header">
    <div class="logo">Boolflix</div>
    <div class="ricerca">
      <input
        @keyup.enter="$emit('performSearch', inputText)"
        v-model="inputText"
        type="text"
        placeholder="Cerca il film o la serie"
      />
      <button @click="$emit('performSearch', inputText)">
        Cerca
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: "Header",
  data() {
    return {
      inputText: "",
    };
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 10vh;
  width: 100%;
  padding: 0px 50px;
  background-color: black;
}
.logo {
  font-size: 30px;
  color: red;
  text-transform: uppercase;
}

input,
button {
  border: 1px solid #888;
  border-radius: 3px;
  padding: 5px 20px;
}

input {
  margin: 0px 10px;
  outline: none;
}
button {
  color: white;
  background-color: black;
}

button:hover {
  background-color: #2d2d2d;
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
