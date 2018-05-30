<template>
  <div class="hello">
    <banner/>
    <homelist/>
  </div>
</template>

<script>
import Banner from './banner/banner'
import Homelist from './homelist/Homelist'
export default {
  name: 'HelloWorld',
  components: { Homelist, Banner }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="less" >
h1, h2 {
  font-weight: normal;
}
.hello{
  padding: 0px;
  margin: 0px;
}

a {
  color: #42b983;
}
</style>
