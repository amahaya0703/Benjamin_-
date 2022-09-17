<template>
  <div>
    <h2>都道府県一覧</h2>
    <Prefectures
    :prefPosts="posts"
    @on-table="Diagram"
    >
    </Prefectures>
    <demoGraphics
    :testTests="tests"
    ></demoGraphics>
  </div>
</template>

<script>
import demoGraphics from "./components/demoGraphics.vue";
import Prefectures from "./components/Prefectures.vue";
import axios from "axios";

const apiUrl = "https://opendata.resas-portal.go.jp/api/v1/prefectures"
const apiKey = "nyB4LKskiLFNzAYzdoIcbnaovQkWIvATq6O9GOCc"
const config = {
      headers: {
        'Content-Type': 'application/json',
        'x-api-key': apiKey
      }
    };

 export default {
  data() {
    return {
      posts: [],
      tests:[]
    }
  },
  components: {
    Prefectures,
    demoGraphics
  },
  created() {
    axios.get(apiUrl, config)
      .then(response => {
        this.posts = response.data.result.map(val => {
          return {
            id: val["prefCode"],
            name: val["prefName"],
            isChecked: false
          };
        });
      })
  },
  methods: {
    Diagram(value) {
      axios.get(`https://opendata.resas-portal.go.jp/api/v1/population/composition/perYear?prefCode=${value}`, config)
        .then(response => {

          this.tests = response.data.result.data.map(val => {
            return {
              label: val["label"],
              data: val["data"].map(val => {
                return {
                  year: val["year"],
                  value: val["value"],
                  rate: val["rate"]
                }
              })
            };
          });
        });
    }
  }
}
</script>

<!-- for soujinkouArray{
  // 今回
  const base = soujinkouArray[i]
  // 前回
  const prev = soujinkouArray[i - 1]
  const zoukaRate = base / prev * 100
}


. の前に?をつける事でudifundを無視できる。 -->
