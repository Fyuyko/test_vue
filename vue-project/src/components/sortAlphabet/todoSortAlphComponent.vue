<template>
  <todoSortAlphItemComponent :onSortAlphTodo="onSortAlphTodo"/>
</template>

<script>
import TodoSortAlphItemComponent from "./todoSortAlphItemComponent.vue";

export default {
  name: "todoSortAlphComponent",

  components: {TodoSortAlphItemComponent},

  props: ["onSortAlphTodo"],

}
</script>

<style scoped>

</style>