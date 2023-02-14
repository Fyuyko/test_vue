<script>
  export default {
    data() {
      return {
        text: ""
      }
    },

    methods: {
      createUserTodo(event) {
        //нужно отправить данные в ToDo
        // @submit="(event) => createUserTodo(event)"
      }
    }
  }
</script>

<template>
  <form class="add-todo">
    <input v-model="text" class="add-todo__import" placeholder="Поле ввода" />
    <button class="add-todo__button">Click</button>
  </form>
</template>

<style scoped>

</style>