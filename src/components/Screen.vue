<template>
  <div class="screen">
    <div class="screen-member">
      <h3>{{ calculation }}</h3>
    </div>
    <div class="screen-member">
      <h1>{{ formatedResult }}</h1>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  props: {
    calculation: {
      type: String,
      required: true,
    },
    result: {
      type: Number,
      required: true,
    },
  },
  computed: {
    formatedResult(): string {
      return new Intl.NumberFormat("fr-FR").format(+this.result);
    },
  },
});
</script>

<style lang="scss" scoped>
.screen {
  height: 6em;
  background-color: slategray;
  padding: 1em;
}

.screen-member {
  height: 3em;
  display: flex;
  justify-content: flex-end;
  align-items: center;

  h1,
  h3 {
    color: white;
  }
}
</style>
