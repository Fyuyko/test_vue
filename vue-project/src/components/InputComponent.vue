<script>
  export default {
    data() {
      return {
        text: ""
      }
    },

    props: ['onDataCollection'],

    methods: {
      dataCollection(event) {
        event.preventDefault();
        this.onDataCollection({
          text: this.text,
        })

        this.text = "";
      }
    }
  }
</script>

<template>
  <form class="add-todo" @submit="(event) => dataCollection(event)">
    <input type='text' v-model="text" class="add-todo__import" placeholder="Поле ввода" />
    <button class="add-todo__button">Click</button>
  </form>
</template>

<style scoped>

</style>