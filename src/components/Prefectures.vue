<template>
  <div class="app">
    <ul>
      <li v-for="prefPost in prefPosts" :key="prefPost.id">
      <label :for="prefPost.id">
        <input
        type="checkbox"
        :id="prefPost.id"

        v-model="prefPost.isChecked"
        :value="prefPost.name"
        @change="table(prefPost.id, prefPost.name)"
        >
        {{prefPost.name}}
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
      isChecked: true
    }
  },
  methods: {
    table(id, name) {
  this.$emit("on-table",id,name);

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
