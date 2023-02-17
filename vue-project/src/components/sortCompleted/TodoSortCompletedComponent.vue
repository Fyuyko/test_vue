<template>
  <div class="sort">

    <div class="sort__header">
      Все элементы
    </div>
    <ul class="sort__list">

      <li class="sort__list-item" v-for="sortItem in this.sortList" >
        <TodoSortItemComponent :item="sortItem" :onCompleted="this.onCompleted"/>
      </li>

    </ul>
  </div>
</template>

<script>
import TodoSortItemComponent from "./TodoSortCompletedItemComponent.vue";

export default {
  name: "TodoSortComponent",

  components: {TodoSortItemComponent},

  props: ["onSort", "onCompleted"],

  data() {
    return {
      sortList: [
        {
          name: "all",
          title: "Все элементы",
        },
        {
          name: "completed",
          title: "Завершенные задачи",
        },
        {
          name: "uncompleted",
          title: "Не завершенные задачи",
        },
      ],
    }
  },

  methods: {

  }

}
</script>

<style scoped>
  .sort {
    position: relative;
  }

  .sort__header {
    padding-bottom: 10px;
    cursor: pointer;
  }

  .sort__list {
    position: absolute;
    bottom: 0;
    left: 0;
    transform: translateY(100%);

    max-height: 0;
    background: white;
    z-index: 1;

    transition: max-height linear .3s;
    overflow: hidden;

    pointer-events: none;
    padding: 0;
  }
  .sort:hover .sort__list {
    max-height: 500px;
    box-shadow: 0 5px 5px 4px rgb(0 0 0 / 10%);
    pointer-events: all;
  }

  .sort__list-item {
    list-style: none;
  }

</style>