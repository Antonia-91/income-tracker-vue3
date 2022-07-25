<template>
  <div class="income-list">
    <!---another compoinen --->
    <IncomeItem
      v-for="data in state.sortedIncome"
      :key="data.id"
      :income="data"
    />
  </div>
</template>

<script>
import IncomeItem from "./IncomeItem.vue";

export default {
  props: {
    state: Object,
  },
  components: { IncomeItem },
  setup() {
    return {
      IncomeItem,
    };
  },
};
</script>

<style scoped>
.income-list {
  margin-top: 30px;
  padding: 15px;
}
</style>
