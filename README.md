# 首次下载记得安装Npm依赖

```JavaScript
// 安装
npm install 
```



# 目录介绍
```
|-- common                           // 公用目录(包含全局样式，全局js等)
|     └─ css
|         └─ common.scss
|     └─ js
|         └─ util.js
|     └─ http
|         └─ http.api.js             // 统一接口存放
|         └─ http.interceptor.js     // 请求配置
|-- components                       // 公用组件目录
|     └─ a.vue                       // 公用的a组件
|-- pages                            // 业务页面文件存放目录 以入口进行文件夹分类
|     └─ index                       // index页面主体文件夹
|     |    └─ index.vue              // 页面
|     └─ my                          // my页面主体文件夹
|     |    └─ my.vue                 // 页面
|     └─ subpages                    // 业务页面 分包
|          └─ acount
|               └─ acount.vue
|-- static                           // 存放应用引用静态资源（如图片、视频等）的地方，注意：静态资源只能存放于此
|     └─ image                       
|-- store                            // 状态管理
|     └─ index.js 
|-- untils                           // 管理工具
|-- main.js                          // 初始化入口文件
|-- App.vue                          // 应用配置，用来配置App全局样式以及监听
|-- manifest.json                    // 配置应用名称、appid、logo、版本等打包信息
|-- pages.json                       // 配置页面路由、导航条、选项卡等页面类信息
```

# Uniapp的路由与页面跳转

Uniapp 集成多端的跳转方式，以标签 navigator 及封装 API 的形式控制应用内的跳转。

如果我想要首页跳转到列表页面并传一些参数：

```javascript
// 在起始页面跳转到list.vue页面并传递参数
// 该页面需要在 pages.json 注册
uni.navigateTo({
    url: '/pages/list/list?id=1&name=uniapp'
});

// 或者使用标签形式跳转
<navigator url="/pages/list/list?id=1&name=uniapp">去列表</navigator>
```

```javascript
// 去list.vue接受参数
export default {
    onLoad: function (option) { //option为object类型，会序列化上个页面传递的参数
        console.log(option.id); //打印出上个页面传递的参数。
        console.log(option.name); //打印出上个页面传递的参数。
    }
}
```

我们还可以使用下面的几个 API 操作页面跳转:

```html
uni.navigateTo() 保留当前页面，跳转到应用内的某个页面，使用 uni.navigateBack 可以返回到原页面。
uni.redirectTo() 关闭当前页面，跳转到应用内的某个页面。
uni.reLaunch() 关闭所有页面，打开到应用内的某个页面。reLaunch 可以打开任意页面。
uni.switchTab() 跳转到 tabBar 页面，并关闭其他所有非 tabBar 页面。switchTab 只能打开 tabBar 页面。
```

注意：

```html
* navigateTo, redirectTo 只能打开非 tabBar 页面。
* 页面跳转路径有层级限制，不能无限制跳转新页面(10层)
* 跳转到 tabBar 页面只能使用 switchTab 跳转
* 路由 API 的目标页面必须是在 pages.json 里注册的 vue 页面。如果想打开 web url，在 App 平台可以使用 plus.runtime.openURL 或 web-view 组件；H5 平台使用 window.open；小程序平台使用 web-view 组件（url需在小程序的联网白名单中）。在 hello uni-app 中有个组件 ulink.vue 已对多端进行封装，可参考。
```

如果使用标签形式进行跳转改变标签 `open-type`属性即可

```html
<navigator url="navigate/navigate?title=navigate" open-type="navigate">
    跳转到新页面
</navigator>
```
