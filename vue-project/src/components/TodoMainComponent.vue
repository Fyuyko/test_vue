<template>

  <todoSortAlphComponent :onSortAlphTodo="sortAlphTodo"/>
  <TodoSortComponent :onCompleted="completeTodo"/>
  <TodoInputComponent :onCreate="createTodo"/>
  <TodoListComponent :onChecked="checkedTodo" :onDeleted="deleteTodo" :todoData="alphSortData" />
  <LoadingComponent v-if="!this.isLoaded"/>
  <div class="empty-component" v-if="this.isLoaded && data.length === 0">Задачи отсутствуют</div>

</template>

<script>
import {request} from "../utils/getData.js";
import TodoInputComponent from "./TodoInputComponent.vue";
import TodoListComponent from "./TodoListComponent.vue";
import LoadingComponent from "./LoadingComponent.vue";
import TodoSortComponent from "./sortCompleted/TodoSortCompletedComponent.vue";
import TodoSortAlphComponent from "./sortAlphabet/todoSortAlphComponent.vue";


export default {
  name: "TodoMainComponent",

  components: {TodoSortAlphComponent, TodoSortComponent, LoadingComponent, TodoInputComponent, TodoListComponent},

  data() {
    return {
      data: [],
      isLoaded: false,
      completed: "all",
      isAlphSort: false,
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
        completed: false,
        id: Math.floor(Math.random() * (1000 - 5 + 1)) + 5,
      };
      this.data.push(obj);
    },

    checkedTodo(data) {
      this.data.forEach(item => {
        if (item.id === data.id) {
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

    completeTodo(data) {
      this.completed = data;
    },

    sortAlphTodo(data) {
      this.isAlphSort = data;
    },
  },

  computed: {

    sortData() {

      switch (this.completed) {
        case "all":
          return this.data;
          break;
        case "completed":
          return this.data.filter(item => item.completed)
          break;
        case "uncompleted":
          return this.data.filter(item => !item.completed)
          break;
        default:
          return this.data;
          break;
      }

    },

    alphSortData() {

      switch (this.isAlphSort) {
        case false:
          return this.sortData;
        case true:
          return this.sortData.sort((x, y) => {
            return x.title.localeCompare(y.title)
          });
        default:
          return this.sortData;
          break;
      }

    }

  }

}
</script>

<style scoped>


  .empty-component {
    width: fit-content;
    margin: 0 auto;
  }
</style>