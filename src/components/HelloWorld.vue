<template>
  <div class="hello">
    <banner/>
    <!--<transition enter-active-class="bounceInLeft" leave-active-class="bounceOutRight">-->
      <!--<ul class="newsContent animated" v-show="!loading&&ifReturnMsg">-->
    <ul class="ulclass">
        <!--<router-link-->
          <!--v-for="(val,index) in listCon"-->
          <!--:to="{-->
                    <!--name:'newsdetail',-->
                    <!--params:-->
                        <!--{   id:val.tag_id,-->
                            <!--title:val.title,-->
                            <!--media_info:val.media_info,-->
                            <!--media_name:val.media_name,-->
                            <!--datetime:val.datetime,-->
                            <!--abstract:val.abstract,-->
                            <!--image_list:val.image_list,-->
                            <!--repin_count:val.repin_count,-->
                            <!--comment_count:val.comment_count,-->
                            <!--keywords:val.keywords-->
                        <!--}-->
                <!--}"-->

          <!--class="newsDetaile"-->
          <!--:key="index">-->
          <!--<p class="title">{{val.title}}</p>-->
      <li v-for="a in res2" :key="a" class="liclass">
        {{a}}
      </li>

      <!--<div>-->
            <!--<img alt="加载出错" v-for="(img,index) in val.image_list" :key="index" v-lazy="img.url">-->
            <!--<div class="bottomInfo clearfix">-->
              <!--<Icon type="fireball" size="10" color="#d43d3d" v-show="val.hot===1"></Icon>-->
              <!--<span class="avIcon" v-show="val.label==='广告'">广告</span>-->
              <!--<span class="writer">{{val.media_name}}</span> &nbsp;&nbsp;-->
              <!--<span class="comment_count">评论&nbsp;{{val.comment_count}}</span>-->
              <!--<span class="datetime">{{val.datetime|date}}</span>-->
            <!--</div>-->
          <!--</div>-->
        <!--</router-link>-->
      </ul>
    <!--</transition>-->
  </div>
</template>

<script>
import Banner from './banner/banner'
import axios from 'axios'
export default {
  name: 'HelloWorld',
  components: { Banner },
  data () {
    var res = ''
    var params = new URLSearchParams()
    params.append('pageSize', '10')
    params.append('pageNum', '1')
    axios.post('http://202.111.178.10:28085/mobile/homePage', params)
      .then(function (response) {
        res = response.data
        console.log(res)
      })
      .catch(function (response) {
        console.log(response)
      })
    var res2 = ['1', '2', '3']
    return {
      res2
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="less" >
h1, h2 {
  font-weight: normal;
}
/*ul {*/
  /*list-style-type: none;*/
  /*padding: 0;*/
/*}*/
/*li {*/
  /*display: inline-block;*/
  /*margin: 0 10px;*/
/*}*/
li{
  list-style-type: none;
}
a {
  color: #42b983;
}

/*.ulclass {*/
  /*width: 100%;*/
  /*overflow: hidden;*/
  /*overflow-x: auto;*/
  /*text-align: center;*/
  /*position: fixed;*/
  /*left: 0;*/
  /*font-size: 0;*/
  /*top: 1.2rem;*/
  /*background: #f4f5f6;*/
  /*font-family: '微软雅黑';*/
  /*white-space: nowrap;*/
  /*z-index: 999;*/
  /*.liclass {*/
    /*display: inline-block;*/
    /*height: 1rem;*/
    /*line-height: 1rem;*/
    /*width: 1.4rem;*/
    /*font-size: 16px;*/
    /*a {*/
      /*color: #000;*/
      /*}*/
  /*}*/
/*}*/
</style>
