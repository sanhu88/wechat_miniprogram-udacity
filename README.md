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
由逗号分隔			"firstName":"John" , "lastName":"Doe" 
花括号用于保存对象	{ "firstName":"John" , "lastName":"Doe" }
方括号用于保存数组	
{"employees": [{ "firstName":"John" , "lastName":"Doe" }, { "firstName":"Anna" , "lastName":"Smith" }, { "firstName":"Peter" , "lastName":"Jones" }]}
在线格式化	http://www.bejson.com/

## 	发起网络请求
发起 HTTPS 网络请求 wx.request
修改位置index.js
https://developers.weixin.qq.com/miniprogram/dev/api/network/request/wx.request.html

箭头函数
https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Functions/Arrow_functions

success(res) {
console.log(res.data)
}
 let result = res.data.result


## 数据绑定
https://developers.weixin.qq.com/miniprogram/dev/framework/view/wxml/data.html
WXML 中的动态数据均来自对应 Page 的 data
数据绑定使用 Mustache 语法（双大括号）将变量包起来

index.wxml中的 <view class="temp">{{nowTemp}}°</view>
对应
index.js中的
data:{
    nowTemp :14,
    nowWeather : 'sunny'
  },


 在data中，增加
this.setData({
   nowTemp : temp,
   nowWeather : weather
  })
setData 函数用于将数据从逻辑层发送到视图层（异步），同时改变对应的 this.data 的值（同步）。

注意：1. 直接修改 this.data 而不调用 this.setData 是无法改变页面的状态的，还会造成数据不一致。
用 this.setData 函数来更新 Data 中的数据而不是去直接修改 this.data


## wx.setNavigationBarColor
 index.js-->onLoad()
https://developers.weixin.qq.com/miniprogram/dev/api/ui/navigation-bar/wx.setNavigationBarColor.html

 wx.setNavigationBarColor({
  frontColor: '#000000', /*颜色必须六位*/
  backgroundColor: weatherColorMap[weather],
})


## 	下拉刷新 onPullDownRefresh() 
监听屏幕的下拉手势，
调用网络 API 获取数据，
调用网络的同时，在屏幕上给出提示（例如点点点或者圈圈），来告诉用户正在获取数据。
数据返回后关闭提示，
数据返回后在页面上显示新的数据

官方文档
https://developers.weixin.qq.com/miniprogram/dev/api/ui/pull-down-refresh/wx.startPullDownRefresh.html

封装getNow()

## 天气预报list
WXML:
<scroll-view scroll-x>

WXSS
display: flex;
flex-direction: column;

获取现在的时间小时
let nowHour = new Date().getHours()

## 今天状态条
教程写法
 	todayTemp: `${result.today.minTemp}° - ${result.today.maxTemp}°`,
 	todayDate: `${date.getFullYear()}-${date.getMonth()+1}-${date.getDate()} 今天`
使用了撇号`
自己使用的是 Date() 拼接的

new Date().getTime() 获取时间戳


## list
flex-grow


## 	获取位置信息
bindtap = 'onTapLocation'

wx.getLocation(Object object)


wx.getLocation({
 type: 'wgs84',
 success (res) {
   const latitude = res.latitude
   const longitude = res.longitude
   const speed = res.speed
   const accuracy = res.accuracy
 }
})

https://developers.weixin.qq.com/miniprogram/dev/api/location/wx.getLocation.html


经纬度转化城市名
逆地址解析
reverseGeocoder(options:Object)

https://lbs.qq.com/qqmap_wx_jssdk/method-reverseGeocoder.html

## 		城市值和tips绑定 -6.6使新的位置
在 wxml 中使用 {{city}} 渲染动态变量
在 data 中声明动态变量 city，设置默认值 '广州市'
在获取城市名后，调用 setData() 对 city 赋值
对 city 赋值后，重新获取天气数据
在获取天气数据时，使用 data 中存储的当前城市名称
在调用 setData 之后，调用 getNow() 获取天气数据