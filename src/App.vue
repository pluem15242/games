<template>
<body>
  <div id="app">
    <Game msg />
  </div>
</body>
</template>

<script>
import Game from "./components/game.vue";

export default {
  name: "App",
  components: {
    Game,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  padding: 3em;
}
body { 
  background-image: url("https://downloadwap.com/thumbs2/wallpapers/p2ls/new/35/mK8cFTzq.jpg"); 
  background-attachment: fixed;
  background-position: center;
  background-repeat: no-repeat;
  background-size: cover;
}
</style>
