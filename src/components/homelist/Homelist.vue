<template>
  <div>
    <ul class="ulclass">
      <li v-for="(a,i) in message" :key="i" class="liclass">
        <div class="style1_div" v-if="a.style == 1 && a.type == 1" @click="toImageDetail(a.contentId)">
          <div class="style1_img_div">
            <img :src="a.thumbnail1Path" class="style1_img">
          </div>
          <div class="style1_title">
            {{a.contentName}}
          </div>
          <div class="style1_date_div">
            每日一图 · {{a.contentDate.slice(5)}}
          </div>
        </div>

        <div class="style2_div" v-if="a.style == 2 && a.type == 1" @click="toImageDetail(a.contentId)">
          <div class="style2_title">
            {{a.contentName}}
          </div>
          <div class="style2_img_div">
            <img :src="a.thumbnail1Path" class="style2_img">
            <img :src="a.thumbnail2Path" class="style2_img">
            <img :src="a.thumbnail3Path" class="style2_img">
            <!--<img v-show="a.thumbnail3Path.length != 0" :src="a.thumbnail3Path" class="style2_img">-->
          </div>
          <div class="style2_date_div">
            每日一图 · {{a.contentDate.slice(5)}}
          </div>
        </div>

        <div class="type2_div" v-if="a.type == 2">
          <div class="type2_title">
            {{a.contentName}}
          </div>
          <div class="video_img_div">
            <img :src="a.thumbnail1Path" class="video_img">
          </div>
          <div class="type2_date_div">
            脉动地球 · {{a.contentDate.slice(5)}}
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
  },
  methods: {
    toImageDetail (contentId) {
      console.log(contentId)
      this.$router.push('../detail/imageDetail')
    }
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

  .style2_div {
    margin: 14px 18px;
    height: 211px;
    border-bottom: solid 1px #ECECEC;

  }

  .style1_div {
    margin: 14px 18px;
    height: 138px;
    border-bottom: solid 1px #ECECEC;

  }

  .imgclass {
    width: 100px;
    height: 100px;
  }

  .style2_img {
    margin-top: 14px;
    height: 110px;
    float: left;
    width: 32.3%;
    border-radius: 5px;
    margin-right: 2.5px;
  }

  .video_img {
    margin-top: 14px;
    height: 169px;
    float: left;
    border-radius: 5px;
    width: 100%;
    margin-right: 5px;
  }

  .type2_title {
    margin: 14px 18px;
  }

  .type2_div {
    margin: 14px 18px;
    height: 271px;
    border-bottom: solid 1px #ECECEC;
  }

  .style2_img_div {
  }

  .style1_title {
    margin-top: 28px;
    margin-left: 149px;
    margin-bottom: 14px;
  }

  .style1_date_div {
    margin-left: 149px;
    margin-top: 10px;

  }

  .style1_img {
    margin-top: 14px;
    height: 110px;
    width: 110px;
    border-radius: 5px;
    float: left;
  }

  .style2_title {
    margin-left: 0px;
  }

  .style1_img_div {
    float: left;
    margin-top: 0px;

  }

  .style2_date_div {
    margin-left: 0px;
  }

</style>
