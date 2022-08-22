<template>
  <div>
    <h2>都道府県一覧</h2>
  </div>
</template>

<script>
const apiUrl = "https://opendata.resas-portal.go.jp/api/v1/prefectures"
const apiKey = "nyB4LKskiLFNzAYzdoIcbnaovQkWIvATq6O9GOCc"
const config = {headers: {
    'Content-Type': 'application/json',
    'x-api-key': apiKey
}}

import axios from "axios";
export default {
  data() {
    return {
      result:[]
    }
  },
  created() {
    axios.get(apiUrl, config)
      .then(response => {
        this.result = response.data.result;
    })
  }
}
</script>

<style>

</style>
