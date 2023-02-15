<script>
  export default {
    props: ["title", "id", "completed", "onDeleteItem", "onChecked"],

    data() {
      return {
        id: this.id,
        title: this.title,
        completed: this.completed,
      }
    },

    methods: {
      completedCheck(data) {
        return data ? "checked" : "";
      },

      deleteItem() {
        this.onDeleteItem({
          idDel: this.id,
        })
      },

      checked(checkboxItem) {
        if (checkboxItem.checked) {
          this.onChecked({
            idCheck: this.id,
          })
        }
      }
    }

  }
</script>

<template>

  <li class="todo__item show" :class="completedCheck(this.completed)">
    <div class="checkbox-wrapper">
      <input :id="'checkbox' + this.id" type="checkbox" class="checkbox" :checked="this.completed" @change="checked(this)">
      <label :for="'checkbox' + this.id">{{this.title}}</label>
    </div>
    <button class="todo__item-remov" :id="this.id" @click="deleteItem()">X</button>
  </li>

</template>
