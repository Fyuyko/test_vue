<script>
  export default {
    props: {
      //id: this.id,
      //title: this.title,
      //completed: this.completed,
    },

    data() {
      return {
        id: 5,
        title: "Мое дело",
        completed: "checked",
      }
    },

    methods: {
      completedCheck() {
        return this.completed ? "checked" : "";
      }
    }

  }
</script>

<template>

  <li class="todo__item show" :class="completedCheck()">
    <div class="checkbox-wrapper">
      <input :id="this.id" type="checkbox" class="checkbox" :checked="completedCheck()">
      <label for="checkbox1">{{ this.title }}</label>
    </div>
    <button class="todo__item-remov" :id="this.id">X</button>
  </li>

</template>
