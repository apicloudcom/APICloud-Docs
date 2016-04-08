/*
Title: 视频及源码
Description: 视频及源码
Sort: 6
*/
<style type="text/css">
    .float-l{
        float:left;   
    }
    .float-r{
        float:right;   
    }
    .row.v-course{
        padding:0 15px;
    }
    .row.v-course .odd,.row.v-course .even{
        width:49%;
    }
    .veo-classify{
        width:100%;
        border:1px solid #dcdcdc;
        /*float: left;*/
        display: inline-block;
        margin:10px 0;
    }
    .veo-header{
        padding:20px 5%;
        overflow: hidden;
        border-bottom: 1px solid #dcdcdc;
    }
    .veo-header .pic{
        display: block;
        width:44.7%;
        /*height:105px;*/
        float: left;
        margin-right: 5%;
    }
    .veo-header .info{
        float:left;
        width:50%;
    }
    .veo-header .info .brief{
        width:100%;
        font-size:12px;
        line-height: 20px;
        margin:0;
        height:60px;
        overflow:hidden;
    }
    .content ul.veo-list{
        list-style: none;
        padding:0;
        margin:0;
    }
    .veo-list li{
        overflow:hidden;
        height:30px;
        padding:0 6%;
        margin:5px 0;
    }
    .veo-list li span:first-child{
        /*width:20%;*/
    }
    .veo-list .veo-line{
        width:1px;
        height:20px;
        background-color:#333;
        margin:5px 3%;
    }
    .veo-list li span{
        display: inline-block;
        line-height:30px;
    }
    .veo-list .veo-name{
        width:72%;
        overflow:hidden;
        display: inline-block;
        line-height:30px;
        white-space: nowrap;
        text-overflow:ellipsis;
        text-decoration: none;
        cursor: pointer;
    }
    .veo-list .veo-more{
        text-align: center;
        color:#619be4;
        border-top:1px solid #dcdcdc;
        height:40px;
        margin:0;
    }
    .veo-list .get-more{
        cursor:pointer;
    }
    .veo-list .get-more .icon{
        width:15px;
        height:6px;
        margin-right: 5px;
        display: inline-block;
    }
    .veo-list .get-more .arr-b{
        background: url(../img/arr-b.png) no-repeat;
    }
    .veo-list .get-more .arr-t{
        background: url(../img/arr-t.png) no-repeat;
    }
    .veo-list .veo-more span{
        line-height: 40px;
    }
</style>
<h1 class="first">视频教程</h1>
<div class="row v-course">
    <div class="float-l even">
    </div>
    <div class="float-r odd"></div>
</div>

<!-- <h1 class="module-video">模块视频</h1>
<table class="table table-bordered">
    <tr>
        <td><a href="#">listView</a></td>
        <td><a href="#">listView</a></td>
        <td><a href="#">listView</a></td>
        <td><a href="#">listView</a></td>
        <td><a href="#">listView</a></td>
    </tr>
    <tr>
        <td><a href="#">listView</a></td>
        <td><a href="#">listView</a></td>
        <td><a href="#">listView</a></td>
        <td><a href="#">listView</a></td>
        <td><a href="#">listView</a></td>
    </tr>
    <tr>
        <td><a href="#">listView</a></td>
        <td><a href="#">listView</a></td>
        <td><a href="#">listView</a></td>
        <td><a href="#">listView</a></td>
        <td><a href="#">listView</a></td>
    </tr>
    <tr>
        <td><a href="#">listView</a></td>
        <td><a href="#">listView</a></td>
        <td></td>
        <td></td>
        <td></td>
    </tr>
</table> -->

<h1 class="example-code">案例源码</h1><div>*由APICloud及社区用户贡献</div>
<div class="example-con" id="example-code">
</div>
<!--video player-->
<div id="vplayer" class="modalx">
    <a href="javascript:void(0);" class="close"></a>
    <div class="wrap"></div>
