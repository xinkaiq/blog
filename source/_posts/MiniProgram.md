---
title: MiniProgram
date: 2024-03-03 10:27:09
tags: [miniprogram]
---

## Setup (开始)
### 注册微信小程序账号
> Precondition - E-Mail
> 1. 未被微信公众平台注册
> 2. 未被微信开放平台注册
> 3. 未被个人微信号绑定过

1. 在<a href='https://mp.weixin.qq.com'>微信公众平台</a>中：
- 点击导航栏右侧（右上角）`立即注册`
![微信公众平台主页](/images/MiniProgram/signup-1.png)
- 点击左下角`小程序`
![微信公众号注册页面](/images/MiniProgram/signup-2.png)
- 点击`前往注册`
![微信公众号注册页面](/images/MiniProgram/signup-3.png)
- 依次填写`账号信息`、`邮箱激活`、`信息登记`
- 填写完毕可进入如下页面：
![微信小程序个人页面](/images/MiniProgram/signup-finish.png)

### 完善小程序账号信息
- pass

### 小程序开发者ID
点击`开发管理`，即可在`开发者ID`下找到`ID`
![微信小程序开发者ID](/images/MiniProgram/devId.png)
我的id是：`wx7dfa84058dfcd4dc`

### 创建小程序项目
- 安装微信小程序开发工具
    - 略
- 创建微信小程序项目
    - 打开并登录微信小程序开发工具
    - 点击`小程序` -> `+`
    ![微信小程序开发工具](/images/MiniProgram/devtool-1.png)

## <a href="https://developers.weixin.qq.com/miniprogram/dev/reference/configuration/app.html">配置文件</a>
### 全局配置 - <a href="https://developers.weixin.qq.com/miniprogram/dev/reference/configuration/app.html#window">配置window</a>
```
  "window": {
    "navigationBarTitleText": "kaiikay",
    "navigationBarBackgroundColor": "#f3524f",
    "enablePullDownRefresh": true,
    "backgroundColor": "#efefef",
    "backgroundTextStyle": "dark"
  },
```

### 全局配置 - <a href="https://developers.weixin.qq.com/miniprogram/dev/reference/configuration/app.html#tarBar">配置tabbar</a>
`tabBar`字段：
- 定义**小程序顶部、底部tab栏**，用以实现页面之间的快速切换，
- 可以通过`tabBar`配置项指定tab栏的表现，以及`tab`切换时显示的对应页面
```
  "tabBar": {
    "selectedColor": "#000000", // text color if selected
    "color": "#666666",         // text color while not been selected
    "borderStyle": "black",     // border color
    "position": "bottom",       // default: bottom. If top, no icons images would be shown
    "list": [
      {
        "pagePath": "pages/index/index",                // target page path
        "text": "Home",                                 // target page name
        "iconPath": "src/icon/icon-home-outline.png",   // target page icon image while not been selected
        "selectedIconPath": "src/icon/icon-home.png"    // target page icon image if selected
      },
      {
        "pagePath": "pages/cate/cate",
        "text": "Category",
        "iconPath": "src/icon/icon-menu-outline.png",
        "selectedIconPath": "src/icon/icon-menu.png"
      },
      {
        "pagePath": "pages/cart/cart",
        "text": "Cart",
        "iconPath": "src/icon/icon-cart-outline.png",
        "selectedIconPath": "src/icon/icon-cart.png"
      },
      {
        "pagePath": "pages/profile/profile",
        "text": "Me",
        "iconPath": "src/icon/icon-user-outline.png",
        "selectedIconPath": "src/icon/icon-user.png"
      }
    ]
  },
```

### 全局配置 - <a href="https://developers.weixin.qq.com/miniprogram/dev/reference/configuration/app.html#networkTimeout">配置networkTimeout</a>

