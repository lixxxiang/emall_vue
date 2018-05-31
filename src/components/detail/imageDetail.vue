<template>
  <div>
    <div class="title-div">
      <div class="tab">
        <a class="tab-item1">每日一图</a>
        <a class="tab-item2">发生位置</a>
      </div>
      <div class="title">
        <a class="imageName">{{message.imageName}}</a>
      </div>
      <div class="date">
        <a class="imageDate">每日一图 · {{message.imageDate.slice(5)}}</a>
      </div>
    </div>
    <div class="detail-div">
      <a>{{message.richText1}}</a>
      <!--<a>{{message.richText2}}</a>-->
      <!--<a>{{message.richText3}}</a>-->
    </div>
  </div>
</template>

<script>
import { Tab, TabItem } from 'vux'
import axios from 'axios'

var message = {}

export default {
  components: {
    Tab,
    TabItem
  },
  name: 'imageDetail',
  data () {
    return {
      imageId: this.$route.params.id,
      message
    }
  },
  mounted () {
    this.$nextTick(function () {
      console.log(this.imageId)
      var params = new URLSearchParams()
      var self = this
      params.append('imageId', this.imageId)
      axios.post('http://202.111.178.10:28085/mobile/getDailyPicDetail', params)
        .then(function (response) {
          self.message = response.data.data
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
  .title-div{
    background-color: #6299FF;
    width: 100%;
    height: 189px;
    margin: 0 auto;
    position: absolute;
  }
  .tab{
    width: 169px;
    height: 22px;
    margin:31px auto auto auto;
    /*background-color: #629900;*/
  }
  .tab-item1{
    float: left;
    color: #FFFFFF;
    font-size: 16px;
    position: relative;
    top: 50%;
    transform: translateY(-50%);
  }
  .tab-item2{
    float: right;
    color: #FFFFFF;
    font-size: 14px;
    position: relative;
    top: 50%;
    transform: translateY(-50%);
  }
  .title{
    /*background-color: #621900;*/
    margin:34px 17px 45px 17px;
    height: 57px;
    position: absolute;

  }
  .imageName{
    float: left;
    color: #FFFFFF;
    font-size: 16px;

  }
  .date{
    /*background-color: #629900;*/
    margin:101px 17px 18px 17px;
    height: 17px;
  }
  .imageDate{
    float: left;
    color: #FFFFFF;
    font-size: 14px;
  }
  .detail-div{
    background-color: #629900;
    position: absolute;
    margin:194px 17px 18px 17px;

  }
</style>
