<template>
    <div class='page-search'>
        page is search
        <ul>
            <li v-for="(item, index) in list" :key="index">{{item}}</li>
        </ul>
    </div>
</template>

<script>
import axios from 'axios'
export default {
  layout: 'search',
  data() {
    return {
      list: []
    }
  },
  // async mounted() {    //  浏览器端处理组件的方式
  //   let self = this
  //   let {status, data: { list }} = await axios.get('/city/list')
  //   if (status === 200) {
  //     this.list = list
  //   }
  // },
  async asyncData() { //  服务器端渲染组件的方式
    let {status, data: { list }} = await axios.get('http://localhost:3000/city/list')
    if (status === 200) {
      return {
        list
      }
    }
  }
  // async fetch() {    //  用于处理vuex的数据
  //   let {status, data: { list }} = await axios.get('http://localhost:3000/city/list')
  //   if (status === 200) {
  //     return {
  //       list
  //     }
  //   }
  // }
}
</script>

<style>
.page-search {
  color: green
}
</style>
