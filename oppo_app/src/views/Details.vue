<template>
    <div class="detail_wrap">
      <div class="crumb_wrap">
        <div class="crumb">
          <a href="#">首页</a>
          <a href="#">空调</a>
          <a href="javascript:void(0)">KFR-35GW/WXDA1@</a>
        </div>
      </div>
      <div class="product_wrap">
        <div class="product_left">
          <div class="zoom_pic"  v-show="show" :style="{'background-image':`url(${list[i].lg})`,'background-position':bgPosition}"></div>                 
          <div class="showcase" @mouseover="toggle(true)" @mouseout="toggle(false)" @mousemove="move($event)">
            <div class="mask" :style="maskStyle" v-show="show"></div>
             <img :src="list[i].md" alt="" class="showcase_inner">
          </div>               
          <ul class="thumbnails">
            <li :key="i" v-for="(p,i) of list"><a href=""><img :src="p.sm" alt="" @mouseover="change(i)"></a></li>
          </ul>
          <div class="share_collect">
            <div class="share_kits">
              <span>分享到</span>
              <div class="share_wrap">
                <a href="#" class="bds_qq icon"></a>
                <a href="#" class="bds_weixin icon"></a>
              </div>
            </div>
            <div class="collect_wrap">
              <i class="icon_1 icon"></i>
              <span class="collect_text1">收藏</span>
              <i class="icon_2 icon"></i>
              <span class="collect_text2">对比</span>
            </div>
          </div>
        </div>
        <div class="product_right">
          <h1>空调 变频大1.5匹 一级能效 智能冷暖 KFR-35GW/WXDA1@</h1>
          <h5><span>急速保价</span>1级能效，美居+京东直连，微信控制（可AIRKISS配网），蓝色时尚装饰块，大导风板，上下左右自动摆风</h5>
          <div class="floor_price">
            <div class="price_wrap">
              <p><span>¥</span>3299.00</p>
            </div>
          </div>
          <div class="floor_comment">
            <div class="comment1">
              <span class="icon1">优惠</span>
              <span class="icon2">送积分</span>
              <span class="icon3">最高送329积分</span>
            </div>
            <div class="comment2">
              <span class="icon1">领劵</span>
              <i class="c_icon1"></i>
              <span class="icon2">满减100</span>
              <span class="icon3">领取</span>
              <i class="c_icon2"></i>
            </div>
            <div class="comment3"></div>
          </div>
          <div>
            
          </div>
          <div></div>
          <div></div>
        </div>      
      </div>
    </div>
</template>

