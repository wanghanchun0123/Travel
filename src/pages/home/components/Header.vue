<template>
  <div class="header">
    <div class="header-left"><div class="iconfont back-icon">&#xe624;</div></div>
    <div class="header-input"><span class="iconfont">&#xe632;</span> 输入城市/景点</div>
    <router-link to="/city">
    <div class="header-right">
      {{this.$store.state.city}}
      <span class="iconfont arrow-icon">&#xe60a;</span>
    </div>
    </router-link>
  </div>
</template>
<style lang="stylus" scoped>
@import '~styles/varibles.styl';
.header {
  display: flex;
  line-height:.86rem;
  background: $bgColor;
  color: #ffffff;
}
.header-left {
  width: .64rem;
  float: left;
}
 .back-icon {
   text-align: center;
   font-size: .4rem;
 }
.header-right {
  min-width: 1.04rem;
  float: right;
  padding: 0 .1rem;
  text-align: center;
  color: #ffffff;
}
 .arrow-icon {
   font-size: .24rem;
 }
.header-input {
  flex: 1;
  background: #ffffff;
  border-radius:.1rem;
  margin-top: .12rem;
  line-height: .64rem;
  margin-left: .2rem;
  padding-left: .2rem;
  color: #cccccc;
  height: .64rem;
}
</style>
<script>
export default {
  name: 'HomeHeader',
  props:{
    city:String
  }
}
</script>
