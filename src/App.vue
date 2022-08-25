<template>
  <div>
    <h2>都道府県一覧</h2>
    <Prefectures :prefPosts="posts" @on-table="Diagram"></Prefectures>
    <ul>
      <li v-for="totalpopu in totalpopus " :key="totalpopu.year">{{totalpopu}}</li>
    </ul>
    <!-- <Prefectures></Prefectures>
    <Prefectures></Prefectures>
    <Prefectures></Prefectures>
    <Prefectures></Prefectures> -->
  </div>
</template>

<script>
import Prefectures from "./components/Prefectures.vue";
import axios from "axios";

export default {
  data() {
    return {
      posts: [],
      totalpopus:[],
      youngpopus: [],
      workingpopus: [],
      oldpous:[]
    }
  },
  components: {
    Prefectures
  },
  created() {
    const populationUrl = `https://opendata.resas-portal.go.jp/api/v1/population/composition/perYear?prefCode=1`
    const apiUrl = "https://opendata.resas-portal.go.jp/api/v1/prefectures"
    const apiKey = "nyB4LKskiLFNzAYzdoIcbnaovQkWIvATq6O9GOCc"
    const config = {
      headers: {
        'Content-Type': 'application/json',
        'x-api-key': apiKey
      }
    };

    axios.get(apiUrl, config)
      .then(response => {
        this.posts = response.data.result.map(val => {
          return {
            id: val["prefCode"],
            name: val["prefName"],
            isChecked: false
          };
        });
      }),

      axios.get(populationUrl, config)
      .then(response => {
         // 総人口

        this.totalpopus = response.data.result.data[0].data.map(val => {
          return {
            year: val["year"],
            value: val["value"]
          };
        });
        // 年少人口
        this.youngpopus = response.data.result.data[1].data.map(val => {
          return {
            year: val["year"],
            value: val["value"],
            rate: val["rate"]
          };
        });
        // 生産年齢人口
        this.workingpopus = response.data.result.data[2].data.map(val => {
          return {
            year: val["year"],
            value: val["value"],
            rate: val["rate"]
          };
        });
        // 老年人口
        this.oldpous = response.data.result.data[3].data.map(val => {
          return {
            year: val["year"],
            value: val["value"],
            rate: val["rate"]
          };
        });
      })
  },
  methods: {
    Diagram(value) {
      console.log(value);
      this.posts = value
    }
  }
}
</script>
