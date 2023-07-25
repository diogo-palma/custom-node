<script lang="ts" setup>
import {
  VueFlow,
  MiniMap,
  Controls,
  Background,
  BackgroundVariant,
  isNode,
  useVueFlow,
} from "@braks/vue-flow";
import { ref } from "vue";
import CustomNode from "./CustomNode.vue";

const elements = ref([
  {
    id: "1",
    type: "custom",
    label: "Node 1",
    position: { x: 250, y: 5 },
    data: { bgImage: "https://cdn2.thecatapi.com/images/DmP9GCClC.jpg" },
  },
  {
    id: "2",
    type: "custom",
    label: "Node 2",
    position: { x: 250, y: 250 },
    data: { bgImage: "https://cdn2.thecatapi.com/images/88l.jpg" },
  },
  {
    id: "e1-2",
    source: "1",
    target: "2",
  },
]);
const {
  onPaneReady,
  onNodeDragStop,
  onConnect,
  instance,
  addEdges,
} = useVueFlow();
onPaneReady(({ fitView }) => {
  fitView({ padding: 0.1 });
});
onNodeDragStop((e) => console.log("drag stop", e));
onConnect((params) => addEdges([params]));
</script>
<template>
  <VueFlow
    v-model="elements"
    class="vue-flow-basic-example"
    :default-zoom="1.5"
    :min-zoom="0.2"
    :max-zoom="4"
    :zoom-on-scroll="false"
  >
    <template #node-custom="props">
      <CustomNode v-bind="props" />
    </template>
    <MiniMap style="transform: scale(0.5); transform-origin: bottom right" />
    <Controls />
  </VueFlow>
</template>
<style>
</style>