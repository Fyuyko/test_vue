<template>

  <ul class="todo">
    <li class="todo__item" v-for="todo in todoData">
      <TodoItemComponent :title="todo.title" :id="todo.id" :completed="todo.completed" :onDeleted="this.onDeleted" :onChecked="this.onChecked" />
    </li>
  </ul>

</template>

<script>
import TodoItemComponent from "./TodoItemComponent.vue";

export default {
  name: "TodoListComponent",
  components: {TodoItemComponent},

  props: ["onChecked", "onDeleted", "todoData"],

  methods: {

  },

}
</script>

<style scoped>
  .todo {
    font-size: 12px;
    list-style: none;
    padding: 0;
  }

  .todo__item {
    display: flex;
    background-color: #fff;
    -webkit-box-pack: justify;
    -ms-flex-pack: justify;
    justify-content: space-between;
    margin-bottom: 5px;
    padding: 10px;
  }

</style>