| 属性 | 类型 | 默认值 | 说明 |
| ---- | ---- | ---- | ---- |
| request | number | 60000 | `wx.request`的超时时间，单位：毫秒 |
| connectSocket | number | 60000 | `wx.connectSocket`的超时时间，单位：毫秒 |
| uploadFile | number | 60000 | `wx.uploadFile`的超时时间，单位：毫秒 |
| downloadFile | number | 60000 | `wx.downloadFile`的超时时间，单位：毫秒 |

### <a href="https://developers.weixin.qq.com/miniprogram/dev/reference/configuration/page.html">页面配置（局部配置）</a>
每一个小程序也可以使用自己的`.json`文件来对本页面的窗口表现进行配置
> 注意：
> 页面配置文件的属性和全局配置文件中的`window`属性几乎一致，只不过这里不需要额外指定`window`字段，因此如果出现相同的配置项，页面中配置项***会覆盖全局配置文件中相同的配置项***

### <a href="https://developers.weixin.qq.com/miniprogram/dev/devtools/projectconfig.html">项目配置文件</a>和配置sass
#### 1. 项目配置文件
在项目创建的时候，每个项目的根目录生成两个`config.json`文件，用于保存开发者在工具上做的个性化配置，例如和编译有关的配置。
当重新安装微信开发者工具或者换电脑时，只要载入同一个项目的代码包，开发者工具就会自动恢复到当时开发项目的个性化配置。
> 两个`config.json`文件
> `project.config.json`：项目配置文件，常用来进行配置公共的配置
> `project.private.config.json`：项目私有的配置，常用来配置个人的配置

NOTE:
> 1. `project.private.config.json`写到`.gitignore`避免版本管理的冲突
> 2. 写最终编译结果有关的设置**必须**设置到`project.config.json`中
#### 2. 配置`sass`
打开`project.config.json`，并修改`setting`
```
  "setting": {
    "useCompilerPlugins": [
      "sass"
    ],
    ...
  }
```
修改page下面的`.wxss`后缀名为`.scss`

### <a href="https://developers.weixin.qq.com/miniprogram/dev/reference/configuration/sitemap.html">sitemap.json</a>
- `sitemap.json`文件：配置小程序及其页面是否允许被微信索引，提高小程序在微信内部被用户搜到的概率
- 注意：没有`sitemap.json`则默认所有页面都能被索引

## <a href="https://developers.weixin.qq.com/miniprogram/dev/framework/app-service/page-life-cycle.html">生命周期</a>
- `onLoad(Object[json] query)`
  - 页面加载时出发。一个页面只会调用一次，可以在`onLoad()`的参数中获取打开当前页面路径中的参数
- `onShow()`
  - 页面显示/切入前台时触发
  - 一个页面可以触发很多次
- `onReady()`
  - 页面**初次**渲染完成时触发
  - 一个页面只会调用一次
- `onHide()`
  - 页面隐藏/切入后台时触发
  - 一个页面可以触发很多次
- `onUnload()`
  - 页面卸载时触发
<img src="https://res.wx.qq.com/wxdoc/dist/assets/img/page-lifecycle.2e646c86.png" alt="生命周期图" />

## 视图结构`wxml`
- 数据绑定
  - 单个绑定
    ```
      <view>{{ name }}</view>
    ```
  - object绑定
    ```
      <view>
        <view>ID: {{ user.id }}</view>
        <view>name: {{ user.name }}</view>
        <view>age: {{ user.age }}</view>
      </view>
    ```
  - list绑定
    - 可以用`wx:for`循环读取。
    - `wx:for-item`可以重命名循环变量名，默认为`item`。
    - `wx:key`可以设置`key`以提高性能
      ```
        <view wx:for="{{ users }}" wx:for-item="user" wx:key="id">
          <view>[{{ index }}] ID: {{ user.id }}</view>
          <view>name: {{ user.name }}</view>
          <view>age: {{ user.age }}</view>
        </view>
      ```
  - `wx:if`
    - `wx:if`语法块中不能参杂其他无关的代码
      ```
        <block wx:if="{{ ... }}">
          <view>...</view>
        </block>
        <block wx:elif="{{ ... }}">
          <view>...</view>
        </block>
        <block wx:else>
          <view>...</view>
        </block>
      ```
  - 专门写`wx:`的标签：`<block>`
    - `<block>`不会出现在dom上面
      ```
        <block wx:for="{{ users }}" wx:for-item="user" wx:key="id">
          <view>[{{ index }}] ID: {{ user.id }}</view>
          <view>name: {{ user.name }}</view>
          <view>age: {{ user.age }}</view>
        </block>
      ```
    - 推荐写法
      ```
        <block wx:for="{{ users }}" wx:for-item="user" wx:key="id">
          <view>
            <view>[{{ index }}] ID: {{ user.id }}</view>
            <view>name: {{ user.name }}</view>
            <view>age: {{ user.age }}</view>
          </view>
        </block>
      ```

