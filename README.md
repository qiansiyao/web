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
