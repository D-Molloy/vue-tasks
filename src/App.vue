<template>
  <div id="app">
    <!-- <img src="./assets/logo.png"> -->
    <Tasks />
  </div>
</template>

<script>
import Tasks from "./components/Tasks.vue";

export default {
  name: "app",
  components: {
    Tasks
  }
};
</script>

<style>
@import url("https://fonts.googleapis.com/css?family=Montserrat:400,700");

body {
  background-color: #eeeeee;
  font-family: "Montserrat", sans-serif;
  display: grid;
  grid-template-rows: auto;
  justify-items: center;
  align-items: center;
}
body,
html {
  margin: 0;
  height: 100%;
}
#app {
  width: 50%;
}
</style>
