<template>
  <div>
    <ul class="ulclass">
      <li v-for="(a,i) in message" :key="i" class="liclass">
        <div class="style1_div" v-if="a.style == 1">
          <div class="style1_title">
            {{a.contentName}}
          </div>
          <img :src="a.thumbnail1Path" class="style1_img">
        </div>
        <div class="style2_div" v-if="a.style == 2">
          <div>
            {{a.contentName}}
          </div>
          <div class="imgdiv">
            <img :src="a.thumbnail1Path" class="imgclass1">
            <img :src="a.thumbnail2Path" class="imgclass1">
            <img :src="a.thumbnail3Path" class="imgclass1">
            <!--<img v-if="a.thumbnail3Path.length != 0" :src="a.thumbnail3Path" class="imgclass1">-->
          </div>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios'

var message = {}
export default {
  name: 'home_list',
  data () {
    return {
      message
    }
  },
  mounted () {
    this.$nextTick(function () {
      console.log('ffdfdfd')
      var params = new URLSearchParams()
      var self = this
      params.append('pageSize', '10')
      params.append('pageNum', '1')
      axios.post('http://202.111.178.10:28085/mobile/homePage', params)
        .then(function (response) {
          self.message = response.data.data.MixedContentList
          console.log(self.message)
        })
        .catch(function (response) {
          console.log(response)
        })
    })
  }
}
</script>

<style scoped lang="less" rel="stylesheet/less">
  .ulclass {
    margin: 0px;
    padding: 0px;
  }

  .liclass {
    list-style: none;
    text-align: left;
    margin: 0px;
  }

  .style2_div{
    margin: 14px 18px;
  }
  .style1_div{
    margin: 14px 18px;
    vertical-align: middle;
  }
  .imgclass {
    width: 100px;
    height: 100px;
  }
  .imgclass1{
    margin-top: 14px;
    height: 110px;
    float: left;
    width: 31.3%;
    margin-right: 5px;
    border-bottom: solid 1px #ECECEC;

  }
  .imgdiv{
    border: 1px black;
    zoom: 1;
    width: 100%;

  }
  .style1_title{
    float: right;
    margin-top: 14px;
    margin-left: 21px;
  }
  .style1_img{
    margin-top: 14px;
    height: 110px;
    width: 110px;
    float: left;
  }

</style>
