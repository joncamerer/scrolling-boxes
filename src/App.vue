<template>
  <div>
    <summary-list />
  </div>
</template>

<script>
import SummaryList from "@/components/summaryList";

export default {
  name: "App",
  components: { SummaryList },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