- 修改&刷新数据`this.setData({key: value, key: value, ...})`

## 小程序常用的组件
1. `view`
2. <a href="https://developers.weixin.qq.com/miniprogram/dev/component/swiper.html">`swiper`</a> and `swiper-item`
3. `image`
4. `text`
5. `navigator`
6. `scroll-view`
7. 字体图标

### 1. `view`组件
`view` == `div`
### 2. <a href="https://developers.weixin.qq.com/miniprogram/dev/component/swiper.html">`swiper`组件</a>和`swiper-item`组件
- 在小程序中，提供了`swiper`组件和`swiper-item`组件实现轮播图
- `swiper`滑块视图容器，其中自能放置`swiper-item`组件
- `swiper-item`只可放置在`swiper`组件中，宽高自动设置为100%，代表`swiper`中的每一项
### 3. <a href="https://developers.weixin.qq.com/miniprogram/dev/component/image.html">`image`组件</a>
属性：
1. `src`属性：图片资源地址
2. `mode`：图片裁剪、缩放模式
3. `show-menu-by-longpress`：长按图片显示菜单
4. `lazy-load`：图片懒加载（上下三屏）
```
<view class="swiper">
  <swiper
    autoplay
    circular
    interval="2000"
    indicator-dots
    indicator-color="#fff"
    indicator-active-color="#f3514f"
  >
    <swiper-item>
      <image src="../../src/img/background-1.jpg" mode="" show-menu-by-longpress lazy-load />
    </swiper-item>
    <swiper-item>
      <image src="../../src/img/background-2.jpg" mode="" show-menu-by-longpress lazy-load />
    </swiper-item>
    <swiper-item>
      <image src="../../src/img/background-3.jpg" mode="" show-menu-by-longpress lazy-load />
    </swiper-item>
  </swiper>
</view>
```
### 4. <a href="https://developers.weixin.qq.com/miniprogram/dev/component/text.html">`text`组件</a>
在小程序中，如果要渲染文本，需要使用text组件，常用的属性有2个：
1. `user-select`：文本是否可选，用于长按选择文本
2. `space`：显示连续空格
    - `space="ensp"`：中文字符空格一半大小
    - `space="emsp"`：中文字符空格大小
    - `space="nbsp"`：根据字体设置的空格大小
    ```
    <text user-select space="emsp">一二  三四 (emsp)</text>
    <text user-select space="ensp">一二  三四 (ensp)</text>
    <text user-select space="nbsp">一二  三四 (nbsp)</text>
    ```
    ![space效果](/images/MiniProgram/text-space.png)

注意事项：
1. 除了文本节点意外的其他节点都无法长安选中
2. `text`组件内只支持`text`嵌套
### 5. <a href="https://developers.weixin.qq.com/miniprogram/dev/component/navigator.html">`navigator`组件</a>
在小程序中，如果需要进行跳转，需要使用`navigator`组件，常用的属性有2个：
1. `url`：当前小程序内的跳转链接
2. `open-type`：跳转方式
    - `navigate`：保留当前页面，跳转到应用内的某个页面。但是不能跳到`tabbar`页面
    > `tabBar`页面：在`tabBar(app.json)`的`list`里面的页面就是`tabBar`页面
    - `redirect`：关闭当前页面，跳转到应用内的某个页面。但是不能跳到`tabbar`页面
    - `switchTab`：跳转到`tabBar`页面，并关闭其他所有非`tabBar`页面
    - `reLaunch`：关闭所有页面，打开到应用内的某个页面
    - `navigateBack`：关闭当前页面，返回上一页或者多级页面

