<template>
<div>
  <div id="header">
        <div class="inner">
            <a class="midea_logo" href="//www.midea.cn/?mtag=40005.1.10" title="美的"><img src="../../public/img/header/midea_logo.png" alt=""></a>
            <ul class="nav">
                <li class="item">
                    <a href="#">首页</a>
                </li>
                <li class="item">
                    <a href="#">商家入驻</a>
                </li>
                <li class="item">
                    <a href="">企业采购</a>
                </li>
                <li class="item">
                    <a href="#">全屋家电套购</a>
                </li>
                <li class="item">
                    <a href="#">会员福利社</a>
                </li>
            </ul> 
        </div>
        <div class="search_wrap">
            <form action="">
                <input type="search" name="keyword" placeholder="请搜索商品">
                <a href="#">
                    <i class="search_i"></i>
                </a>
            </form>
        </div>
        <div class="myphone">
            <a href="#">
                <i class="icon_phone"></i>
            </a>
        </div>
        <div class="mycart">
            <a href="#">
                <i class="icon_cart"></i>
            </a>
        </div>
        <div class="login">
            <a href="#">
                <i class="icon_login"></i><span>登录</span>
            </a>
        </div>
    </div>
    <div class="operation_wrap">
        【通知消息】
    </div>
</div>    
</template>

<script>
  export default {
  }
</script>

<style scoped>
        #header{
            height:44px;
            margin:0 auto;
            overflow:hidden;
            position:relative;
            background:#0092d8;
        }
        .midea_logo{
            float:left;
            width: 120px;
            height: 44px;      
        }
        .nav{
            list-style:none;
            margin-left:150px;
        }
        .nav li.item{
            float:left;
            line-height:44px;
        }
        .nav .item a{
            display:block;
            text-decoration:none;
            padding:0 30px;
            font-family:\5FAE\8F6F\96C5\9ED1;
            height: 44px;
            line-height: 44px;
            color: #a3c3e6;
            font-size: 12px;
        }
        #header>.inner>.nav>.item>a:hover{color:#fff;}
        #header>.search_wrap{
            width:250px;
            height:44px;
            position: absolute;
            top:0;
            right:218PX;
            background:white;
        }
        #header>.search_wrap>form>input{
            width:100%;
            height:44px;
            line-height: 44px;
            padding: 0 10px 0 35px;
            border: 0 none;
            border-bottom: 1px solid #e0e0e0;
            border-radius: 0;
        }
        #header>.search_wrap>form>a>i.search_i{
            background:url(../../public/img/header/search.png) no-repeat 0px 0px;
            position:absolute;
            top:6px;
            right:219px;
            width:25px;
            height:25px;
            display:block;
        } 
        #header>.myphone,.mycart,.login{
            position:absolute;
            height:44px;
        }
        #header>.myphone{
            width:65px;
            right:153px;
        }
        #header>.mycart{
            width:65px;
            right:89px;
        }
        #header>.login{
            width:86px;
            right:0px;
        }
        #header>.myphone:hover,#header>.mycart:hover,#header>.login:hover{
            background:#006fa3;
        }
        .inform{
            width:100%;
            height:16px;
            font-size: 12px;
            background: rgb(0, 59, 102);
            line-height: 16px;
            color: rgb(255, 255, 255);
            text-align: center;
            padding: 4px;
        }
        #header>div>a{text-decoration:none}
        #header>div>a>i{
            position:absolute;
            width:20px;
            height:20px;
            display:block;
        }
        #header>.myphone>a>i.icon_phone{  
            background:url(../../public/img/header/index_sprite.png) no-repeat -118px -213px;
        }
        #header>.mycart>a>i.icon_cart{  
            background:url(../../public/img/header/index_sprite.png) no-repeat -146px -213px;
        }
        #header>.login>a>i.icon_login{  
            background:url(../../public/img/header/index_sprite.png) no-repeat -37px -213px;
        }
        #header>.myphone>a>.icon_phone{
            top:10px;
            right:24px;
        }
        #header>.mycart>a>.icon_cart{
            top:10px;
            right:24px;
        }
        #header>.login>a>.icon_login{
            top:10px;
            right:58px;
        }
        #header>.login>a>span{
            position:absolute;
            top:11px;
            right:20px;
            color:#fff;
        }
        .operation_wrap{
            overflow: hidden;
            display: block;
            font-size: 12px;
            background: rgb(0, 59, 102);
            line-height: 16px;
            color: rgb(255, 255, 255);
            text-align: center;
            padding: 4px;
        }
</style>