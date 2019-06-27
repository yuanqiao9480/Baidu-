# Baidu-
第二十到第二十一天：让你和页面对话
问题：
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">    
    <title>IFE ECMAScript</title>
    <style>
        .palette {
            margin: 0;
            padding: 0;
            list-style: none;
        }
        .palette li {
            width: 40px;
            height: 40px;
            border: 1px solid #000;
            cursor: pointer;
        }
    </style>
</head>
<body>            
    <ul class="palette">
        <li style="background-color:crimson"></li>
        <li style="background-color:bisque"></li>
        <li style="background-color:blueviolet"></li>
        <li style="background-color:coral"></li>
        <li style="background-color:chartreuse"></li>
        <li style="background-color:darkolivegreen"></li>
        <li style="background-color:cyan"></li>
        <li style="background-color:#194738"></li>        
    </ul>

    <p class="color-picker"></p>

    <script>
        var list = document.querySelectorAll("li");
        for (var i = i = 0, len = list.length; i < len; i++) {
            list[i].onclick = function(e) {
                var t = e.target;
                var c = t.style.backgroundColor;
                var p = document.getElementsByClassName("color-picker")[0]
                p.innerHTML = c;
                p.style.color = c;

            }
        }
    </script>
</body>
</html>
基于如上 HTML，实现如下功能：
点击某一个 Li 标签时，将 Li 的背景色显示在 P 标签内，并将 P 标签中的文字颜色设置成 Li 的背景色
基于上面的学习，如果你上一个练习没有用到事件代理的方式，那么请重构上一个编码练习，如果已经用到了，则进入下一个练习
答案：
         var oUl=document.getElementsByTagName("ul")[0],
                    oLi=oUl.getElementsByTagName("li"),
                    oP=document.getElementsByTagName("p")[0];
                oUl.onclick=function(e){
                    var e=e||window.event,
                        target=e.target||e.srcElement,
                        index=Array.prototype.indexOf.call(oLi,target);
                    oP.style.backgroundColor=target.style.backgroundColor;
                    oP.style.color=target.style.backgroundColor;
                    console.log(index);
                }
-  ------------------------------------------------- -------------------——————————————————————————————————————————————————————————————————                
