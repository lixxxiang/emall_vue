<template>
  <div>
    <div class="title">
      <div class="tab">
        <a class="tab-item1">每日一图</a>
        <a class="tab-item2">发生位置</a>
      </div>
    </div>
  </div>
</template>

<script>
import { Tab, TabItem } from 'vux'
export default {
  components: {
    Tab,
    TabItem
  },
  name: 'imageDetail'
}
</script>

<style scoped lang="less" rel="stylesheet/less">
  .title{
    background-color: #6299FF;
    width: 100%;
    height: 189px;
    position: absolute;
  }
  .tab{
    width: 169px;
    height: 22px;
    margin:31px auto auto auto;
    background: #f2056e;
  }
  .tab-item1{
    margin: ;
  }
</style>
