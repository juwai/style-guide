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
  
   /**
   * @ <对该模块的说明及注意事项>
   * @author <作者名字>
   * @createDate <创建日期:YYYY-MM-DD>
   * @dep <依赖模块名称> <对依赖的简要说明，如果没有依赖，这行可以去掉>
   * @param {<参数的数据类型>} <参数名> <参数的简单解释>
   * @return {<返回的数据类型>} <返回值的简单解释>
   */
define(function(){

});
```
**6.函数注释规范(注释位于每个函数头部)**
```

define(function(){
      
      /** 
       * @ 返回已经绑定了事件的数据对象
       * @author Richard@juwai.com  
       * @param {Object} e 事件对象
       * @param {json Object} d data数据(json)
       * @return {Object} 返回一个对像
      */
     return function(e,d){
       
         return {event:e,data:d}
     }
});
```
## 三.Html编写原则
**1.确保单个页面中只有一个H1元素**

**2.可以有多个其他h2,3,4,5标签,但注意该标签有语义化作用，不宜滥用**

**3.除非特殊需求,原则上html标签嵌套不得超过3层**

**4.使用html5标签，页面结构清晰和语义化**

  - 关于h5元素的详细用法和说明请[猛击这里](http://htm5.sinaapp.com/)
  
**5.原则上a标签元素上必须加上title属性，以更好的支持seo**

**6.代码缩进(请保持两个空格的缩进)**
  ```
  <div class="demo">
    <span></span>
  </div>
  ```
**7.注释风格**
```
<!--header start-->
<header>
</header>
<!--header end-->
```

## 四.前端集成管理化工具使用
**1.目前前端构建工具的比较**
  - grunt:
    - 相对的低效：grunt各插件之间是独立的，频繁的IO读写会造成资源的浪费
    - 插件A、插件B之间彼此独立,难以串联
    - 不能对不同的业务等制定不同的开发及部署规范
    - 不能对整站的静态资源进行管理
    - 编译工具滥用、黑盒效应、灵活性差....
  - F.I.S:
    - 管道操作，避免了频繁的文件IO
    - 灵活的配置：强大到令人发指的部署配置(可对不同的项目，进行不同的静态资源部署)
    - 根据静态资源表对整站的静态资源进行管理加载
    - grunt只想安静的做个工具,而F.I.S是工具+开发框架的合集(可以理解F.I.S是一个定制化的Grunt)
    - 文档系统化不足，虽然也有很多文档，但总有管中窥豹的感觉，新手上手困难
  - gulp:
    - 取代grunt
    - 似乎结合了grunt、fis两者的一些特点
    - 学习成本相对于fis来说要低不少（从官方的demo来看）
    - 值得继续关注
**2.FIS安装及使用**
  - 安装node.js
  - 安装fis```npm install -g fis  ```
  - 安装less编译器```npm install -g fis-parser-less ```
