<script setup>
  import InputComponent from "./components/InputComponent.vue";
  import ToDo from "./components/ToDo.vue";
</script>

<template>

  <InputComponent />

  <ul id="todo" class="todo">

    <ToDo />
<!--      v-for="item in items"
      :item="item"
      :title="item.title"
      :key="item.id"
    /> -->

  </ul>
</template>

