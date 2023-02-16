<template>

  <ul class="todo">
    <li class="todo__item show" v-for="todo in todoData" >
      <TodoItemComponent :title="todo.title" :id="todo.id" :completed="todo.isCompleted" :deletedTodo="this.onDeleted" :checkedTodo="this.onChecked"/>
    </li>
  </ul>

</template>

<script>
import TodoItemComponent from "./TodoItemComponent.vue";

export default {
  name: "TodoListComponent",
  components: {TodoItemComponent},

  props: ["onChecked", "onDeleted", "todoData"],

  data() {
    return {

    }
  },

}
</script>

<style scoped>
  .todo {
    font-family: NotoSans;
    font-size: 12px;
    list-style: none;
    padding: 0;
  }

  .todo__item {
    background-color: #fff;
    -webkit-box-pack: justify;
    -ms-flex-pack: justify;
    justify-content: space-between;
    margin-bottom: 5px;
    padding: 10px;
    display: none;
  }

  .todo__item.show {
    display: -webkit-box;
    display: -ms-flexbox;
    display: flex;
  }
</style>