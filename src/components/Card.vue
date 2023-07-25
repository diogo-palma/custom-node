<script lang="ts" setup>
import { defineProps } from "vue";

interface Props {
  bgImage: string;
}

const props = defineProps<Props>();
</script>
<template>
  <div
    class="card"
    :style="{
      backgroundImage: `url('${props.bgImage}')`,
      backgroundRepeat: 'no-repeat',
      backgroundSize: 'cover',
    }"
  >
    <slot></slot>
  </div>
</template>
<style scoped>
.card {
  border: 1px black solid;
  padding: 1rem;
  display: flex;
  flex-direction: column;
}
</style>