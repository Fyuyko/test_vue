<template>
  <div class="sort-alph">
    <input id="checkbox-alph" type="checkbox" class="checkbox-alph" v-model="checked" @change="sort(this)">
    <label for="checkbox-alph">{{checked ? "Отсортровано по алфавиту" : "Отсортировать по алфавиту"}}</label>
  </div>
</template>

<script>
export default {
  name: "todoSortAlphItemComponent",

  props: ["onSortAlphTodo"],

  data() {
    return {
      checked: false,
    }
  },

  methods: {
    sort(data) {
      this.onSortAlphTodo(data.checked);
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