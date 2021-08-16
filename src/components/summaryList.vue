<template>
  <div>
    <h1>Scrolling Boxes</h1>
    <div id="summary-container">
      <summary-box
        v-for="box in boxes"
        :key="box.id"
        v-bind:box="box"
        class="box"
      />
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
    };
  },
  created() {
    this.makeTen();
  },
  methods: {
    makeTen() {
      const lorem =
        "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aliquam sit amet efficitur mi, quis condimentum ante. Aliquam eget risus eget quam tincidunt congue. Nunc sit amet urna luctus, blandit justo vitae, luctus libero. Vivamus quis sapien in orci euismod ultrices. Nullam semper massa ut euismod vehicula. Quisque quis eros nunc. Suspendisse interdum, purus in consequat venenatis, massa orci ultricies libero, maximus elementum elit tellus vel felis. In nulla felis, tempus ac eleifend at, posuere in odio. In accumsan aliquet semper. Phasellus tincidunt massa sed lacus sollicitudin, a congue ex sollicitudin.";
      let times = 0;

      do {
        var box = {};

        box.id = this.boxes.length + 1;
        box.text = lorem.substr(0, Math.random() * (613 - 56) + 56);

        this.boxes.push(box);
        times += 1;
      } while (times < 10);
    },
  },
};
</script>

<style>
#summary-container {
  max-height: 200px;

  overflow: scroll;
}

.box {
  border: 1px solid blue;
  margin-bottom: 10px;
}
</style>