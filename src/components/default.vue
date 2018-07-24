<template>
  <div class="default paddingl40 text-dark">
    <h1>语法</h1>
    <!-- 主key -->  
    <div class="lh-28">
      <strong v-text="datas.name"></strong>
      <span class="paddingh10 borderl lh-14" v-for="item in datas.key">
        <span v-text="item.name"></span><i class="baseIcon-CSS3 text-red" v-show="item.css3"></i>
      </span>
    </div>
    <!-- 默认值 -->
    <div class="lh-28">
      <strong>默认值</strong></span>
      <span class="marginh10" v-text="datas.default"></span>
    </div>
    <!-- 适用于 -->
    <div class="lh-28">
      <strong>适用于</strong>
      <span class="paddingh10 borderl lh-14" v-for="item in datas.apply">
        <span v-text="item"></span>
      </span>
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
  width:60px;
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
  height:14px;
  display:inline-block;
}

</style>