</div>
<style type="text/css">
    .content .title{display: none;}
    .content .intro{margin-bottom: 0;}
    h1{
        margin-bottom: 10px;
    }
    h1.first{margin-top: 0;}
    .content img{
        border:none; padding: 0; border-radius: 0; 
        width: 179px; height: 101px;
    }
    .v-course{
        height: auto;
        position: relative;
    }
    .v-course.active{
    }
    .v-course .v-course-container{
        margin: 0;
        width: 1028px;
        max-height: 167px;
        overflow: hidden;
        -webkit-transition: all .25s ease;
           -moz-transition: all .25s ease;
            -ms-transition: all .25s ease;
             -o-transition: all .25s ease;
                transition: all .25s ease;
        margin-left: 15px;
    }
    .v-course.active .v-course-container{
        max-height: 835px;
    }
    .v-course .glyphicon-chevron-down,.v-course.active .glyphicon-chevron-up{
        display: inline-block;
    }
    .v-course .glyphicon-chevron-up,.v-course.active .glyphicon-chevron-down{
        display: none;
    }
    .v-course .v-course-box{
        position: relative; margin-right: 26px;
        width: 179px; height: 154px;
        border: 1px solid #EBEBEB;
        margin-bottom: 13px;
        float: left;
    }
    .v-course a{
        display: inline-block;
    }
    .v-course a .play{
        display: inline-block;
        height: 52px;
        width: 52px;
        top: 0;
        background: url(/img/vbtn.png) no-repeat;
        z-index: 200;
        position: absolute; left: 50%; top: 50%;
        margin-left: -26px; margin-top: -50px;
    }
    .v-course a:hover .play{
        background: url(/img/vbtn.png) no-repeat left bottom;
    }
    .v-course label{
        width: 177px; height: 46px; color: #4D4D4D;
        background-color: #FAFAFA; padding: 7px 10px;
        overflow: hidden; font-size: 12px;
        border-top: 1px solid #EBEBEB;
    }
    .v-course .list-toggle{
        position: absolute;
        bottom: -13px;
        left: 940px;
        font-size: 12px;
        cursor: pointer;
        color: #609BE3;
        text-decoration: underline;
    }
    .module-video, .example-code{
        margin-top: 70px;
    }
    .example-code span{
        font-size: 14px; color: #808080; margin-left: 40px; 
        font-weight: normal;
    }
    .apidemo{
        border:1px solid #dfdfdf; margin-bottom: 10px;
        width: 497px; margin-right: 9px;
        padding: 11px 17px;
    }
    .apidemo .pull-left{
        width: 214px;
        border-right: 1px solid #D6D6D6;
    }
    .apidemo .img-right{
        margin-left: 84px;
    }
    .apidemo .pull-left.right{
        width: 247px;
        border-right: none;
    }
    .apidemo img, .custom-app img{
        width: 66px; height: 66px; float: left; border-radius: 10px;
    }
    .apidemo h2,.apidemo a.cus-title{
        color:#609BE3; font-size: 12px;
        font-weight: bolder; margin-top: 4px; margin-bottom: 4px;
        display: block;
        background: none;
        padding-left: 0;
    }
    .apidemo h2.sname{
        color: #808080; font-weight: normal;
        margin-top: 0; margin-bottom: 12px;
        text-overflow: ellipsis;
        overflow: hidden;
        white-space: nowrap;
    }
    .apidemo a{
        font-size: 12px;
        background: url(/img/icon-download.png) no-repeat left center; 
        padding-left: 20px;
        display: inline-block;
        line-height: 18px;
    }
    .apidemo p.intro{
        padding-left: 17px;
        padding-top: 0;
        font-size: 12px;
        color: #808080;
        overflow-y: auto;
        max-height: none;
        min-height: 60px;
    }
    .apidemo,.custom-app{
        background-color: #FAFAFA;
    }
    .custom-app {
        width: 244px;
        border: 1px solid #ECECEC;
        margin-right: 9px;
        margin-bottom: 9px;
        padding: 11px 17px;
    }
    .custom-app .pull-left{
        width: 214px;
    }
    .custom-app .img-right{
        margin-left: 84px;
    }
    .custom-app .pull-left.right{
        width: 247px;
        border-right: none;
    }
    .custom-app h2,.custom-app a.cus-title{
        color:#609BE3; font-size: 12px;
        font-weight: bolder; margin-top: 4px; margin-bottom: 4px;
        display: block;
        background: none;
        padding-left: 0;
    }
    .custom-app h2.sname{
        color: #808080; font-weight: normal;
        margin-top: 0; margin-bottom: 12px;
        text-overflow: ellipsis;
        overflow: hidden;
        white-space: nowrap;
    }
    .custom-app a{
        font-size: 12px;
        background: url(/img/icon-download.png) no-repeat left center; 
        padding-left: 20px;
        display: inline-block;
        line-height: 18px;
    }
    .app-code{
        border:1px solid #dfdfdf; padding: 40px; margin-bottom: 10px;
    }
    .app-code h4{
        font-size: 16px; position: relative; top: -6px; color:#222;
    }
    .app-code .info{
        margin-left: 20px;
    }
    .app-code .explain, .app-code .code{
        display: inline-block; font-weight: bold;
    }
    .app-code .explain{
        background: url(/img/icon-view.png) no-repeat left center; 
        padding-left: 26px;
    }
    .app-code .code{
        background: url(/img/icon-download.png) no-repeat left center;
        padding-left: 20px; margin-left: 40px;
    }
    .first{
        padding-left: 0; padding-right: 5px;
    }
    .last{
        padding-right: 0; padding-left: 5px;
    }
    p.intro{
        clear: both; padding-top: 20px; margin-bottom: 0; line-height: 1.4;
        max-height: 60px; min-height: 60px; overflow: hidden;

    }
    .example-con{
        width: 1028px;
        margin-top: 30px;
    }

    .modalx {
        background: none repeat scroll 0 0 rgba(0, 0, 0, 0.9);
        display: table;
        height: 100%;
        left: 0;
        overflow: hidden;
        position: fixed;
        top: 0;
        vertical-align: middle;
        visibility: hidden;
        width: 100%;
        z-index: 9999;
    }
    .modalx > a.close {
        background-image: url("/img/close.png");
        background-repeat: no-repeat;
        background-position: center center;
        border: 3px solid rgba(255, 255, 255, 0);
        border-radius: 50%;
        cursor: pointer;
        display: block;
        height: 45px;
        opacity: 0.3;
        position: fixed;
        right: 27px;
        top: 27px;
        transition: all 0.5s cubic-bezier(0.27, 1.64, 0.32, 0.95) 0s;
        width: 45px;
        z-index: 10000;
    }
    .modalx > a.close:hover {
        border-color: rgba(255, 255, 255, 0.3);
        border-radius: 50%;
        opacity: 1;
        transform: rotate(90deg);
    }
    .modalx > .content {
        display: table-cell;
        text-align: center;
        vertical-align: middle;
    }
    #h5video{
        position: absolute; left:0; right: 0; margin: auto;
    }
</style>

