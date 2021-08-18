<template>
  <div id="app-list-flex">
    <div id="main-scroll-flex">
      <infinite-list />
    </div>
    <div id="sidebar-flex">
      <fixed-list />
      <fixed-list />
    </div>
  </div>
</template>

<script>
import FixedList from "@/components/fixedList";
import InfiniteList from "@/components/infiniteList.vue";

export default {
  name: "App",
  components: { FixedList, InfiniteList },
};
</script>

<style>
html {
  display: flex;
  height: 100vh;
  overflow: hidden;
}

body {
  display: flex;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;

  display: flex;
}

#app-list-flex {
  display: flex;
  flex-direction: row;
}

#main-scroll-flex {
  display: flex;
  margin-right: 10px;
}

#sidebar-flex {
  display: flex;
  flex-direction: column;
}
</style>
