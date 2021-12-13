<template>
  <div v-if="isNaN(+operation)" class="operator button">
    <span :class="'icon-' + label"></span>
  </div>
  <div v-else class="number button">
    <span>{{ label }}</span>
  </div>
</template>
<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  props: {
    operation: {
      type: String,
      required: true,
    },
    label: {
      type: String,
      required: true,
    },
  },
});
</script>

<style lang="scss" scoped>
.button {
  width: 10em;

  cursor: pointer;
  border: 0.02em solid darkblue;

  height: 2em;
  flex: 1;

  display: flex;
  justify-content: center;
  align-items: center;

  font-size: 3em;
  font-weight: bold;
}

.clear {
  font-weight: normal;
}

.operator {
  background-color: darkcyan;
  color: white;
}
</style>
