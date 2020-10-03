<template>
  <div id="app">
    <grid-layout
      class="grid"
      :layout="layout"
      :col-num="16"
      :max-rows="9"
      :row-height="100"
      :is-draggable="true"
      :is-resizable="true"
      :is-mirrored="false"
      :vertical-compact="true"
      :margin="[10, 10]"
      :use-css-transforms="true"
    >
      <grid-item
        class="item"
        v-for="item in layout"
        :x="item.x"
        :y="item.y"
        :w="item.w"
        :h="item.h"
        :i="item.i"
        :key="item.i"
      >
        {{ item.i }}
      </grid-item>
    </grid-layout>
  </div>
</template>

<script>
import VueGridLayout from "vue-grid-layout";
// import Chat from "@/components/Chat.vue";
// import Poll from "@/components/Poll.vue";

export default {
  name: "App",
  components: {
    GridLayout: VueGridLayout.GridLayout,
    GridItem: VueGridLayout.GridItem
    // Chat,
    // Poll
  },
  data: () => ({
    layout: [
      { x: 0, y: 0, w: 16, h: 1, i: "Chat" },
      { x: 0, y: 1, w: 16, h: 1, i: "Poll" },
      { x: 0, y: 1, w: 16, h: 1, i: "Tool" }
      // { x: 2, y: 0, w: 2, h: 4, i: "1" },
      // { x: 4, y: 0, w: 2, h: 5, i: "2" },
      // { x: 6, y: 0, w: 2, h: 3, i: "3" },
      // { x: 8, y: 0, w: 2, h: 3, i: "4" },
      // { x: 10, y: 0, w: 2, h: 3, i: "5" },
      // { x: 0, y: 5, w: 2, h: 5, i: "6" },
      // { x: 2, y: 5, w: 2, h: 5, i: "7" },
      // { x: 4, y: 5, w: 2, h: 5, i: "8" },
      // { x: 6, y: 3, w: 2, h: 4, i: "9" },
      // { x: 8, y: 4, w: 2, h: 4, i: "10" },
      // { x: 10, y: 4, w: 2, h: 4, i: "11" },
      // { x: 0, y: 10, w: 2, h: 5, i: "12" },
      // { x: 2, y: 10, w: 2, h: 5, i: "13" },
      // { x: 4, y: 8, w: 2, h: 4, i: "14" },
      // { x: 6, y: 8, w: 2, h: 4, i: "15" },
      // { x: 8, y: 10, w: 2, h: 5, i: "16" },
      // { x: 10, y: 4, w: 2, h: 2, i: "17" },
      // { x: 0, y: 9, w: 2, h: 3, i: "18" },
      // { x: 2, y: 6, w: 2, h: 2, i: "19" }
    ],
    draggable: true,
    resizable: true,
    index: 0
  }),
  methods: {
    itemTitle(item) {
      var result = item.i;
      if (item.static) {
        result += " - Static";
      }
      return result;
    }
    /*
        increaseWidth: function(item) {
            var width = document.getElementById("content").offsetWidth;
            width += 20;
            document.getElementById("content").style.width = width+"px";
        },
        decreaseWidth: function(item) {
            var width = document.getElementById("content").offsetWidth;
            width -= 20;
            document.getElementById("content").style.width = width+"px";
        },
        removeItem: function(item) {
            //console.log("### REMOVE " + item.i);
            this.layout.splice(this.layout.indexOf(item), 1);
        },
        addItem: function() {
            var self = this;
            //console.log("### LENGTH: " + this.layout.length);
            var item = {"x":0,"y":0,"w":2,"h":2,"i":this.index+"", whatever: "bbb"};
            this.index++;
            this.layout.push(item);
        }
*/
  },
  computed: {}
};
</script>

<style>
.grid {
  width: 100%;
}

.item {
  background-color: lightgrey;
}
</style>
