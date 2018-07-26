<template>
  <div id="app">
    <div class="header flex-container paddingv10">
      <div class="logo fs-20 text-center">
        <i class="baseIcon-wang text-blue"></i>
        <i class="baseIcon-lei text-red"></i>
      </div>
      <!-- top导航 -->
      <div class="flex1 fs-20 headerNav">
        <a :href="item.url" class="text-dark paddingh20" v-for="item in navUrl"><i :class="item.name"></i></a>
      </div>
      <div class="paddingh20 mobileNav" @click="headerNav=!headerNav">
        <i class="baseIcon-nav fs-20"></i>
      </div>
    </div>
    <!-- mobile top导航 -->
    <div class="fs-20 mobileNav" v-show="headerNav">
      <div class="flex-container">
        <a :href="item.url" class="text-dark flex1 text-center" v-for="item in navUrl"><i :class="item.name"></i></a>
       <!--  <a href="/#/emoji" class="text-dark flex1 text-center"><i class="baseIcon-smile"></i></a>
        <a href="/#/ScaleLinear" class="text-dark flex1 text-center"><i class="baseIcon-table"></i></a>
        <a href="/css/" class="text-dark flex1 text-center"><i class="baseIcon-CSS3"></i></a>
        <a href="/svg/" class="text-dark flex1 text-center"><i class="baseIcon-svg"></i></a> -->
      </div>
        
    </div>
    <div class="flex-container top paddingt10">
      <div class="nav borderr fs-14 text-dark lh-22 paddingl20 headerNav">
        <div v-for="(itemO,$indexO) in data">
          <div class="paddingh20 marginv5" style="border-left:3px solid #3bb4f2">
            <span v-text="itemO.cn" style="font-weight: 700;"></span> <span v-text="itemO.en" class="fs-10"></span>
          </div>
          <div v-for="(itemS,$indexS) in itemO.dataList">
            <div class="lh-30 navHover paddingl20">
              <span v-text="itemS.cn" style="color:#777"></span> <span v-text="itemS.en" class="fs-10" style="color:#aaa"></span>
            </div>

            <router-link :to="{path:'/default',query: {id1: $indexO,id2: $indexS,id3: $indexT}}" v-for="(itemT,$indexT) in itemS.secList" v-text="itemT.name" class="lh-28 navHover paddingl20 fs-12 dis-b" style="color:#777"></router-link>
          </div>
        </div>
      </div>
      <div class="pos-f top0 left0 bottom0 mobileNav" style="width:65%;background: rgb(0,0,0,.8);overflow-y: scroll" v-show="leftNav">
        <div class="fs-14 text-white lh-22 paddingt20">
          <div v-for="(itemO,$indexO) in data">
            <div class="paddingh20 margint5 marginb5 marginl20" style="border-left:3px solid #3bb4f2">
              <span v-text="itemO.cn" style="font-weight: 700;"></span> <span v-text="itemO.en" class="fs-10"></span>
            </div>
            <div v-for="(itemS,$indexS) in itemO.dataList">
              <div class="lh-30 navHover paddingl20">
                <span v-text="itemS.cn" class="text-white"></span> <span v-text="itemS.en" class="fs-10" style="color:#eee"></span>
              </div>

              <router-link :to="{path:'/default',query: {id1: $indexO,id2: $indexS,id3: $indexT}}" v-for="(itemT,$indexT) in itemS.secList" v-text="itemT.name" class="lh-28 navHover paddingl20 fs-12 dis-b text-white"></router-link>
            </div>
          </div>
        </div>
      </div>
      <div class="flex1 mobileRight">
        <router-view/>
      </div>
    </div>
    <div class="pos-f bottom30 right30 round flex-container center border" style="background: rgb(255, 255, 255, .4)">
      <div class="baseIcon-aim" style="font-size:40px;">
        <i :class="'path'+item" v-for="item in [1,2,3,4,5,6,7,8,9,10]" style="font-style:normal"></i>
      </div>
    </div>
    <div class="mobileNav" @click="leftNav = !leftNav">
      <div class="pos-f right30 round text-white flex-container center" style="bottom:110px;">
        <i class="baseIcon-navT" style="font-size:25px;"></i>
      </div>
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
      data:css3Data.data,
      headerNav:false,
      leftNav:false,
      navUrl:[
        {
          "name":"baseIcon-led",
          "url":"/#/led"
        },
        {
          "name":"baseIcon-smile",
          "url":"/#/emoji"
        },
        {
          "name":"baseIcon-table",
          "url":"/#/ScaleLinear"
        },
        {
          "name":"baseIcon-CSS3",
          "url":"/css/"
        },
        {
          "name":"baseIcon-svg",
          "url":"/svg/"
        }
      ]
    }
  },
  methods: {
    mobileNavShow: function(){
      var that = this;
      var data = that.data[that.id1].dataList[that.id2].secList[that.id3];
      return data
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
.mobileNav{
  display:none;
}
.mobileRight{
  padding-left:40px;
}
.logo{
  width:200px;
}
.round{
  width:60px;
  height:60px;
  border-radius: 50%;
  background-color:rgb(0,0,0,.2);
}
@media screen and (max-width: 640px) {
  .logo{
    width:100px;
  }
  .headerNav{
    display:none;
  }
  .headerNavShow{
    display:block;
  }
  .mobileNav{
    display:block;
  }
  .mobileRight{
    padding-left:20px;
    padding-right:20px;
  }
}
</style>
