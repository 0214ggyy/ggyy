
### 东风 智能助手 后台管理系统

  该项目属于二次开发---pc端
  因代码编译习惯,坑是避免不了的,所以记录这次成长篇幅
  
  ## 项目技术
     vue.2x+vue-cli.3x+elementUI+css3
    
      1.组件显示整个页面用watch:监听路由to,from-->if判断this.$route.name---在标题头添加v-show判断条件.
      (上面是标题头写在app.vue中)个人建议不要这么写--->容易出现bug.    
      bug:::组件页面虽然显示整个页面,但是点击刷新时会出现标题头.并这种只是覆盖上面,当缩放页面时也会显示,标题头.结论:不要在app中写,另起一个组件,这样就不出现这个问题.
      2.rem在vue中使用.
      遇到问题:之前项目开发运用elementui没有使用rem相应式布局,如果自己编译一个新的页面,想在新的页面单独使用rem.配置起来比较困难,
      解决方式:采用css3中vw和vh视口单位（ Viewport units )
      @media screen and (max-width: 1200px) {
        .container,
        /* .title-top, */

        .title-but,
        .timelist,

        .syslist,

        .timeYlist,

        .detailslist,

        .box
        {
          transform: scale(0.75);
        }
        .container{
          min-height: 578px;
        }
        
  ### 先区别px、em、rem、%、vw、vh、vm这些单位
      1、px就是pixel的缩写，意为像素。px就是设备或者图片最小的一个点，比如常常听到的电脑像素是1024x768的，表示的是水平方向是1024个像素点，垂直方向是768个像素点。是我们网页设计常用的单位，也是基本单位。通过px可以设置固定的布局或者元素大小，缺点是没有弹性。特点是1. em的值并不是固定的； 
      2. em会继承父级元素的字体大小。em参考物是父元素的font-size，具有继承的特点。如果自身定义了font-size按自身来计算（浏览器默认字体是16px），整个页面内1em不是一个固定的值。特点是1. em的值并不是固定的； 2. em会继承父级元素的字体大小。
      3. rem是相对于根元素html，这样就意味着，我们只需要在根元素确定一个参考值，可以设计HTML为大小为10px，到时设置1.2rem就是12px.以此类推。优点是，只需要设置根目录的大小就可以把整个页面的成比例的调好。
      4、%一般来说就是相对于父元素的，1、对于普通定位元素就是我们理解的父元素 2、对于position: absolute;的元素是相对于已定位的父元素 3、对于position: fixed;的元素是相对于ViewPort（可视窗口），
      5、vw css3新单位，view width的简写，是指可视窗口的宽度。假如宽度是1200px的话。那10vw就是120px 举个例子：浏览器宽度1200px, 1 vw = 1200px/100 = 12 px。
      6、vh css3新单位，view height的简写，是指可视窗口的高度。假如高度是1200px的话。那10vh就是120p 举个例子：浏览器高度900px, 1 vh = 900px/100 = 9 px。
      7、vm css3新单位，相对于视口的宽度或高度中较小的那个。其中最小的那个被均分为100单位的vm 举个例子：浏览器高度900px，宽度1200px，取最小的浏览器高度，1 vm = 900px/100 = 9 px。兼容性太差 ，现在基本上没人用，我试了一下Chrome就用不了。3.常见问题假如使用em来设置文字大小要注意什么？4.解决方案注意父元素的字体大小，因为em是根据父元素的大小来设置的。比如同样是1.5em，要是父元素是20，那1.5em就是30px.要是父元素是30px,1.5em就是45px.特别是在多重div嵌套里面更要注意。


## git 一次输入密码设置
  git config --global credential.helper store
## vue渲染数据.高亮按钮 解决方式
    在data中定义即将渲染的数据，及active

	data() {
	  return {
	   wpList: [
	    {
	     name: '食品饮料'
	    },
	    {
	     name: '鲜花'
	    },
	    {
	     name: '其它'
	    }
	   ],
	   active:''
	  }
	 }
	 ...

	•定义高亮的标签类名

	.active {
	  background: #fd7522;
	  border: 1px solid #fd7522;
	  color: #fff;
	 }

	•动态渲染按钮的数据，并动态的增加active类名（当active为当前name值时添加），添加点击事件（点击时让active=name）

	<el-row class="wp-list">
	  <el-button v-for="item in wpList" :key="item.name" 
	  :class="{active : active == item.name}" 
	  @click="selected(item.name)">{{item.name}}</el-button>
	</el-row>

	•在methods中定义点击事件函数

	selected(name){
	  this.active = name;
	}
## 富文本编译样式::
	1.其中img图片需要后台给一个服务器接口,在postman中调用接口,上传图片.获取一个连接,添加到富文本编译中.
	2.其他标签的样式直接添加
	3.上传后台数据库
	4.调用接口获取数据渲染
	<h5 style="font-size:16px;font-family:PingFang-SC-Bold;font-weight:bold;color:rgba(255,255,255,1);padding-top:10px ;padding-left:17px ;">发布1.01版本</h5><p style="font-size:14px;font-family:PingFang-SC-Medium;font-weight:500;color:rgba(255,255,255,1);padding-top:21px ;padding-left:23px;"> 1.算法设置的疯狂双方开始疯狂沙克首付</p><p><img src="http://umapdev.dfmc.com.cn:8090/smart/BaseAppFile/send/图层 3.png"style="width: 193px;height: 145px;padding-top:13px ;padding-left:23px ;"></p><p style="font-size:14px;font-family:PingFang-SC-Medium;font-weight:500;color:rgba(255,255,255,1);padding-top:21px ;padding-left:23px;"> 2.算法设置的疯狂双方开始疯狂沙克首付</p><p><img src= "http://umapdev.dfmc.com.cn:8090/smart/BaseAppFile/send/图层 3.png" style="width: 193px;height: 145px;padding-top:13px ;padding-left:23px ;"><img src="http://umapdev.dfmc.com.cn:8090/smart/BaseAppFile/send/图层 3.png"style="width: 193px;height: 145px;padding-top:13px ;padding-left:23px ;"></p>
	
	
