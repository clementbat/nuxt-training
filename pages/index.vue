<template>
  <section class="container">
    <div>
      <div class="chart">
        <bar-chart 
          :labels=labels
          :data=data
        />
      </div>
      <h1 class="title">
        Chart test with NUXT
      </h1>
      {{ title }}
      <h2 class="subtitle">
        Nuxt.js project
      </h2>    
    </div>
  </section>
</template>

<script>
import axios from 'axios'
import barChart from '~/components/barChart.vue'

export default {
  components: {
    barChart
  },
  async asyncData (context) {
    let { data } = await axios.get(`https://jsonplaceholder.typicode.com/posts/1`)
    return { 
      title: data.title,
      labels: ["Red", "Blue", "Yellow", "Green", "Purple", "Orange"],
      data: [12, 19, 3, 5, 2, 3]
    }
  }
}
</script>

<style>
.container {
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: "Quicksand", "Source Sans Pro", -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif; /* 1 */
  display: block;
  font-weight: 300;
  font-size: 50px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}
</style>
