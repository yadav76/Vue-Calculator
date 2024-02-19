<template>
  <div>
    <CalculatorComp />
  </div>
</template>

<script>
import CalculatorComp from "./components/CalculatorComp.vue";

export default {
  name: "App",
  component: {
    CalculatorComp,
  },
  components: { CalculatorComp },
};
</script>

<style lang="scss" scoped></style>
