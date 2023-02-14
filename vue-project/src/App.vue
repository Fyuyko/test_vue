<script setup>
  import InputComponent from "./components/InputComponent.vue";
  import ToDo from "./components/ToDo.vue";
</script>

<script>
  export default {
    methods: {
      onDataCollection (data) {
        this.text = data.text
      }
    }
  }
</script>

<template>

  <InputComponent :onDataCollection="onDataCollection"/>

  <ul id="todo" class="todo" >

    <ToDo :text="text" :id="1" completed="true"/>
<!--      v-for="item in items"
      :item="item"
      :title="item.title"
      :key="item.id"
    /> -->

  </ul>
</template>