注意事项：
1. 路径后可以带参数。与URL参数方法一致
2. `open-type="switchTab"`时，不支持传参

坑：
- 问题1：
    - `<navigator url="pages/list/list">到商品列表页面</navigator>`点击没有效果
    - 解决方法：确保url以`/`开头，即：`<navigator url="/pages/list/list">到商品列表页面</navigator>`
### 6. <a href="https://developers.weixin.qq.com/miniprogram/dev/reference/wxml/template.html">`template`组件</a>
- static：不用`data`
  ```
    <!-- define template -->
    <template name="msgItemStatic">
      <view>
        <view>ID: 1</view>
        <view>name: kaiikay</view>
        <view>age: 18</view>
      </view>
    </template>
    <!-- use template -->
    <template is="msgItemStatic" data="" />
  ```
- dynamic：用`data`
  ```
    <!-- define template -->
    <template name="msgItemDynamic">
      <view>
        <view>ID: {{ id }}</view>
        <view>name: {{ name }}</view>
        <view>age: {{ age }}</view>
      </view>
    </template>
    
    <!-- use template -->
    <template is="msgItemDynamic" data="{{ ...user }}" />
  ```

### 7. <a href="https://developers.weixin.qq.com/miniprogram/dev/reference/wxml/import.html">`include`组件和`import`组件</a>
> 动态文件用相对地址；静态文件用绝对地址
- `include`引用
  - 将此代码块直接复制到需要的地方（ctrl c+v）
    ```
      <view>--- include ---</view>
      <include src="/template/user.wxml" />
    ```
- `import`引用
  - 相当于正常引用，可以调用其中某个或者某几个template。（想到于调用参数）
    ```
      <!-- import -->
      <import src="/template/user-import.wxml" />
      <!-- call -->
      <template is="user-template" data="{{ user }}" />
    ```
- `include` v.s. `import`
  - 定义方式不一样
  - 引用的方式不一样，`include`相当于复制代码过来，`import`相当于调用函数
  - 数据的传递不一样，`include`直接获取`js`中的数据，`import`必须通过`template`的`data`属性获取

## 小程序的样式`wxss`
约等于`css`。包含了`css`当中大部分的特性，同时对`css`进行了扩充及修改
- 新增了尺寸单位`rpx` (max: 750rpx)
  - 容器最好用`rpx`
  - 字体最好用`px`
- 提供了**全局样式**和**局部样式**
  - `app.wxss`最为全局样式
  - 局部页面样式`page.wxss`仅对当前页面生效`app.wxss<page.wxss<行级`
- `wxss`仅支持部分`css`选择器
  - `.class`
  - `#id`
  - `element`
  - `element, element`
  - `::after`
  - `::before`
- 样式导入
  - 使用`@import`语句可以导入外联样式表
    ```
      @import '/style/font.wxss'
    ```
- 页面全局样式
  ```
    page {
      background: #888
      ...
    }
  ```
- 动画：`animate.css`

### flex
- `flex`主轴和交叉轴
  - `flex-direction: row | row-reverse | column | column-reverse`
- `flex`换行
  - `flex-wrap: nowarp | wrap | wrap-reverse`
- `flex`主轴和交叉轴的对齐方式
  - 主轴：`justify-content: flex-start | flex-end | center | space-between | space-around;`
  - 交叉轴：`align-items: flex-start | flex-end | center | stretch | baseline;`
- 开启`flex`布局（项目变成flex容器）
  ```
    .class {
      display: flex
    }
  ```
- 开启`flex`布局以后，子元素的`float`, `clear`和`vertical-align`属性将失效。定位不受影响
- 水平垂直居中
  ```
    selector {
      justify-content: center;
      align-items: center;
    }
  ```
