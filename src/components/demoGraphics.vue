<template>
  <div>
    <table>
      <div class="wrapper">
        <tbody class="total">
              <p>{{TotalLabel}}</p>
        <tr v-for="(total,index) in TotalSortData" :key="`total-${total.year}`">
          <th>{{total.year}}</th>
          <th>{{total.value}}</th>
          <th>{{ Math.round(TotalSortData[index+1]?.value/TotalSortData[index]?.value*100)}}%</th>
        </tr>
        </tbody>
        <tbody class="young">
          <p>{{YoungLabel}}</p>
        <tr v-for="young in YoungSortData" :key="`young-${young.year}`">
          <th>{{young.year}}</th>
          <th>{{young.value}}</th>
          <th>{{young.rate}}%</th>
        </tr>
        </tbody>
        <tbody class="production">
          <p>{{ProductionLabel}}</p>
        <tr v-for="production in ProductionSortData" :key="`working-${production.year}`">
          <th>{{production.year}}</th>
          <th>{{production.value}}</th>
          <th>{{production.rate}}%</th>
        </tr>
        </tbody>
        <tbody class="old">
          <p>{{OldLabel}}</p>
        <tr v-for="old in OldSortData" :key="`old-${old.year}`">
          <th>{{old.year}}</th>
          <th>{{old.value}}</th>
          <th>{{old.rate}}%</th>
        </tr>
        </tbody>
      </div>
    </table>
  </div>
</template>


<script>
export default {
  props: ["Population"],
  computed: {
    TotalLabel() {
      return this.Population[0]?.label;
    },
    YoungLabel() {
      return this.Population[1]?.label;
    },
    ProductionLabel() {
      return this.Population[2]?.label;
    },
    OldLabel() {
      return this.Population[3]?.label;
    },
    TotalSortData() {
     return this.Population[0]?.data.slice().reverse();
    },
    YoungSortData() {
     return this.Population[1]?.data.slice().reverse();
    },
    ProductionSortData() {
     return this.Population[2]?.data.slice().reverse();
    },
    OldSortData() {
     return this.Population[3]?.data.slice().reverse();
    }
  }
}
</script>

<style scoped>
.wrapper{
  display: flex;
  margin: 0 auto;
  width: 0rem;
}
table{
  display: grid;
  grid-template-columns: 3fr 3fr 3fr 3fr;
}
th{
  padding-right: 30px;
}
</style>
