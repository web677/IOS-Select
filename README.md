
## IOS-Selector是什么?
IOS-Selector是一个仿苹果select的选择器控件。

公司产品提需求，要改进现在的地址选择方式，之前是三个select，各自独立，每次进行查询匹配。复用性无且安卓IOS样式不一致。

思路很简单，先画三个列表，填入数据，new 三个新的IScroll绑定滑动相关事件即可。代码只有不到两百行，受限于之前所用地址数据格式，解析方式部分有些绕。也因此，对于来源数据的地址格式得按照要求来。可以应用为1/2/3级联动，demo中分别有地址/日期/性别的选择demo。
## 参数

* column： 选择框联动层级
* data： 数据（数据格式严格参照给出的格式）
* title： 选择控件title
* default： 默认选中项（参数格式严格按照demo来，有几级就写几级）
* callback： 确定选择的回调函数，传回三个参数，分别是被选中项的id的数组/文本的数组/完整key值得数组

### 调用示例：

```javascript
    var mySelector = new IosSelector("#demo",{
            column: 3,
            data: address,
            title: "地址选择",
            default: ["23-河南省","992-平顶山市","1413-高新技术产业开发区-467000-0375"],
            callback: function(id,text,key) {
                console.log(id,text,key);
            }
    });
```

### 示例图片
![image](https://github.com/web677/IOS-Select/blob/master/img/ios-selector.jpg)

## 注意：

* 引入的iscroll必须为probe版本的;
* 样式使用单位为rem，Iphone6/6s(375 X 667)下：html {font-size: 50px;} 且font-size在ios-selector.css中写死。如重置，请重写ios-selector.css。
* 在前一个select滑动停止前滑动下一个，偶尔会导致报错（要重现这个问题需要极快的手速或者在PC端用浏览器快速滑动），不过不会阻塞JS运行，也不会导致数据异常，暂未发现不良后果（这里有参考百度钱包H5页面中的地址选择控件，思路大致一样，一样都有这个问题）。

## 关于作者

前端小白，更多是整理自己的解决思路，写法上也是入门级水平，自知一定有极大改进空间，欢迎大神批评、指正、鼓励
