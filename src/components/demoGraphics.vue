<template>
  <div>
    <table>
      <div class="total">
        <tbody>
          <tr>
          <td>総人口</td>
        </tr>
        </tbody>
        <thead>
          <tr v-for="total in totalSort " :key="`total-${total.year}`">
          <th>{{total.year}}</th>
          <th>{{total.value}}</th>
          <th>{{test}}</th>
        </tr>
        </thead>
      </div>
      <div class="young">
         <tbody>
           <tr>
          <td>年少人口</td>
        </tr>
        </tbody>
        <thead>
          <tr v-for="young in youngSort " :key="`young-${young.year}`">
          <th>{{young.value}}</th>
          <th>{{young.rate}}</th>
        </tr>
        </thead>
      </div>
      <div class="working">
        <tbody>
        <tr>
          <td>生産年齢人口</td>
        </tr>
        </tbody>
        <thead>
          <tr v-for="working in workingSort " :key="`working-${working.year}`">
          <th>{{working.value}}</th>
          <th>{{working.rate}}</th>
        </tr>
        </thead>
      </div>
      <div class="old">
        <tbody>
          <tr>
          <td>老年人口</td>
        </tr>
        </tbody>
        <thead>
          <tr v-for="old in oldSort " :key="`old-${old.year}`">
          <th>{{old.value}}</th>
          <th>{{old.rate}}</th>
        </tr>
        </thead>
      </div>
    </table>
  </div>
</template>

<script>
export default {
  props: ["totals", "youngs", "workings", "olds"],
  computed: {
    totalSort() {
      return this.totals.slice().reverse();
    },
    youngSort() {
      return this.youngs.slice().reverse();
    },
    workingSort() {
      return this.workings.slice().reverse();
    },
    oldSort() {
      return this.olds.slice().reverse();
    },
    test() {
      for (let i = 0; i < this.totalSort.length; i++) {
        return this.totalSort[i + 1].value / this.totalSort[i].value * 100;
      }
    }
  }
  }
</script>

<style scoped>
table{
  display: grid;
  grid-template-columns: 3fr 3fr 3fr 3fr;
}
th{
  padding-right: 30px;
}
.total,.young,.working,.old{
  display: flex;
  margin-bottom: 30px;
}
</style>
