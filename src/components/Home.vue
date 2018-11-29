<template>
  <div v-loading="loading">
    <p>{{info}}</p>
    <el-row>
      <el-col :span="4">

      </el-col>
      <el-col :span="16" offset="4">
        <home-list v-for="item in tableData"
                   v-bind:key="item.uid"
                   v-bind:item="item"></home-list>
      </el-col>
      <el-col :span="4">
          <el-button icon="el-icon-refresh" v-on:click="regreshClick"></el-button>
      </el-col>
    </el-row>
  </div>
</template>

<script>
// import HomeList form '@/components/child/HomeList'
import HomeList from './child/HomeList.vue'
const axios = require('axios')
export default {
  name: 'home',
  components: {
    HomeList
  },
  data () {
    return {
      loading: true,
      page: 1,
      info: null,
      tableData: [],
      cancheData: []
    }
  },
  mounted () {
    this.getData()
  },
  methods: {
    regreshClick: function () {
      this.page++
      this.getData()
    },
    getData: function () {
      var _this = this
      axios.get('https://www.apiopen.top/satinGodApi?type=1&page=' + _this.page)
        .then(response => {
          _this.cancheData = response.data.data
          // _this.tableData = _this.cancheData
          if (_this.tableData.length === 0) {
            _this.tableData = _this.cancheData
          } else {
            _this.cancheData.forEach(element => {
              _this.tableData.unshift(element)
            })
          }
          _this.info = '' + _this.tableData.length
          _this.loading = false
        })
        .catch(error => {
          console.log(error)
          _this.info = error
          _this.loading = false
        })
        .finally(function () {
          _this.loading = false
        })
    }
  }
}
</script>

<style>
</style>
