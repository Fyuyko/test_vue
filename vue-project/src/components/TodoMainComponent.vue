<template>

  <TodoInputComponent :onCreate="createTodo"/>
  <TodoListComponent :onChecked="checkedTodo" :onDeleted="deleteTodo" :todoData="data"/>
  <LoadingComponent v-if="!this.isLoaded"/>
  <div class="empty-component" v-if="this.isLoaded && data.length === 0">Задачи отсутствуют</div>

</template>

<script>
import {request} from "../utils/getData.js";
import TodoInputComponent from "./TodoInputComponent.vue";
import TodoListComponent from "./TodoListComponent.vue";
import LoadingComponent from "./LoadingComponent.vue";


export default {
  name: "TodoMainComponent",

  components: {LoadingComponent, TodoInputComponent, TodoListComponent},

  data() {
    return {
      data: [],
      isLoaded: false,
    }
  },

  mounted() {
    request('https://jsonplaceholder.typicode.com/todos?_page=1&_limit=5', 'GET')
      .then(todos => {
        for (let todo in todos) {
          this.data.push(todos[todo]);
          this.isLoaded = true;
        }
      });
  },

  methods: {
    createTodo(data) {
      let obj = {
        title: data,
        isCompleted: false,
        id: Math.floor(Math.random() * (1000 - 5 + 1)) + 5,
      };
      this.data.push(obj);
    },

    checkedTodo(data) {
      this.data.forEach(item => {
        if (item.id === data) {
          item.completed = !item.completed;
        }
      })
    },

    deleteTodo(data) {
      this.data.forEach((item, index) => {
        if (item.id === data) {
          this.data.splice(index, 1);
        }
      });
    },
  },

}
</script>

<style scoped>


  .empty-component {
    width: fit-content;
    margin: 0 auto;
  }
</style>