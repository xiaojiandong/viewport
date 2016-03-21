
# viewport 动态全局缩放适配不同宽度的手机屏幕
# 步骤
1. 引入autoview.js这段脚本
2. 引入css样式，定宽640px

# autoview.js脚本中的内容：
  ``` javascript  
    $(function(){
      var jsVer = 29;
            var useScaledViewportMeta = function ( ) {
            //一段动态的viewport meta设置，以640像素为基础宽度，动态全局缩放适配不同宽度的浏览器屏幕
            //@isAndroid:boolean  android环境下，不需要user-scalable参数，设置了反而引发了scale的失效
                var phoneWidth = parseInt(window.screen.width);
                var phoneScale = phoneWidth/640;
                document.write('<meta name="viewport" content="width=640, user-scalable=no,           target-densitydpi=device-dpi,minimum-scale='+phoneScale+',maximum-scale='+phoneScale+'">');
            };
            var ua = navigator.userAgent;
            if (/Android (\d+\.\d+)/.test(ua)){
                var version = parseFloat(RegExp.$1);
               // andriod 2.3
               if(version>2.3){
                   useScaledViewportMeta();
                   // andriod 2.3以上
                }else{
                   document.write('<meta name="viewport" content="width=640, target-densitydpi=device-dpi">');
                }
               // 其他系统
           } else {
                useScaledViewportMeta();
            }
      });
  ```      

*****************************
# css样式中的内容
``` css
.page-outer-wrap{ /*这是最外层父容器的样式*/
   width: 640px;
   margin: 0 auto;
   border: 1px solid #f00;
   box-sizing: border-box;
}
```
*****************************
# pc端呈现示意图
![image](https://github.com/xiaojiandong/viewport/blob/master/autoview/image/pc-auto.png)
# 移动端iphone6P呈现示意图
![image](https://github.com/xiaojiandong/viewport/blob/master/autoview/image/m-iphone6p.png)
# 移动端iphone6呈现示意图
![image](https://github.com/xiaojiandong/viewport/blob/master/autoview/image/m-iphone6.png)
# 移动端iphone5呈现示意图
![image](https://github.com/xiaojiandong/viewport/blob/master/autoview/image/m-iphone5.png)
# 移动端iphone4呈现示意图
![image](https://github.com/xiaojiandong/viewport/blob/master/autoview/image/m-iphone4.png)

# 针对于其他安卓手机，同样缩放；也可以在ipad屏幕上缩放但不建议使用
