<template>
  <div class="swiper-container">
    <div class="swiper-wrapper">
      <div class="swiper-slide" v-for="str in images" :key="str" :style="{ backgroundImage: 'url(' + str + ')' }"></div>
    </div>
    <div class="swiper-pagination swiper-pagination-white"></div>
  </div>
</template>

<script>
import Swiper from 'swiper'
import axios from 'axios'
import 'swiper/dist/css/swiper.min.css'
export default {
  name: 'banner',
  data () {
    var images = []
    axios.get('http://202.111.178.10:28085/mobile/homePageSlide')
      .then(function (response) {
        for (var j = 0; j < response.data.data.length; j++) {
          images.push(response.data.data[j].imageUrl)
        }
        console.log(images)
      })
      .catch(function (response) {
        console.log(response)
      })
    return {
      images
    }
  },
  mounted () {
    var swiper = new Swiper('.swiper-container', {
      pagination: '.swiper-pagination',
      paginationClickable: true,
      loop: true,
      speed: 600,
      autoplay: true,
      observer: true, // 修改swiper自己或子元素时，自动初始化swiper
      observeParents: false, // 修改swiper的父元素时，自动初始化swiper
      onTouchEnd: function () {
        swiper.update()
        swiper.startAutoplay()
        swiper.reLoop()
      }
    })
  }
}
</script>

<style lang="less">
  .swiper-container {
    width: 100%;
    height: 10rem;
  .swiper-wrapper {
    width: 100%;
    height: 100%;
    transition-timing-function:linear !important;
  }
  .swiper-slide {
    background-position: center;
    background-size: cover;
    width: 100%;
    height: 100%;
  img {
    width: 100%;
    height: auto;
  }
  }
  .swiper-pagination-bullet {
    width:0.833rem;
    height: 0.833rem;
    display: inline-block;
    background: #7c5e53;
  }
  }
</style>
