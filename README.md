# 基于layui实现的省市县区三级联动下拉选择器

## 关于layui 
这里不做介绍，[直戳我阅读](http://layui.com)

## 关于本省市区级联下拉选择器 
本选择器已经将它封装成一个layui的插件，使用起来非常方便，支持一个页面中使用多个省市区选择器，并且支持选择结果回调，支持自定义lay-filter。

## 使用方法以及一些约定
1. html部分  
 整个选择器需要使用一个父标签包裹，如下使用了id="area-picker"，并且分别给省、市、区的select加上province-selector、city-selector、county-selector，用来区分对应的内容标签，这里也可以自定义lay-filter，当一个页面有多个省市区选择器的时候，需要每组lay-filter命名不一样，因此，最好的方式是，不手动设置lay-filter。每个select可以指定初始值，在select上写data-value=""即可。初始值也可以通过js设置。
```html
<div class="layui-form-item" id="area-picker">
            <div class="layui-form-label">网点地址</div>
            <div class="layui-input-inline" style="width: 200px;">
              <select name="province" class="province-selector" data-value="广东省" lay-filter="province-1">
                <option value="">请选择省</option>
              </select>
            </div>
            <div class="layui-input-inline" style="width: 200px;">
              <select name="city" class="city-selector" data-value="深圳市" lay-filter="city-1">
                <option value="">请选择市</option>
              </select>
            </div>
            <div class="layui-input-inline" style="width: 200px;">
              <select name="county" class="county-selector" data-value="龙岗区" lay-filter="county-1">
                <option value="">请选择区</option>
              </select>
            </div>
          </div>
```
2.js部分  
引入layarea, 根据指定选择器渲染标签
```js
//配置插件目录
layui.config({
    base: './mods/'
    , version: '1.0'
});
//一般直接写在一个js文件中
layui.use(['layer', 'form', 'layarea'], function () {
    var layer = layui.layer
        , form = layui.form
        , layarea = layui.layarea;

    layarea.render({
        elem: '#area-picker',
        // data: {
        //     province: '广东省',
        //     city: '深圳市',
        //     county: '龙岗区',
        // },
        change: function (res) {
            //选择结果
            console.log(res);
        }
    });
});
```
3.完整示例  
请直接查看index.html源码。

## 相关问题
代码能用