<script>
export default {
  data(){
    return {
      list:[
        {sm:require("../../public/img/details/1s1_78eeae9d72720a97A25859_120_120.webp"),md:require("../../public/img/details/1m1_78eeae9d72720a97A25859_530_530.webp"),lg:require("../../public/img/details/1l1_78eeae9d72720a97A25859.webp")},
        {sm:require("../../public/img/details/1s2_2ff9d9fcbff9d4fcA8430_120_120.webp"),md:require("../../public/img/details/1m2_2ff9d9fcbff9d4fcA8430_530_530.webp"),lg:require("../../public/img/details/1l2_2ff9d9fcbff9d4fcA8430.webp")},
        {sm:require("../../public/img/details/1s3_613deda569af56b8A25623_120_120.webp"),md:require("../../public/img/details/1m3_613deda569af56b8A25623_530_530.webp"),lg:require("../../public/img/details/1l3_613deda569af56b8A25623.webp")},
        {sm:require("../../public/img/details/1s4_e666eec19098dfdeA29769_120_120.webp"),md:require("../../public/img/details/1m4_e666eec19098dfdeA29769_530_530.webp"),lg:require("../../public/img/details/1l4_e666eec19098dfdeA29769.webp")},
        {sm:require("../../public/img/details/1s5_b6c97fb764c02f2aA25956_120_120.webp"),md:require("../../public/img/details/1m5_b6c97fb764c02f2aA25956_530_530.webp"),lg:require("../../public/img/details/1l5_b6c97fb764c02f2aA25956.webp")}
      ],
      specs:[],
      ulWidth:0,//小图片列表的宽
      moved:0,//已经左移的li的个数
      i:0,//默认显示第几张图片
      show:false,//控制mask和lgDiv的显示和隐藏
      maskStyle:{
        top:0,
        left:0
      }
    }
  },
  computed:{
    bgPosition(){
      return `-${parseFloat(this.maskStyle.left)*16/7}px -${parseFloat(this.maskStyle.top)*16/7}px`
    },
    ulMarginLeft(){
      return this.moved*-62+"px"
    }
  },
  created(){
    this.loadDetails();
  },
  methods:{
    moove(e){
      var top=e.offsetY-250/2;
      var left=e.offsetX-250/2;
      if(top<0) top=0;
      else if(top>250) top=250;
      if(left<0) left=0;
      else if(left>250) left=250;
      this.maskStyle.top=top+"px";
      this.maskStyle.left=left+"px";
    },
    toggle(bool){
      this.show=bool;
    },
    change(i){
      this.i=i;
    },
    move(i){
      if(i==-1&&this.moved!=0
          ||i==1&&this.moved<this.pics.length-4)
        this.moved+=i;
    },
    loadDetails(){
      this.axios.get(
        "http://localhost:3000/details",{
          params:{
            lid:this.$route.params.lid
          }
        }
      ).then(res=>{
        console.log(res.data);
        this.product=res.data.product;
        this.pics=res.data.pics;
        this.ulWidth=this.pics.length*62+"px";
        this.moved=0;
        this.i=0;
        this.show=false;
        this.specs=res.data.specs;
      })
    }
  },
  watch:{
    "$route":function(){
      this.loadDetails();
    }
  }
}
</script>

<style scoped>
  .crumb_wrap {
    border-bottom: 1px solid #eee;
  } 
  .crumb {
    width: 1190px;
    margin: 11px auto 10px auto;
    height: 20px;
  }
  .crumb a{
    display:block;
    height: 20px;
    line-height: 20px;
    color: #666;
    float:left;
    margin-left:15px;
  }
  .crumb a:last-child{
    cursor: default;
  }
  .crumb a:hover{
    color:#0092d8;
  }
  .product_wrap {
    clear:both;
    margin: 40px auto 60px auto;
    width: 1190px;
  }
  .product_wrap .product_left {
    float: left;
    padding-left: 85px;
    position: relative;
  }
  .product_wrap .zoom_pic {
    position:absolute;
    overflow:hidden;
    left: 595px;
    height: 500px;
    width: 500px;
    z-index:10;
    background-color: #fff;
  }
  .product_wrap .showcase {
    background-color: #fff;
    width: 500px;
    height: 500px;
    margin-right: 95px;
    position: relative;
  }
  .product_wrap .showcase_inner {
    display: block;
    height: 500px;
    width: 500px;
  }
  .mask{
    width:209px;
    height:209px;
    position: absolute;
    background-color: #0080dc;
    opacity: .2;
  }
  .product_wrap .thumbnails {
    clear: right;
    list-style:none;
    overflow: hidden;
    margin-top: 30px;
    padding-left: 50px;
  }
  .product_wrap .thumbnails li {
    border: 1px solid #d6d6d6;
    background-color: #fff;
    cursor: pointer;
    float: left;
    opacity: 0.4;
    margin: 1px 10px 1px 1px;
  }
  .product_wrap .thumbnails li img {
    width: 60px;
    height: 60px;
  }
  .product_wrap .share_collect {
    clear: right;
    overflow: hidden;
    padding-left: 50px;
    margin-top: 20px;
    height: 18px;
  }
  .share_collect .share_kits,.share_collect .collect_wrap {
    float: left;
    clear: right;
    overflow: hidden;
    margin-left:20px;
    border-left:1px solid #e6e6e6;
  }
  .share_kits>span{
    display: block;
    float: left;
    font-size: 12px;
    height: 18px;
    line-height: 18px;
    color: #333;
  }
  .share_collect .share_wrap{
    display:inline-block;
    
  }
  .share_collect .share_wrap .icon{
    display:inline-block;
    margin:0 0 0 10px;
    float:left;
    width: 18px;
    height: 18px;
   
  }
  .share_collect .share_wrap .bds_qq{
    background:url(../../public/img/xtb/detail_sprite.png) no-repeat -20px -66px;
  }
  .share_collect .share_wrap .bds_weixin{
    background:url(../../public/img/xtb/detail_sprite.png) no-repeat -36px -66px;
    width:22px;
  }
  .share_collect .icon{
    display:block;
    float:left;
    margin-left:20px;
    width:18px;
    height:18px;
  }
  .share_collect .icon_1{
    background:url(../../public/img/xtb/detail_sprite.png) no-repeat -38px -89px;
  }
  .share_collect .icon_2{
    background:url(../../public/img/xtb/detail_sprite.png) no-repeat -99px -124px;
  }
  .share_collect  .collect_wrap>span{
    margin-left:13px;
    float:left;
    padding-top:3px;
  }
  .product_wrap .product_right {
    width: 510px;
    float: left;
    margin-left: 0;    
  }
  .product_wrap .product_right h1 {
    margin-top: -3px;
    margin-bottom: 10px;
    color: #333;
    font-size: 22px;
    line-height: 28px;
    max-height: 54px;
    font-weight:normal;
    text-align:left;
    word-wrap: break-word;
    word-break: break-all;
  }
  .product_right h5 {
    color: #f60;
    font-size: 12px;
    line-height: 18px;
    margin-top: -3px;
    margin-bottom: 8px;
    position: relative;
    font-weight:normal;
    text-align:left;   
  }
