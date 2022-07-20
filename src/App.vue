<template>
  <component :is="Header" :totalIncome="state.totalIncome" />
  <component :is="Form" />
</template>

<script>
import Header from "./components/Header.vue";
import { reactive, computed } from "vue";
import Form from "./components/Form.vue";

export default {
  setup() {
    const state = reactive({
      income: [],
      sortedIncome: computed(() => {
        let temp = [];

        temp = state.income.sort(function (a, b) {
          return b.date - a.date;
        });
        return temp;
      }),
      totalIncome: computed(() => {
        let temp = 0;
        if (state.income.length > 0) {
          for (let i = 0; i < state.income.length; i++) {
            temp += state.income[i].value;
          }
          return temp;
        } else {
          return 0;
        }
      }),
    });
    // Return template data
    return {
      Header,
      state,
      Form,
    };
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Fira Sans", sans-serif;
}
body {
  background: #eee;
}
</style>
