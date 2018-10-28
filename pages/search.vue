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
  async mounted() {
    let self = this
    let {status, data: { list }} = await axios.get('/city/list')
    if (status === 200) {
      this.list = list
    }
  }
}
</script>

<style>
.page-search {
  color: green
}
</style>
