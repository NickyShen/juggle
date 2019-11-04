# juggle

## 介绍
    阿里推出飞冰来进行页面搭建，但是飞冰的物料开发不是想象中的简单。
    开发此项目，可以直接使用市面上线程的组件库（iview, vux, Element），也可以基于现有组件库封装自定义组件。
    通过拖拽布局，生成页面配置 json 文件，再通过json动态渲染页面。
    此项目包含两部分，report.html模板渲染页面以及一个页面配置服务。
    页面配置服务用来拖拽生成页面配置json文件，目前还在实现中，初期直接使用本地配置文件。
    report.html模板渲染页面已经实现并已在线上进行验证
    
### 项目地址：http://juggle.isjs.cn/index.html

### 配置项文档：https://github.com/adminV/juggle/blob/master/OPTIONS.md

### 方案说明：
    在一个页面上承载多个页面，使页面配置化。首先想为什么这么做？这么做有什么好处？
    第一: 减少重复开发成本，多个页面，多个项目共有的自定义组件，需要有一套公共的仓库来进行维护。
    第二: 将简单工作交给PM或者运营。
    第三: 提高开发效率，以往做一个新页面的开发时间，使用配置生成只需要10分钟。
    
抽象的看我们日常开发的页面，可以分为以下几类：
    1. 活动页  特点是动画样式丰富，活动可复用性高，配置灵活。
    2. 录入页  特点是表单校验，输入项校验。
    3. 回显页  特点是请求单向，没有用户操作。
我们把按钮，输入框，日期选择等称为 元素，
由不同的组合而成的具有特定功能的集合称为  组件，
最终不同的组件集合起来就是一个页面模板。

   我们这次的项目目的就是实现页面模板化，基于现有的element，vuex，iview作为元素库。
基于元素库封装自定义组件。然后通过组件的灵活配置，实现页面模板化。

   页面模板的载体是 report.html 页面
页面模板文件为一个json文件，位于 public/pageConfig 目录下，以 config 开头的js文件。
通过script标签异步引入，配置参数挂载到 window.__pageConfig__ 中，再通过Vue实例向下传递。



