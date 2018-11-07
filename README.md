# wechat_miniprogram-udacity
note of learning Wechat Mini Program


##  开发者网站
https://mp.weixin.qq.com

开发者ID ： 设置-->开发设置


##  创建全新的项目:

项目目录：选择一个空文件夹
AppID： 填入你的 AppID
项目名称：可以任意填写，例如 weather
勾选 建立普通快速启动模版
点击 确定


## 	WXML & WXSS
WXML（WeiXin Markup Language）
https://developers.weixin.qq.com/miniprogram/dev/framework/view/wxml/

WXSS(WeiXin Style Sheets)
https://developers.weixin.qq.com/miniprogram/dev/framework/view/wxss.html
				rpx（responsive pixel）
				可以根据屏幕宽度进行自适应。规定屏幕宽为750rpx。
				定义在 app.wxss 中的样式为全局样式
				page 的 wxss 文件中定义的样式为局部样式，并会覆盖 app.wxss

WXML -- html 代码
WXSS -- css 代码

## 	rpx
【px】px就是Pixel的缩写，就是指像素。这个作为图片采样的基本单位，没什么需要特别说明的。

【rem】在做移动端适配是最常用的方法就是使用rem作为单位，因为rem是根据html的fontsize去动态计算实际的px的。

【rpx】rpx其实是微信对于rem的一种应用的规定，或者说一种设计的方案，官方上规定屏幕宽度为20rem，规定屏幕宽为750rpx。
微信小程序中1rem=750/20rpx 

计算屏幕长度对应的rpx对应 比如宽度是W px，长度是L px
则L(rpx)= (750/Wpx)*Lpx

官方文档
https://developers.weixin.qq.com/miniprogram/dev/

## 	opacity
opacity 来修改文字的深浅 0.8

文字视图，通常我们都会设定行高是文字大小的1.4倍。

## background
src="/images/sunny-bg.png" mode="scaleToFill"
mode 图片裁剪缩放的模式
	scaleToFill  不保持纵横比缩放图片，使图片的宽高完全拉伸至填满 image 元素


父视图：position: relative;
 需要定位的子视图position: absolute;
 	http://zh.learnlayout.com/position.html
## 	navigationBarBackgroundColor
app.json

##  onLoad() 
onLoad() 函数,我们可以给 Page() 传入 onLoad() 函数
onLoad() 函数会在页面启动时被执行

## API
https://test-miniprogram.com/api/weather/now?city=上海市

## URL
URL（统一资源定位符）是 URI（通用资源标识）的特定类型


URL 通常由以下三或四个组成部分组成，第四部分可省略：

协议。它可以是 HTTP（不带 SSL）或 HTTPS（带 SSL）。
主机。例如：cn.udacity.com。
路径。例如：/course/wechat-mini-program--nd666-cn-1。
查询字符串。规则为?后显示参数查询值，伪 url 为：?param1=value1&param2=value2

## JSON
JSON 语法是 JavaScript 对象表示法语法的子集。

数据通过"名称":"值"	"firstName" : "John"
