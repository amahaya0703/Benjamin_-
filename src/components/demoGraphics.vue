<template>
<div>
  <table>
    <thead>
      <tr v-for="total in sortTotalyear" :key="total.year">
        <th>{{total.year}}</th>
        <th>{{total.value}}</th>
      </tr>
    </thead>
  </table>
</div>
</template>

<script>
export default {
  props: ["totals", "youngs", "workings", "olds"],
  data(year){
    return {
      total: [year]
    }
  },
  computed: {
    sortTotalyear() {
      return this.totals.slice().reverse();
    }
  }
}
</script>

<style scoped>
li{
  list-style: none;
  width: 264px;
  margin: 0 auto;
}
</style>
