<template>
  <div>
    <table>
      <div>
        <p>TEST</p>
        <tbody>
            <tr v-for="(test,index) in testSort" :key="test.label">
            <th>{{index}}</th>
            <th>{{test}}</th>
            <th>{{test.label}}</th>
            <th>{{test.data}}</th>
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
    testSort() {
      console.log(this.testTests[0]?.data);
      console.log(this.testTests[0]);
     return this.testTests.slice().reverse();
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
