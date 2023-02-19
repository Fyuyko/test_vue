<template>
  <div class="sort-alph">
    <button id="checkbox-alph" :disabled="this.sorting" @click.stop="sort(this)">click</button>
    <label for="checkbox-alph">{{sorting ? "Отсортровано по алфавиту" : "Отсортировать по алфавиту"}}</label>
  </div>
</template>

<script>
export default {
  name: "todoSortAlphItemComponent",

  props: ["onSortAlphTodo"],

  data() {
    return {
      sorting: false,
    }
  },

  methods: {
    sort(button) {
      this.sorting = !this.sorting;
      this.onSortAlphTodo(button.sorting);
    }
  }

}
</script>

<style scoped>
  .sort-alph {
    padding-bottom: 10px;
    display: flex;
    gap: 10px;
  }
</style>