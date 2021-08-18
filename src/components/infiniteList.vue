<template>
  <div id="infinite-list">
    <h1>Infinite Boxes</h1>

    <div id="infinite-container">
      <summary-box
        v-for="box in boxes"
        :key="box.id"
        v-bind:box="box"
        class="infinite-box"
      />
    </div>

    <div id="load-bar">
      <div id="load-select">
        <span>Generate </span>
        <select v-model="load">
          <option value="5">5</option>
          <option value="10">10</option>
          <option value="25">25</option>
          <option value="50">50</option>
        </select>
        <span> boxes at a time</span>
      </div>

      <span>You've generated {{ boxes.length }} boxes</span>
    </div>
  </div>
</template>

<script>
import summaryBox from "@/components/summaryBox";

export default {
  components: { summaryBox },
  data() {
    return {
      boxes: [],
      load: 10,
    };
  },
  created() {
    this.makeLoad();
  },
  mounted() {
    const list = document.getElementById("infinite-container");

    list.addEventListener("scroll", () => {
      if (list.scrollTop + list.clientHeight >= list.scrollHeight) {
        this.makeLoad();
      }
    });
  },
  methods: {
    makeLoad() {
      const lorem =
        "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aliquam sit amet efficitur mi, quis condimentum ante. Aliquam eget risus eget quam tincidunt congue. Nunc sit amet urna luctus, blandit justo vitae, luctus libero. Vivamus quis sapien in orci euismod ultrices. Nullam semper massa ut euismod vehicula. Quisque quis eros nunc. Suspendisse interdum, purus in consequat venenatis, massa orci ultricies libero, maximus elementum elit tellus vel felis. In nulla felis, tempus ac eleifend at, posuere in odio. In accumsan aliquet semper. Phasellus tincidunt massa sed lacus sollicitudin, a congue ex sollicitudin.";
      let times = 0;

      do {
        var box = {};

        box.id = this.boxes.length + 1;
        box.text = lorem.substr(0, Math.random() * (613 - 56) + 56);

        this.boxes.push(box);
        times += 1;
      } while (times < this.load);
    },
  },
};
</script>

<style>
#infinite-list {
  display: flex;
  flex-direction: column;
  width: 60vw;
}

#infinite-container {
  overflow: scroll;
}

.infinite-box {
  border: 1px solid blue;
  color: blue;
  background-color: blue;

  margin-bottom: 10px;
}

#load-bar {
  display: flex;
  justify-content: space-around;
  flex-wrap: wrap;

  margin-top: 10px;
}
</style>