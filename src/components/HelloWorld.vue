<template>
  <div class="hello paddingl40">
    <!-- 第一层 -->
    <div v-for="(itemO,$indexO) in data">
    <!-- 第二层 -->
      <div v-for="(itemS,$indexS) in itemO.dataList">
        <h1 class="text-darker lh-32 fs-18" v-text="itemS.cn + ' ' + itemS.en"></h1>
        <div class="margint10">
          <router-link :to="{path:'/default',query: {id1: $indexO,id2: $indexS,id3: $indexT}}" v-for="(itemT,$indexT) in itemS.secList" v-text="itemT.name" class="cssWidth text-dark dis-i"></router-link>
        </div>
      </div>
    </div>
    
  </div>
</template>

<script>
import css3Data from '../json/css3Data.json';
export default {
  name: 'HelloWorld',
  data () {
    return {
      data:css3Data.data
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.cssWidth{
  width:180px;
}
</style>
