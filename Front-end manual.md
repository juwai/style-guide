# 前端开发手册(beta)
## 一.css编写原则
**1.使用less书写并最终编译为css文件**

**2.使用模块化的概念来组织css文件(如页头页尾可以分成不同的less文件,并最终编译进css文件),列主要模块如下:**
* header.less
* footer.less
* slider.less(侧边栏控件)
* pager.less(翻页控件)
* page.less(每个单页样式)
* list.less(列表控件)
* tab.less(tab控件)
* form.less(表单控件)
* combobox.less(下拉选择框)
* common.less(包含cssreset及通用样式)
* Mixins.less(包含一些less的公共变量，可以复用)

**3.css组织过程(以首页为例):**

* header.less+footer.less+common.less+Mixins.less →编译→index.css
* 每个页面保持一个单独的样式，最多不超过2个

**4.页面css组织方案**
* 推荐使用粗粒度基类+UI类库的方式进行class编码，例如:
```
<div class="fl row recommend"></div>
```
- fl和row是基类,recommend是ui类(具有长宽，背景等属性)，可以添加多个基类，但不建议添加过多的ui类

**5.css图标解决方案**
* 减少http请求数，字体可缩放不变形，图标颜色自定义
* 使用 [font-awesome库](http://fortawesome.github.io/Font-Awesome/)
* 使用 [icomoon在线字体库](https://icomoon.io/app/)

**6.css类名编写规则**
* 好的命名方式 .jw-page-menu
* 不好的命名方式 .jw-bar
* 命名规则 .jw-(ui模块名,如page,tab)-(功能描述)
* 尽量少用id 命名,不利于复用

## 二.js编写原则

**1.使用类库**
* jquery (v1.7.2-v1.9.1)
* require.js (异步脚本加载器)

**2.模块化原则**
- UI前端模块化(将常见的使用模块包装成单独的js文件),大致的模块猜想如下:
  - UI.Form.js(表单操作模块,UI表示命名空间)
  - UI.ComboBox.js
  - UI.CheckBox.js
  - UI.DatePicker.js
  - UI.DataGrid.js
  - UI.Alert.js
  - UI.dialog.js
  - UI.tooltip.js
  - UI.animate.js
  - UI.confim.js
  - UI.waterfall.js
  - UI.imagelazyload.js(利用jquery插件实现)
  - modal.js(主要用于数据拉取，即数据模型)
- 模块书写方式
  - 举例,alert模块(alert.js):
  ```
  define(['$ui'],function(ui){
     ui.alert=function(setting){
          var def={}
          var option=$.extend(def,setting);
          ........................
       }
     return ui;
  });
  ```
  - 页面调用:
  ```
  require(['domReady!','alert'],function(domReady,Alert){
            Alert("xxxx");
   });
  ```
  - 作为模块，本身应该降低与其他模块之间的耦合度，但过度的松耦合又会造成碎片化的问题，应注意。
- 模块定义
  - ui模块(用于元素的表现层)
  - data数据模块(即model层)
  - event模块(事件绑定模块)
  - modal.js

    ```
      define(['jquey','JW_config'],function($,con){
            con.data.getCategory=function(setting){
                     var def={}
                     var $data;
                     var option=$.extend(def,setting);
                     $.post(option.url,option.data,function(json){
                            $data=json
                    });     
                    return $data; 
              }
               return con.data; 
      });
    ```
  - event.js(用于绑定模型和ui层)
  ```
    define(['modal','JW_config'],function(m,con){
              con.event. autoCompalte=function(m.getCategory){
                      var model=m.getCategory();
                    //dosomething
               }
   });
  ```
**3.事件绑定**
- 错误方法
```
 $('ul > li').onclick(function(){
   //code here
});
```
- 正确方法
```
 my.dosomething=function(){
  ////code here
}
 $('ul > li').onclick(my.dosomething());
```

- 在页面中调用事件
```
require(['JW_config','event'],function(con,event){
    $('ul > li').on('click',event.autoCompalte);
    $('#someid').on('mouseover',event.comBox);
});
```
**4.变量定义及约定**
- 禁止单个全局变量暴露给外部

 ```
  var T=20;
```
* 以命名空间的形式定义全局变量(JW_cofig.js)
```
//变量声明应该有语义，禁止声明无语义的变量
define(function(){  
        var JW=window.JW||{};
             JW.global={
                  a:1,
                  b:2
                }
     return JW;
});
```
**5.模块注释规范(注释位于每个模块文件的头部)**
```
  /*
      <summary>
      depiction：<对该模块的说明及注意事项>
      </summary>
      <dep="<模块依赖>"><模块依赖说明,没有可以删除该节点></dep>
      <returns>
      <对方法返回值的说明，该说明必须明确说明返回的值代表什么含义>
      </returns>
      Writer：作者名
      CreateDate：<方法创建日期，格式：YYYY-MM-DD>
  */
define(function(){

});
```
**6.函数注释规范(注释位于每个函数头部)**
```

define(function(){
      
      /* 
        <summary>
         depiction：返回事件和数据绑定对象
         </summary>
        <dep="jquery">该函数依赖jquery库</dep>
        <paramname="e">event.js传入的event事件对象</param>
        <paramname="d">data.js传入的data对象</param>
        <returns>
        返回一个和当前事件相关联的event对象，并交由页面js处理该对象
        </returns>
        author：Richard
        CreateDate：2014-11-20
      */
     return function(e,d){
       
         return {event:e,data:d}
     }
});
```
