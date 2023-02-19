<script>
  export default {
    name: "TodoInputComponent",

    props: ['onCreate'],

    data() {
      return {
        value: ""
      }
    },

    methods: {
      dataReceive() {
        if (this.value.split(' ').join('').length > 0) {
          this.onCreate(this.value)
          this.value = "";
        }
      }
    }
  }
</script>

<template>
  <form class="add-todo" @submit.prevent="dataReceive">
    <input type='text' v-model="value" class="add-todo__import" placeholder="Поле ввода" />
    <button class="add-todo__button">Click</button>
  </form>
</template>

<style scoped>
  .add-todo {
    background-color: #fff;
    height: 38px;
    display: -webkit-box;
    display: -ms-flexbox;
    display: flex;
    -webkit-box-align: center;
    -ms-flex-align: center;
    align-items: center;
    margin-bottom: 10px;
    -webkit-box-sizing: border-box;
    box-sizing: border-box;
  }

  .add-todo__import {
    flex: 1;

    outline: none;
    border: none;
    padding: 0 0 0 16px;
    width: calc(100% - 51px);
  }

  .add-todo__import::placeholder {
    color: #bac2cd;
  }

  .add-todo__button {
    border: none;
    outline: none;
    background-color: #55b8ff;
    color: #fff;
    width: 70px;
    height: 32px;

    padding: 10px 20px;
    margin-right: 10px;
  }

</style>