<template>
  <div class="app">
    <ul>
      <li v-for="prefPost in prefPosts" :key="prefPost.id">
      <label :for="prefPost.id">
        <input
        type="checkbox"
        :id="prefPost.id"
        :checked="prefPost.isChecked"
        :value="prefPost.name"
        v-model="eventData.target"
        >
        {{prefPost.name}}
      </label>
      </li>
      <p>{{eventData.target}}</p>
    </ul>
  </div>
</template>

<script>

export default {
  props: ["prefPosts"],
  data() {
    return {
      eventData: {
        target: [],
        tests:[]
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
