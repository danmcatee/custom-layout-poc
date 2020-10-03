<template>
  <div id="app">
    <div class="toolsRow">
      <div
        class="tool"
        v-for="(tool, i) in tools"
        :key="tool.type"
        :class="[selectedTool === i ? 'tool-selected' : null]"
        @click="selectedTool = i"
      >
        {{ tool.type }}
      </div>
      <div class="tool" @click="selectedTool = null">x</div>
    </div>
    <div class="gridContainer">
      <div class="baseGrid toolGrid">
        <Chat
          v-if="tools[0].visible"
          :style="{
            gridArea: `${tools[0].position.top}/${tools[0].position.left}/${tools[0].position.bottom}/${tools[0].position.right}`
          }"
        />
        <Poll v-if="tools[1].visible" />
      </div>
      <div class="baseGrid gridOverlay" v-if="overlayVisible">
        <div class="overlayItem" v-for="i in 144" :key="i"></div>
      </div>
    </div>
  </div>
</template>

<script>
import Chat from "@/components/Chat.vue";
import Poll from "@/components/Poll.vue";

export default {
  name: "App",
  components: {
    Chat,
    Poll
  },
  data: () => ({
    tools: [
      {
        type: "chat",
        visible: true,
        position: { top: 2, left: 1, bottom: 4, right: 1 }
      },
      {
        type: "poll",
        visible: true,
        position: { top: 0, left: 0, bottom: 0, right: 0 }
      }
    ],
    selectedTool: null
    // overlayVisible: true
  }),
  computed: {
    overlayVisible: function() {
      return this.selectedTool !== null ? true : false;
    }
  }
};
</script>

<style>
.toolsRow {
  display: flex;
  margin-bottom: 2rem;
}
.tool {
  border: 1px solid black;
  padding: 2rem;
  margin-right: 1rem;
}

.tool-selected {
  border: 1px solid lime;
}

.gridContainer {
  position: relative;
}

.baseGrid {
  display: grid;
  grid-template-columns: repeat(16, 1fr);
  grid-template-rows: repeat(9, 1fr);
  height: 600px;
  gap: 1rem;
}

.toolGrid {
}

.gridOverlay {
  position: absolute;
  width: 100%;
  top: 0;
  left: 0;
}

.overlayItem {
  border: 1px solid black;
}
</style>
