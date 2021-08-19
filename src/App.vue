<template>
  <div id="header-body-flex">
    <Header />
    <div id="body-flex">
      <div id="main-scroll-flex">
        <infinite-list />
      </div>

      <div id="sidebar-flex">
        <fixed-list />
        <fixed-list />
      </div>
    </div>
  </div>
</template>

<script>
import FixedList from "@/components/FixedList";
import InfiniteList from "@/components/InfiniteList";
import Header from "@/components/Header";

export default {
  name: "App",
  components: {
    FixedList,
    InfiniteList,
    Header,
  },
};
</script>

<style>
html {
  display: flex;
  height: 100vh;
  width: 100vw;
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

#header-body-flex {
  display: flex;
  flex-direction: column;
}

#header {
  background-color: green;
  height: 10%;
}

#body-flex {
  display: flex;
  flex-direction: row;
  height: 90%;
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
