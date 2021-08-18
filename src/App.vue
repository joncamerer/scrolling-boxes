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
import InfiniteList from "@/components/infiniteList";

export default {
  name: "App",
  components: {
    FixedList,
    InfiniteList,
  },
};
</script>

<style>
html {
  display: flex;
  height: 100vh;
}

body {
  display: flex;
}

#app {
  display: flex;

  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
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
