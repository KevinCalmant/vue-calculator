<template>
  <div class="calculator">
    <Screen :calculation="calculation" :result="result" />
    <div class="keyboard">
      <div class="row" v-for="(row, index) in rows" :key="index">
        <Operator
          v-for="button in row"
          @click="handleOperation(button.operation)"
          :label="button.label"
          :operation="button.operation"
          :key="button.label"
        />
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
import Screen from "./components/Screen.vue";
import { rows } from "./misc/rows";
import Operator from "./components/Operator.vue";

export default defineComponent({
  name: "App",
  components: { Screen, Operator },
  data() {
    return {
      rows: rows,
    };
  },
  methods: {
    handleOperation(operation: string): void {
      if (operation === "clear") {
        this.calculation = "";
        this.result = 0;
      } else if (operation === "=") {
        const calcEval = eval(this.calculation);
        if (isNaN(calcEval)) {
          this.result = 0;
        } else {
          this.result = calcEval;
          this.calculation = "";
        }
      } else if (isNaN(+operation)) {
        this.calculation = this.calculation + " " + operation + " ";
      } else {
        this.calculation = this.calculation + +operation;
      }
    },
  },
  setup() {
    return {
      calculation: ref(""),
      result: ref(0),
    };
  },
});
</script>

<style lang="scss">
@import "./assets/fontello/css/fontello.css";

body,
html {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 100%;
}

.calculator {
  width: 30em;
}

.keyboard {
  width: 100%;
  height: 100%;

  display: flex;
  flex-direction: column;
}

.row {
  display: flex;
  flex-direction: row;

  width: 30em;
}
</style>
