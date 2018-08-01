<template>
  <div class="default text-dark">
    <h1 class="text-red">语法</h1>
    <!-- 主key -->  
    <div class="lh-28 flex-container top left">
      <strong v-text="datas.name"></strong>
      <div class="flex1">
        <span class="paddingh10 borderl lh-14" v-for="item in datas.key">
          <span v-text="item.name"></span><i class="baseIcon-CSS3 text-red" v-show="item.css3"></i>
        </span>
      </div>
      
    </div>
    <!-- 默认值 -->
    <div class="lh-28 flex-container top left">
      <strong>默认值</strong>
      <span class="marginh10" v-text="datas.default"></span>
    </div>
    <!-- 适用于 -->
    <div class="lh-28 flex-container top left">
      <strong>适用于</strong>
      <div class="flex1">
        <span class="paddingh10 borderl lh-14" v-for="item in datas.apply">
          <span v-text="item"></span>
        </span>
      </div>
      
    </div>
    <!-- 继承性 -->
    <div class="lh-28 flex-container top left">
      <strong>继承性</strong>
      <span class="paddingh10 borderl" v-text="datas.succession == '' ? '无' : datas.succession">
      </span>
    </div>
    <!-- 动画性 -->
    <div class="lh-28 flex-container top left">
      <strong>动画性</strong>
      <span class="paddingh10 borderl" v-text="datas.animated ? datas.animated : '否'">
      </span>
    </div>
    <!-- 计算值 -->
    <div class="lh-28 flex-container top left">
      <strong>计算值</strong>
      <span class="paddingh10 borderl" v-html="datas.calculated">
      </span>
    </div>
    <!-- 媒体 -->
    <div class="lh-28 flex-container top left">
      <strong>媒体</strong>
      <span class="paddingh10 borderl" v-text="datas.media">
      </span>
    </div>

    <h1 class="margint30 text-red">取值</h1>
    <div v-for="item in datas.key" class="margint10 flex-container left top">
      <strong style="min-width: 100px;">
        <span v-text="item.name"></span>
        <i class="baseIcon-CSS3 text-red" v-show="item.css3"></i>
      </strong>
      <span v-html="item.content" class="paddingh10"></span>
    </div>
  </div>
</template>

<script>
import css3Data from '../json/css3Data.json';
export default {
  name: 'default',
  data () {
    return {
      data:css3Data.data
    }
  },
  computed:{
    datas(){
      return this.dataReturn()
    },
    id1(){
      return this.$route.query.id1
    },
    id2(){
      return this.$route.query.id2
    },
    id3(){
      return this.$route.query.id3
    }
  },
  mounted() {
    // this.dataReturn();
  },
  methods: {
    dataReturn: function(){
      var that = this;
      var data = that.data[that.id1].dataList[that.id2].secList[that.id3];
      return data
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.default strong{
  min-width:60px;
  display:inline-block;
}
.default span.borderl{
  border-left:1px solid #666;
}
.default span.borderl:first-of-type{
  border-left:0
}
.default span.lh-14{
  line-height: 14px;
  height: 14px;
  display:inline-block;
}

</style>
