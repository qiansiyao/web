# web

ie8 div支持放大

    if(navigator.appName == "Microsoft Internet Explorer" && navigator.appVersion.match(/8./i)=="8.") 
    { 
    $(function(){
    var imgWid = 0 ;
    var imgHei = 0 ; //变量初始化
    var big = 1.1;//放大倍数
    $(".family .item").hover(function(){
    $(this).find(".fa").stop(true,true);
    var imgWid2 = 0;var imgHei2 = 0;//局部变量
    imgWid = $(this).find(".fa").width();
    imgHei = $(this).find(".fa").height();
    imgWid2 = imgWid * big;
    imgHei2 = imgHei * big;
    $(this).find(".fa").css({"z-index":2});
    $(this).find(".fa").animate({"width":imgWid2,"height":imgHei2,"top":"0px"});
    $(this).find("div").animate({"width":imgWid2,"height":imgHei2,"top":"0px"});

    },function(){
    $(this).find(".fa").stop().animate({"width":imgWid,"height":imgHei});
    $(this).find("div").stop().animate({"width":imgWid,"height":imgHei});

    });
    })
    }

ie9下select选择框的下标样式问题：

    首先我们需要用一个div容器包裹在select元素外围：
    <div class="styled-select">
    <select>
    <option>The second option</option>
    <option>The second option</option>
    </select>
     </div>
    下一步我们需要加入一些css，以确保选择框元素被以某种方式美化：
    .styled-select select {
       background: transparent;
       width: 268px;
       padding: 5px;
       font-size: 16px;
       border: 1px solid #ccc;
       height: 34px;
       -webkit-appearance: none; /*for chrome*/
    }
    我们需要确保选择框的跨度比外围的div容器更宽，这样默认的下拉箭头就会消失（译者注：选择框比外面的div宽大，默认的下拉箭头就会被隐藏）
    我们的div容器需要被美化成新的下拉箭头出现在我们预想的位置：
    .styled-select {
       width: 240px;
       height: 34px;
       overflow: hidden;
       background: url(new_arrow.png) no-repeat right #ddd;
    }
    
兼容ie8 9和firefox的select下添加option的方法

    function addOption(){ 
    //根据id查找对象， 
    var obj=document.getElementById('mySelect'); 
    //添加一个选项 
    obj.add(new Option("值","属性")); //这个只能在IE中有效 
    obj.options.add(new Option("value","text")); //这个兼容IE与firefox 
    } 
    
自定义字体的解决方案：

    自定义字体：http://www.w3schools.com/cssref/css3_pr_font-face_rule.asp
    最好用eot格式。对IE能达到最大兼容。
    字体在线转换：http://transfonter.org/
    没有上传大小限制。并且转换出来的字体文件没有问题。
    ①根据psd找出自己所需的字体类型，提示框内的就是字体名称
    ②上网下载自己所需的字体
    ③如果下的是.ttf哥格式的，就用网站http://transfonter.org/将其转换成.eot.格式的，因为.ttf格式只对chrome有效，.eot格式对IE有效，也可以顺便把.woff格式的写进去。
    ④对应css中加入相应的语句，url是写你存放这些字体的路径。
    兼容所以模式的字体写法：
    @font-face {
      font-family: 'MyWebFont';
      src: url('webfont.eot'); /* IE9 Compat Modes */
      src: url('webfont.eot?#iefix') format('embedded-opentype'), /* IE6-IE8 */
           url('webfont.woff2') format('woff2'), /* Super Modern Browsers */
           url('webfont.woff') format('woff'), /* Pretty Modern Browsers */
           url('webfont.ttf')  format('truetype'), /* Safari, Android, iOS */
           url('webfont.svg#svgFontName') format('svg'); /* Legacy iOS */
    }
    ⑤在你想要字体的那里加入css语句：
      div{
              font-family: MyWebFont;  
       }
