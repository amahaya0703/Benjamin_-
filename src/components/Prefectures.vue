<template>
  <div class="app">
    <ul>
      <li v-for="prefPost in prefPosts" :key="prefPost.prefName">
      <label for="pref">
        <input
        type="checkbox"
        id="pref"
        v-model="eventData.target"
        >
        {{prefPost.prefName}}
      </label>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: ["prefPosts"],
  data() {
    return {
      eventData: {
        target: []
      }
    }
  }


}
</script>


<style scoped>

.app{
  margin: 0 auto;
  width: 250px;
}

ul{
  padding-left: 0px;
  display: grid;
  grid-template-columns: 3fr 3fr 3fr 3fr;
}

li{
  list-style: none;
  width: 100px;
  margin: 0 auto;
}
</style>