.product_right h5>span{
    color: #0092d8;
    font-size: 10px;
    border: 1px #0092d8 solid;
    padding: 0 2px;
    border-radius: 2px;
  }
  .floor_price{
    background-color: #f2f2f2;
    padding: 15px 20px;
  }
  .floor_price p{
    text-align:left;
    color:#f60;
    font-size:32px;
  }
  .floor_price p>span{
    color:#333;
    font-size:20px;
    margin-right:2px;
  }
  .floor_comment .comment1{
    padding: 20px 0 17px;
    border-bottom: 1px dashed #eee;
    position: relative;
  }
  .floor_comment .comment1{
    font-size:12px;
    text-align:left; 
  }
  .floor_comment .comment1>span{
    display:inline-block;
  }
  .floor_comment .comment1>.icon1{
    width:54px;
    color:#999;
    line-height: 18px;
  }
  .floor_comment .comment1>.icon2{
    width:54px;
    color:#fff;
    background-color: #f60;
    line-height: 18px;
    text-align:center;
  }
  .floor_comment .comment1>.icon3{
    color:#333;
    margin-left:10px;
    line-height: 18px;
  }
  .floor_comment .comment2{
    padding-top:10px;
    border-bottom:1px dashed #eee;
    font-size:12px;
    text-align:left;
  }
  .floor_comment .comment2>span{
    display:inline-block;
    font-size:12px;
    line-height:20px;
  }
  .floor_comment .comment2>i{
    display:inline-block;
    width:6px;
    height:20px;
    padding-top:0px;
  }
  .floor_comment .comment2>.icon1{
    width:54px;
    color:#999;
  }
  .floor_comment .comment2>.icon2{
    background-color: #ff784c;
    height:20px;
    color:#fff;
    padding:0 10px;
    width:74px;
    text-align:center;
  }
  .floor_comment .comment2>.icon3{
    background-color: #ff784c;
    height:20px;
    color:#fff;
    padding:0 10px;
    width:44px;
    color:#fff;
    margin-left:1px;
    text-align:center;
  }
  .floor_comment .comment2>c_icon1{
    background:url(../../public/img/xtb/detail_sprite.png) no-repeat -99px -124px;
  }
  .floor_comment .comment2>c_icon2{
    background:url(../../public/img/xtb/detail_sprite.png) no-repeat -99px -124px;
  }
</style>