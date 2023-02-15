<script setup>
  import InputComponent from "./components/InputComponent.vue";
  import ToDo from "./components/ToDo.vue";
  import {request} from "./components/getData";
</script>

<script>
  export default {
    data() {
      return {
        data: []
      }
    },

    mounted() {
      request('https://jsonplaceholder.typicode.com/todos?_page=1&_limit=5', 'GET')
        .then(todos => {
          for (let todo in todos) {
            this.data.push(todos[todo]);
          }
        });
    },

    methods: {

      onDataCollection(data) {
        let obj = {};
        obj.title = data.title;
        obj.completed = false;
        obj.id = this.data.length + 1;

        this.data.push(obj);
      },

      onDeleteItem(data) {
        this.data.forEach(item => {
          if (item.id === data.idDel) {
            this.data.splice(item.id - 1, 1)
          }
        })
      },

      onChecked(data) {
        this.data.forEach(item => {
          if (item.id === data.idCheck) {
            item.completed = !item.completed;
          }
        })
      },
    },

  }
</script>

<template>

  <InputComponent :onDataCollection="onDataCollection"/>

  <ul class="todo">

    <template v-for="(todo) in data">
      <ToDo :title="todo.title" :id="todo.id" :completed="todo.completed" :onDeleteItem="onDeleteItem" :onChecked="onChecked"/>
    </template>

  </ul>
</template>

