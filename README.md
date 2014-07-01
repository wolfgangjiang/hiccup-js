===
hiccup.js
===

这是一个模仿clojure的[hiccup](https://github.com/weavejester/hiccup)，用javascript写的html模版引擎，可以直接用在页面上，而且模版完全符合javascript语法，支持用`ForEach`渲染一个集合。一个基本的例子是：

    ["p", {},
     ["div", {"class": "obj-spec"}, 
     ["div", {"class": "actable"},
      ["span", {}, "类："],
      ["a", {"class": "class-name",
             "href": "javascript:start_rename('" + 
             class_name + "', null);"},
       class_name],
       ["button", {"class": "remove-class"}, "删除类"],
       ["button", {"class": "add-field"}, "添加一个字段"]],
      [hiccup.ForEach, _.keys(obj_spec["fields"]), 
       function (field_name) {                      
         return make_field_hiccup(obj_spec, field_name);
       }]]]

使用时，只需要在项目中引入`hiccup.js`文件，然后执行

    hiccup(["h1", "Hello Hiccup"])
    
即可。

这样的模版可以嵌套，可以作为函数的参数与返回值，可以内嵌raw html。
