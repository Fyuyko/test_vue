<template>
  <a href="#" @click.prevent="sort(this.item)">
    {{ this.item.title }}
  </a>
</template>

<script>
export default {
  name: "TodoSortItemComponent",

  props: ["item", "onCompleted"],

  methods: {
    sort(data) {
      this.onCompleted(data.name);
    }
  }

}
</script>

<style scoped>
  a {
    display: inline-block;
    padding: 10px 20px;
    width: 100%;
    color: black;

    transition: all linear .3s;
  }

  a:hover {
    background-color: rgba(0, 0, 0, 10%);
  }
</style>