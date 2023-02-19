<template>

  <div class="checkbox-wrapper">
    <input :id="'checkbox' + this.id" type="checkbox" class="checkbox" :checked="this.completed" @change="checkedItem(this)">
    <label :for="'checkbox' + this.id">{{this.title}}</label>
  </div>
  <button class="todo__item-remove" :id="this.id" @click="deleteItem()">X</button>

</template>

<script>
  export default {
    props: ["title", "id", "completed", "onChecked", "onDeleted"],

    methods: {

      deleteItem() {
        this.onDeleted(this.id)
      },

      checkedItem(data) {
        if (data) {
          this.onChecked({
            id: this.id,
            checked: this.completed,
          })
        }
      },

    },

  }
</script>

<style scoped>

  .checkbox-wrapper {
    flex: 1;
  }

  .checkbox {
    margin-right: 10px;
    position: absolute;
    z-index: -1;
    opacity: 0;
  }

  label {
    display: inline-block;
    width: 100%;
  }

  .checkbox + label {
    position: relative;
    vertical-align: middle;
    padding: 0 0 0 30px;
    cursor: pointer;
  }

  .checkbox + label:before {
    content: "";
    position: absolute;
    top: 3px;
    left: 0;
    width: 9px;
    height: 9px;
    border: 2px solid #bfc6d0;
  }

  .checkbox + label:after {
    content: "";
    position: absolute;
  }

  .checkbox:checked + label {
    text-decoration: line-through;
  }

  .checkbox:checked + label:after {
    position: absolute;
    top: 7px;
    left: 4px;
    border-radius: 2px;
    background: #55b8ff;
    height: 5px;
    width: 5px;
  }

  .todo__item-remove {
    border: none;
    outline: none;
    background-color: #fff;
    cursor: pointer;
  }

</style>