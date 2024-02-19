<template>
  <div class="calculator">
    <input type="text" v-model="expression" />
    <div class="buttons">
      <button
        v-for="button in buttons"
        :key="button"
        @click="addToExpression(button)"
      >
        {{ button }}
      </button>
      <button @click="evaluateExpression()">=</button>
    </div>
    <button @click="clearExpression()" id="clear">C</button>
  </div>
</template>

<script>
export default {
  name: "CalculatorComp",
  data() {
    return {
      expression: "",
    };
  },
  methods: {
    addToExpression(clickedNumber) {
      this.expression += clickedNumber;
    },
    evaluateExpression() {
      try {
        this.expression = eval(this.expression);

        if (this.expression == "Infinity") {
          setTimeout(() => {
            this.expression = "";
          }, 1000);
        }
      } catch (error) {
        this.expression = "Error";
        setTimeout(() => {
          this.expression = "";
        }, 1000);
      }
    },
    clearExpression() {
      this.expression = "";
    },
  },
  computed: {
    buttons() {
      return [
        "7",
        "8",
        "9",
        "/",
        "4",
        "5",
        "6",
        "*",
        "1",
        "2",
        "3",
        "-",
        "0",
        ".",
        "+",
      ];
    },
  },
};
</script>

<style scoped>
.calculator {
  width: 250px;
  margin: 50px auto;
  background-color: #f2f2f2;
  border-radius: 5px;
  padding: 20px;
}

input[type="text"] {
  width: 220px;
  padding: 10px;
  margin-bottom: 10px;
}

.buttons {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 10px;
}

button {
  padding: 10px;
  border: none;
  background-color: #d9d9d9;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

button:hover {
  background-color: #bfbfbf;
}

button:active {
  background-color: #999999;
}

#clear {
  color: #fff;
  width: 250px;
  margin-top: 10px;
  background-color: #f59;
}
</style>
