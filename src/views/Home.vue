<template>
  <div>
    <div class="container">
      <div class="column-1">
        <input
          type="number"
          id="inputNumber"
          name="inputNumber"
          v-model="value"
          @keyup="onInputKeyUp"
        />
      </div>
      <div class="column-2">
        <select
          name="inputOption"
          id="inputOption"
          v-model="optionSelected"
          @change="onOptionChange"
        >
          <option value="0">isPrime</option>
          <option value="1">IsFibonacci</option>
        </select>
      </div>
      <div class="column-3">{{ result }}</div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      value: 0,
      optionSelected: 0,
      result: false,
    };
  },
  created() {
    this.onCheckValueType();
  },
  methods: {
    onInputKeyUp() {
      if (this.value) {
        if (this.value < 0) {
          this.value = 1;
        }
        this.value = Math.round(this.value);
        this.onCheckValueType();
      }
    },
    onCheckValueType: async function () {
      if (this.optionSelected == 0) {
        this.result = this.isPrime(this.value);
      } else {
        this.result = this.IsFibonacci(this.value);
      }
    },
    onOptionChange() {
      this.onCheckValueType();
    },
    isFloat(value) {
      return value === +value && value !== (value | 0);
    },
    isPrime: function (value) {
      for (let i = 2; i < value; i++) {
        if (value % i == 0) return false;
      }
      return value > 1;
    },
    IsFibonacci: function (value) {
      return (
        this.isPerfectSquare(5 * value * value + 4) ||
        this.isPerfectSquare(5 * value * value - 4)
      );
    },
    isPerfectSquare: function (value) {
      return value > 0 && Math.sqrt(value) % 1 === 0;
    },
  },
};
</script>

<style lang="scss" scoped>
.container {
  display: flex;
  justify-content: space-between;
}
.column-1 {
  width: 200px;
}
.column-2 {
  width: calc(100% - 500px);
  min-width: 100px;
}
.column-3 {
  width: 300px;
}
</style>