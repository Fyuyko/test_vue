<script setup>
  import InputComponent from "./components/InputComponent.vue";
  import ToDo from "./components/ToDo.vue";
  import {request} from "./components/getData";
</script>

<script>
  export default {
    data() {
      return {
        data: [],
        localData: [],
      }
    },

    mounted() {
      request('https://jsonplaceholder.typicode.com/todos?_page=1&_limit=5', 'GET')
        .then(todos => {
          for (let todo in todos) {
            this.data.push(todos[todo]);
          }

          return this.data;

        }).then(data => {
          if (this.localData) {
            const localData = JSON.parse(localStorage.getItem("todo"));
            localData.forEach(localDataItem => {
              data.push(localDataItem);
              this.localData.push(localDataItem);
            })
          }
      });

    },

    methods: {

      onDataCollection(data) {
        this.createTodoItem(data)
      },

      createTodoItem(data) {
        let obj = {};
        obj.title = data.title;
        obj.completed = false;
        obj.id = Math.floor(Math.random() * (1000 - 5 + 1)) + 5;
        this.data.push(obj);

        this.localData.push(obj);
        localStorage.setItem("todo", JSON.stringify(this.localData));
      },

      onDeleteItem(data) {
        this.data.forEach(item => {
          if (item.id === data.idDel) {
            let index = this.data.indexOf(item);
            this.data.splice(index, 1);
          }
        });
        this.localData.forEach(localDataItem => {
          if (localDataItem.id === data.idDel) {
            let index = this.localData.indexOf(localDataItem);
            this.localData.splice(index, 1);
            localStorage.setItem("todo", JSON.stringify(this.localData));
          }
        })
      },

      onChecked(data) {
        this.data.forEach(item => {
          if (item.id === data.idCheck) {
            item.completed = !item.completed;

            console.log(this.data)
          }
        })
        this.localData.forEach(localDataItem => {
          if (localDataItem.id === data.idCheck) {
            localDataItem.completed = !localDataItem.completed;

            console.log(localDataItem.completed)

            localStorage.setItem("todo", JSON.stringify(this.localData));
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

