<script>
  export default {
    props: ["text", "id", "completed"],

    data() {
      return {
        name: this.text
      }
    },

    methods: {
      completedCheck(data) {
        return data ? "checked" : "";
      }
    }

  }
</script>

<template>

  <li class="todo__item show" :class="completedCheck(this.completed)">
    <div class="checkbox-wrapper">
      <input :id="this.id" type="checkbox" class="checkbox" :checked="completedCheck()">
      <label for="checkbox1">{{ name }}</label>
    </div>
    <button class="todo__item-remov" :id="this.id">X</button>
  </li>

</template>
