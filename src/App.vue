<template>
  <div id="app" class="flex-container top paddingt20">
    <div class="nav borderr fs-14 text-dark lh-22 paddingl20">
      <div v-for="itemO in data">
        <div class="paddingh20 marginv5" style="border-left:3px solid #3bb4f2">
          <span v-text="itemO.cn" style="font-weight: 700;"></span> <span v-text="itemO.en" class="fs-10"></span>
        </div>
        <div v-for="itemS in itemO.dataList">
          <div class="lh-30 navHover paddingl20">
            <span v-text="itemS.cn" style="color:#777"></span> <span v-text="itemS.en" class="fs-10" style="color:#aaa"></span>
          </div>
          <div v-for="itemT in itemS.secList" v-text="itemT.name" class="lh-28 navHover paddingl20 fs-12" style="color:#777"></div>
        </div>
      </div>
    </div>
    <div class="flex1">
      <router-view/>
    </div>
  </div>
</template>

<script>
import css from './assets/cmui.css';
import css3Data from './json/css3Data.json';

export default {
  name: 'App',
  data () {
    return {
      data:css3Data.data
    }
  }
}
</script>

<style>
body{
  font-family: "Segoe UI","Lucida Grande",Helvetica,Arial,"Microsoft YaHei",FreeSans,Arimo,"Droid Sans","wenquanyi micro hei","Hiragino Sans GB","Hiragino Sans GB W3",FontAwesome,sans-serif;
}
.marginv5{
  margin:5px 0;
}
.lh-22{
  line-height:22px;
}
.lh-30{
  line-height:30px;
}
.navHover:hover{
  background: rgba(0,0,0,.1)
}
</style>
