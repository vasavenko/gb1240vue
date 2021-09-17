<template>
  <div>
    <div class="display">
      <input type="number" v-model.number="operand1" />
      <input type="number" v-model.number="operand2" />
      = {{ result }}
      <br />
    </div>

    <div class="keyboard">
      <button
        v-for="operation in operations"
        :key="operation"
        :disabled="operand1 === '' || operand2 === ''"
        @click="calculate(operation)"
      >
        {{ operation }}
      </button>
    </div>

    <div v-if="error" :class="{ error: !!error }">
      Ошибка!
      {{ error }}
    </div>
  </div>
</template>

<script>
export default {
  name: "Calculator",
  data() {
    return {
      operand1: "",
      operand2: "",
      result: 0,
      error: "",
      operations: ["+", "-", "*", "/", "**", "%"],
      logs: {},
      checked: false,
      picked: "operand1",
    };
  },
  methods: {
    add() {
      this.result = +this.operand1 + +this.operand2;
    },
    substract() {
      this.result = this.operand1 - this.operand2;
    },
    divide() {
      const { operand1, operand2 } = this;
      if (+operand2 === 0) {
        this.error = "Делить на 0 нельзя!";
      } else {
        this.result = operand1 / operand2;
      }
    },
    multiply() {
      this.result = this.operand1 * this.operand2;
    },
    exp() {
      this.result = this.operand1 ** this.operand2;
    },
    intDiv() {
      this.result = Math.floor(this.operand1 / this.operand2);
    },
    calculate(operation = "+") {
      this.error = "";
      switch (operation) {
        case "+":
          this.add();
          break;
        case "-":
          this.substract();
          break;
        case "*":
          this.multiply();
          break;
        case "/":
          this.divide();
          break;
        case "**":
          this.exp();
          break;
        case "%":
          this.intDiv();
          break;
      }
    },
  },
};
</script>

<style scoped>
.error {
  color: red;
}
.vir_keyboard {
  margin-top: 30px;
}
</style>
