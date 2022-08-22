<template>
  <div>
    <h2>都道府県一覧</h2>
    <Prefectures :prefPosts="posts"></Prefectures>
  </div>
</template>

<script>
const apiUrl = "https://opendata.resas-portal.go.jp/api/v1/prefectures"
const apiKey = "nyB4LKskiLFNzAYzdoIcbnaovQkWIvATq6O9GOCc"
const config = {
  headers: {
    'Content-Type': 'application/json',
    'x-api-key': apiKey
  }
};
import Prefectures from "./components/Prefectures.vue";
import axios from "axios";



export default {
  data() {
    return {
      posts: []
    }
  },
  components: {
    Prefectures
  },
  created() {
    axios.get(apiUrl, config)
      .then(response => {
        this.posts = response.data.result;
    })
  }
}
</script>
