<script>
  export default {
    props: ['onDataCollection'],

    data() {
      return {
        value: ""
      }
    },

    methods: {
      dataCollection() {
        this.onDataCollection({
          title: this.value,
        })

        this.value = "";
      }
    }
  }
</script>

<template>
  <form class="add-todo" @submit.prevent="dataCollection()">
    <input type='text' v-model="value" class="add-todo__import" placeholder="Поле ввода" />
    <button class="add-todo__button">Click</button>
  </form>
</template>
