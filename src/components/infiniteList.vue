<template>
  <div id="infinite-list">
    <h1 id="infinite-header">Infinite Boxes</h1>

    <div id="infinite-container" v-on:scroll="scrolledDown()">
      <button
        id="scroll-top-button"
        type="button"
        v-show="showButton"
        v-on:click="scrollToTop()"
      >
        &#8743;
      </button>

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
          <option
            v-for="option in options"
            :key="option.value"
            :value="option.value"
          >
            {{ option.text }}
          </option>
        </select>
        <span> boxes at a time</span>
      </div>

      <span>You've generated {{ boxes.length }} boxes</span>
    </div>
  </div>
</template>

<script>
import summaryBox from "@/components/SummaryBox";

export default {
  components: { summaryBox },
  data() {
    return {
      boxes: [],
      load: 10,
      options: [
        { text: "five", value: 5 },
        { text: "ten", value: 10 },
        { text: "twenty-five", value: 25 },
        { text: "fifty", value: 50 },
      ],
      showButton: false,
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
      var times = 0;

      do {
        var box = {};

        box.id = this.boxes.length + 1;
        box.text = lorem.substr(0, Math.random() * (613 - 56) + 56);

        this.boxes.push(box);
        times += 1;
      } while (times < this.load);
    },
    scrollToTop() {
      var list = document.getElementById("infinite-container");
      var header = document.getElementById("infinite-header");
      var listTop = list.offsetTop;
      var headTop = header.offsetTop;

      list.scrollTo(0, headTop - listTop);
    },
    scrolledDown() {
      this.showButton =
        document.getElementById("infinite-container").scrollTop > 500;
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
  scroll-behavior: smooth;
}

#scroll-top-button {
  position: fixed;
  margin-top: 15px;
  padding: 5px 12px;

  border-radius: 50%;
  border: 1px solid lightskyblue;

  font-size: larger;
  background-color: lightblue;
  color: blue;
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