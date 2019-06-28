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
-  ------------------------------------------------- -------------------
第二十二天到第二十四天：JavaScript里面的居民们
问题：
<div>
    <label>String A:
        <input id="radio-a" type="radio" checked="true" name="str-obj" value="a">
    </label>
    <textarea id="str-a"></textarea>
    <label>String B:
        <input id="radio-b" type="radio" name="str-obj" value="b">
    </label>
    <textarea id="str-b"></textarea>        
    <label>Num A：<input id="num-a" type="number" value="0"></label>
    <label>Num B：<input id="num-b" type="number" value="1"></label>
</div>
<div>
    <button>获取当前选中输入的内容长度</button>
    <button>当前选中输入中的第3个字符</button>
    <button>把两个输入框的文字连接在一起输出（concat）</button>
    <button>输入B中的内容，在输入A的内容中第一次出现的位置（indexOf）</button>
    <button>输入A中的内容，在输入B的内容中最后一次出现的位置（lastIndexOf）</button>
    <button>使用slice获取选中输入框内容的部分内容，参数为num-a及num-b</button>
    <button>当前选中输入框的行数</button>
    <button>使用substr获取选中输入框内容的子字符串，参数为num-a及num-b</button>
    <button>把所选输入框中的内容全部转为大写</button>
    <button>把所选输入框中的内容全部转为小写</button>
    <button>把所选输入框中内容的半角空格全部去除</button>
    <button>把所选输入框中内容的a全部替换成另外一个输入框中的内容</button>
</div>
<p id="result"></p>
基于如上HTML，实现需求
按照HTML中按钮的描述以此实现功能
计算结果显示在 id 为 result 的 P 标签中
答案：
        //定义常量
        const radioA = document.getElementById("radio-a"),
            radioB = document.getElementById("radio-b"),
            strA = document.getElementById("str-a"),
            strB = document.getElementById("str-b"),
            numA = document.getElementById("num-a"),
            numB = document.getElementById("num-b"),
            buttons = document.getElementsByTagName("button"),
            p = document.getElementById("result");

        //判断是否选中
        function isCheck(check) {
            if (check.checked) {
                return true;
            } else {
                return false;
            }
        }

        //按键1获取当前选中输入的内容长度
        buttons[0].addEventListener("click", function () {
            if (isCheck(radioA)) {
                p.innerHTML = strA.value.length;
            }
            if (isCheck(radioB)) {
                p.innerHTML = strB.value.length;
            }
        })

        //按键2当前选中输入中的第3个字符
        buttons[1].addEventListener("click", function () {
            if (isCheck(radioA)) {
                p.innerHTML = strA.value.charAt(2);
            }
            if (isCheck(radioB)) {
                p.innerHTML = strB.value.charAt(2);
            }
        })

        //按键3把两个输入框的文字连接在一起输出
        buttons[2].addEventListener("click", function () {
            p.innerHTML = strA.value.concat(strB.value);
        })

        //按键4输入B中的内容，在输入A的内容中第一次出现的位置
        buttons[3].addEventListener("click", function () {
            p.innerHTML = strA.value.indexOf(strB.value);
        })

        //按键5输入A中的内容，在输入B的内容中最后一次出现的位置
        buttons[4].addEventListener("click", function () {
            p.innerHTML = strB.value.lastIndexOf(strA.value);
        })

        //按键6使用slice获取选中输入框内容的部分内容，参数为num-a及num-b
        buttons[5].addEventListener("click", function () {
            if (isCheck(radioA)) {
                p.innerHTML = strA.value.slice(numA.value, numB.value);
            }
            if (isCheck(radioB)) {
                p.innerHTML = strB.value.slice(numA.value, numB.value);
            }
        })

        //按键7当前选中输入框的行数
        buttons[6].addEventListener("click", function () {
            if (isCheck(radioA)) {
                p.innerHTML = strA.value.split(/\r?\n|\r/).length + 1;
            }
            if (isCheck(radioB)) {
                p.innerHTML = strB.value.split(/\r?\n|\r/).length + 1;
            }
        })

        //按键8使用substr获取选中输入框内容的子字符串，参数为num-a及num-b
        buttons[7].addEventListener("click", function () {
            if (isCheck(radioA)) {
                p.innerHTML = strA.value.substring(numA.value, numB.value);
            }
            if (isCheck(radioB)) {
                p.innerHTML = strB.value.substring(numA.value, numB.value);
            }
        })

        //按键9把所选输入框中的内容全部转为大写
        buttons[8].addEventListener("click", function () {
            if (isCheck(radioA)) {
                p.innerHTML = strA.value.toUpperCase();
            }
            if (isCheck(radioB)) {
                p.innerHTML = strB.value.toUpperCase();
            }
        })

        //按键10把所选输入框中的内容全部转为小写
        buttons[8].addEventListener("click", function () {
            if (isCheck(radioA)) {
                p.innerHTML = strA.value.toUpperCase();
            }
            if (isCheck(radioB)) {
                p.innerHTML = strB.value.toUpperCase();
            }
        })


        //按键10把所选输入框中的内容全部转为小写
        buttons[9].addEventListener("click", function () {
            if (isCheck(radioA)) {
                p.innerHTML = strA.value.toLowerCase();
            }
            if (isCheck(radioB)) {
                p.innerHTML = strB.value.toLowerCase();
            }
        })

        //按键11，把所选输入框中内容的半角空格全部去除
        buttons[10].addEventListener('click', function () {
            if (isCheck(radioA)) {
                p.innerHTML = strA.value.replace(/\s+/g, '');
            }
            if (isCheck(radioB)) {
                p.innerHTML = strB.value.replace(/\s+/g, '');
            }
        })
       
        //按键12把所选输入框中内容的a全部替换成另外一个输入框中的内容
        buttons[11].addEventListener('click', function () {
            if(isCheck(radioA)){
                p.innerHTML = strA.value.replace(strA.value,strB.value);
            }
            if(isCheck(radioB)){
                p.innerHTML = strB.value.replace(strB.value,strA.value);
            }
        })
        ——————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————
