<template>
  <div class="list" ref="wrapper">
    <div>
    <div class="area">
      <div class="title border-topbottom">当前城市</div>
      <div class="button-list">
        <div class="button-wrapper">
          <div class="button">{{this.$store.state.city}}</div>
        </div>
      </div>
    </div>

    <div class="area">
      <div class="title border-topbottom">热门城市</div>
      <div class="button-list">
        <div class="button-wrapper" v-for="item of hotCities" :key="item.id" @click="handleCityClick(item.name)">
          <div class="button">{{item.name}}</div>
        </div>
      </div>
    </div>

    <div class="area" v-for="(item,key) of cities" :key="key" :ref="key">
      <div class="title border-topbottom">{{key}}</div>
      <div class="item-list">
        <div class="item border-bottom" v-for="innerItem of item" :key="innerItem.id" @click="handleCityClick(innerItem.name)">{{innerItem.name}}</div>
      </div>
    </div>

    </div>
  </div>
</template>
<style lang="stylus" scoped>
  @import '~styles/varibles.styl';
  .list {
    overflow: hidden;
    position: absolute;
    top: 1.58rem;
    left: 0;
    right: 0;
    bottom: 0;
  }
  .title {
    line-height: .44rem;
    background: #eeeeee;
    font-size: .26rem;
    padding-left: .2rem;
    color: #666666;
  }
  .button-list {
    overflow: hidden;
    padding: .1rem .6rem .1rem .1rem;
  }
  .button-wrapper {
    float: left;
    width: 33.33%;
    /*background: red;*/
  }
  .button {
    margin: .1rem;
    padding: .1rem;
    /*padding: .1rem 0;*/
    text-align: center;
    border-radius: .06rem;
    border: .02rem solid #cccccc;
  }
  .item-list {

  }
  .item {
    line-height: .54rem;
    padding-left:.2rem;
  }

</style>
<script>
  import Bscroll from 'better-scroll'
  export default {
    name: 'CityList',
    props: {
      hotCities:Array,
      cities: Object,
      letter:String
    },
    data () {
      return {msg: 'hello vue'}
    },
    mounted() {
      this.scroll = new Bscroll(this.$refs.wrapper)
    },
    watch: {
      letter() {
        if (this.letter) {
          console.log(this.letter)
          const element = this.$refs[this.letter][0]
          this.scroll.scrollToElement(element)
        }
      }
    },
  methods:{
    handleCityClick(city){
      this.$store.commit('changeCity',city)
      this.$router.push('/')
    }
  }
  }
</script>
