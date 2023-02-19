<template>
  <div class="statistic">
    <div>
      всего: {{this.data.length}}
    </div>
    <div>
      выполнено: {{this.addStatistic().completed}}
    </div>
    <div>
      не выполнено: {{this.addStatistic().uncompleted}}
    </div>
  </div>
</template>

<script>
export default {
  name: "TodoStatisticComponent",

  props: ["data"],

  methods: {

    addStatistic() {
      let completed = 0;
      let uncompleted = 0;
      this.data.forEach(dataItem => {
        if (dataItem.completed) {
          completed ++;
        } else {
          uncompleted ++
        }
      })
      return {
        completed,
        uncompleted
      }
    },

  },

}
</script>

<style scoped>
  .statistic {
    display: flex;
    flex-direction: column;
  }

</style>