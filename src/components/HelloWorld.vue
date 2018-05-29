<template>
  <div class="hello">
    <banner/>
    <transition enter-active-class="bounceInLeft" leave-active-class="bounceOutRight">
      <ul class="newsContent animated" v-show="!loading&&ifReturnMsg">
        <router-link
          v-for="(val,index) in listCon"
          :to="{
                    name:'newsdetail',
                    params:
                        {   id:val.tag_id,
                            title:val.title,
                            media_info:val.media_info,
                            media_name:val.media_name,
                            datetime:val.datetime,
                            abstract:val.abstract,
                            image_list:val.image_list,
                            repin_count:val.repin_count,
                            comment_count:val.comment_count,
                            keywords:val.keywords
                        }
                }"

          class="newsDetaile"
          :key="index"
        >
          <p class="title">{{val.title}}</p>
          <div>
            <img alt="加载出错" v-for="(img,index) in val.image_list" :key="index" v-lazy="img.url">
            <div class="bottomInfo clearfix">
              <Icon type="fireball" size="10" color="#d43d3d" v-show="val.hot===1"></Icon>
              <span class="avIcon" v-show="val.label==='广告'">广告</span>
              <span class="writer">{{val.media_name}}</span> &nbsp;&nbsp;
              <span class="comment_count">评论&nbsp;{{val.comment_count}}</span>
              <span class="datetime">{{val.datetime|date}}</span>
            </div>
          </div>
        </router-link>
      </ul>
    </transition>
  </div>
</template>

<script>
import Banner from './banner/banner'
export default {
  name: 'HelloWorld',
  components: { Banner },
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
