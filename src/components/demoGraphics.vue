<template>
  <div>
    <table>
      <div>
        <p>TEST</p>
        <tbody>
            <p>{{testlabel}}</p>
            <tr v-for="(test,index) in testSortData" :key="test.year">
            <th>{{index}}</th>
            <th>{{test.year}}</th>
            <th>{{test.value}}</th>
            <th>{{ Math.round(testSortData[index+1]?.value/testSortData[index]?.value*100)}}%</th>
        </tr>
        </tbody>
      </div>
    </table>
  </div>
</template>


<script>
export default {
  props: ["testTests"],
  computed: {
    testlabel() {
      return this.testTests[0]?.label;
    },
    testSortData() {
     return this.testTests[0]?.data.slice().reverse();
    }//,
    // amahaya() {
    //    this.testTests[0]?.data.forEach((value, index, array) => {
    //     array.map(val => {
    //       return val.value;
    //     })
    //   });
    // }
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
