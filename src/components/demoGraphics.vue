<template>
  <div>
    <table>
      <div>
        <p>TEST</p>
        <tbody>
            <tr v-for="(test,index) in ama" :key="test.label">
            <th>{{index}}</th>
            <th>{{test}}</th>
          <th>{{test.label}}</th>
          <th>{{test.data}}</th>
          <th>{{testSort}}</th>
        </tr>
        </tbody>
      </div>
    </table>
  </div>
</template>



<script>
export default {
  props: ["totals", "youngs", "workings", "olds", "testTests"],
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
    ama() {
      return this.testTests.slice().reverse();
    },
    testSort() {
      this.testTests.forEach(test => {
        const texts = Object.values(test);
        texts[1].forEach((value, index, array) => {
          Object.keys(array[index]).forEach((key) => {
            return array[index + 1].value / array[index].value * 100;
          });
        });
      });
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
