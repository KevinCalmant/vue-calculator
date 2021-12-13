<template>
  <div class="screen">
    <div class="screen-member">
      <h3>{{ calculation }}</h3>
    </div>
    <div class="screen-member">
      <h1>{{ result }}</h1>
    </div>
  </div>
</template>

<script lang="ts">
import { computed, defineComponent } from "vue";

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
  setup(props) {
    const computedResult = computed(() => {
      if (isNaN(+props.result)) {
        return "0";
      }
      return new Intl.NumberFormat("fr-FR").format(+props.result);
    });
    return {
      computedResult,
    };
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
