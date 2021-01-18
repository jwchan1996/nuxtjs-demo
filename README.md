# NuxtJS 基础

[01-基础项目](https://github.com/jwchan1996/nuxtjs-demo/tree/main)  
[02-路由目录规则](https://github.com/jwchan1996/nuxtjs-demo/tree/02-router)  
[03-路由跳转](https://github.com/jwchan1996/nuxtjs-demo/tree/03-router-link)  
[04-动态路由](https://github.com/jwchan1996/nuxtjs-demo/tree/04-dynamic-router)  
[05-嵌套路由](https://github.com/jwchan1996/nuxtjs-demo/tree/05-nest-router)  
[06-自定义路由](https://github.com/jwchan1996/nuxtjs-demo/tree/06-custom-router)  
[07-视图-模板](https://github.com/jwchan1996/nuxtjs-demo/tree/07-views-template)  
[08-视图-布局](https://github.com/jwchan1996/nuxtjs-demo/tree/08-views-layout)  
[09-异步数据-asyncData 方法](https://github.com/jwchan1996/nuxtjs-demo/tree/09-asyncData)  
[10-异步数据-上下文对象](https://github.com/jwchan1996/nuxtjs-demo/tree/10-context)

## Nuxt.js 介绍

### 是什么

- 官网：[https://zh.nuxtjs.org/](https://zh.nuxtjs.org/)
- GitHub 仓库：[https://github.com/nuxt/nuxt.js](https://github.com/nuxt/nuxt.js)

Nuxt.js 是一个基于 Vue.js 的服务端渲染应用框架，它可以帮我们轻松的实现同构应用。

通过对客户端/服务端基础架构的抽象组织，Nuxt.js 主要关注的是应用的 **UI 渲染**。

我们的目标是创建一个灵活的应用框架，你可以基于它初始化新项目的基础结构代码，或者在已有 Node.js 项目中使用 Nuxt.js。

Nuxt.js 预设了利用 Vue.js 开发**服务端渲染**的应用所需要的各种配置。

除此之外，我们还提供了一种命令叫： `nuxt generate` ，为基于 Vue.js 的应用提供生成对应的静态站点的功能。

我们相信这个命令所提供的功能，是向开发集成各种微服务（Microservices）的 Web 应用迈开的新一步。

作为框架，Nuxt.js 为 `客户端/服务端` 这种典型的应用架构模式提供了许多有用的特性，例如异步数据加载、中间件支持、布局支持等非常实用的功能。

### 特性

- 基于 Vue.js
    - Vue、Vue Router、Vuex、Vue SSR
- 自动代码分层
- 服务端渲染
- 强大的路由功能，支持异步数据
- 静态文件服务
- ES2015+ 语法支持
- 打包和压缩 JS 和 CSS
- HTML 头部标签管理
- 本地开发支持热加载
- 集成 ESLint
- 支持各种样式预处理器： SASS、LESS、 Stylus 等等
- 支持 HTTP/2 推送

### Nuxt.js 框架是如何运作的

![image](https://ae01.alicdn.com/kf/U5426d12a87e049f6826396b09d6d081bx.jpg)

Nuxt.js 集成了以下组件/框架，用于开发完整而强大的 Web 应用：

- Vue.js
- Vue Router
- Vuex
- Vue Server Renderer

压缩并 gzip 后，总代码大小为：57kb （如果使用了 Vuex 特性的话为 60kb）。

另外，Nuxt.js 使用 Webpack 和 vue-loader 、 babel-loader 来处理代码的自动化构建工作（如打包、代码分层、压缩等等）。

## 创建项目

Nuxt 提供了两种方式用来创建项目：

- 使用 create-nuxt-app 脚手架工具
- 手动创建

> 下面是手动创建项目过程

（1）准备

```bash
# 创建示例项目 
mkdir nuxtjs-demo 

# 进入示例项目目录中 
cd nuxtjs-demo 

# 初始化 package.json 文件 
yarn init -y 

# 安装 nuxt 
yarn add nuxt
```

在 `package.json` 文件的 `scripts` 中新增：

```json
"scripts": { 
    "dev": "nuxt" 
},
```

上面的配置使得我们可以通过运行 `yarn dev` 来运行 `nuxt` 。

（2）创建页面并启动项目

创建 `pages` 目录：

```bash
mkdir pages
```

创建我们的第一个页面 `pages/index.vue` ：

```html
<template> 
    <h1>Hello world!</h1> 
</template>
```

然后启动项目：

```bash
yarn dev
```

现在我们的应用会在 `http://localhost:3000` 上运行。

> 注意：Nuxt.js 会监听 pages 目录中的文件更改，因此在添加新页面时无需重新启动应用程序。

（3）Nuxt 中的基础路由

Nuxt.js 会依据 `pages` 目录中的所有 `*.vue` 文件生成应用的路由配置。

假设 `pages` 的目录结构如下：

```bash
pages/ 
--| user/ 
-----| index.vue 
-----| one.vue 
--| index.vue
```

那么，Nuxt.js 自动生成的路由配置如下：

```javascript
router: { 
    routes: [ 
        { 
            name: 'index', 
            path: '/', 
            component: 'pages/index.vue' 
        },
        { 
            name: 'user', 
            path: '/user', 
            component: 'pages/user/index.vue' 
        },
        { 
            name: 'user-one', 
            path: '/user/one', 
            component: 'pages/user/one.vue' 
        } 
    ] 
}
```

## Nuxt 路由

Nuxt.js 依据 `pages` 目录结构自动生成 [vue-router](https://github.com/vuejs/vue-router) 模块的路由配置。

### 基础路由

假设 `pages` 的目录结构如下：

```bash
pages/ 
--| user/ 
-----| index.vue 
-----| one.vue 
--| index.vue
```

那么，Nuxt.js 自动生成的路由配置如下：

```javascript
router: { 
    routes: [ 
        { 
            name: 'index', 
            path: '/', 
            component: 'pages/index.vue' 
        },
        { 
            name: 'user', 
            path: '/user', 
            component: 'pages/user/index.vue' 
        },
        { 
            name: 'user-one', 
            path: '/user/one', 
            component: 'pages/user/one.vue' 
        } 
    ] 
}
```

### 路由导航

- a 标签
- `<nuxt-link>` 组件
- 编程式导航

### 动态路由

在 Nuxt.js 里面定义带参数的动态路由，需要创建对应的**以下划线作为前缀**的 Vue 文件或目录。

以下目录结构：

```bash
pages/ 
--| _slug/ 
-----| comments.vue 
-----| index.vue 
--| users/ 
-----| _id.vue 
--| index.vue
```

Nuxt.js 生成对应的路由配置表为：

```javascript
router: { 
    routes: [ 
        { 
            name: 'index', 
            path: '/', 
            component: 'pages/index.vue' 
        },
        { 
            name: 'users-id', 
            path: '/users/:id?', 
            component: 'pages/users/_id.vue' 
        },
        { 
            name: 'slug', 
            path: '/:slug', 
            component: 'pages/_slug/index.vue' 
        },
        {
            name: 'slug-comments', 
            path: '/:slug/comments', 
            component: 'pages/_slug/comments.vue' 
        } 
    ]
}
```

你会发现名称为 `users-id` 的路由路径带有 `:id?` 参数，表示该路由是可选的。如果你想将它设置为必选的路由，需要在 `users/_id` 目录内创建一个 `index.vue` 文件。

### 嵌套路由

你可以通过 vue-router 的子路由创建 Nuxt.js 应用的嵌套路由。

创建内嵌子路由，你需要添加一个 Vue 文件，同时添加一个与**该文件同名**的目录用来存放子视图组件。

> Warning: 别忘了在父组件( .vue 文件) 内增加 <nuxt-child/> 用于显示子视图内容。

假设文件结构如：

```bash
pages/ 
--| users/ 
-----| _id.vue 
-----| index.vue 
--| users.vue
```

Nuxt.js 自动生成的路由配置如下：

```javascript
router: { 
    routes: [ 
        { 
            path: '/users', 
            component: 'pages/users.vue', 
            children: [ 
                { 
                    path: '', 
                    component: 'pages/users/index.vue', 
                    name: 'users' 
                },
                { 
                    path: ':id', 
                    component: 'pages/users/_id.vue', 
                    name: 'users-id' 
                } 
            ] 
        } 
    ] 
}
```

### 路由配置

[https://zh.nuxtjs.org/api/configuration-router](https://zh.nuxtjs.org/api/configuration-router)

## 视图

![image](https://ae01.alicdn.com/kf/U5426d12a87e049f6826396b09d6d081bx.jpg)

### 模板

### 布局

（1）默认布局

（2）自定义布局

（3）错误页面

### 页面

### HTML 页面头部

（1）默认 Meta 标签

（2）个性化特定页面的 Meta 标签

## 异步数据

### asyncData 方法

Nuxt.js 扩展了 Vue.js，增加了一个叫 **asyncData** 的方法，使得我们可以在设置组件的数据之前能异步获取或处理数据。

- 基本用法
    - 它会将 asyncData 返回的数据融合组件 data 方法返回数据一并给组件
    - 调用时机：服务端渲染期间和客户端路由更新之前
- 注意事项
    - 只能在页面组件中使用，即 pages 目录下
    - 没有 this，因为它是在组件初始化之前被调用的

### 上下文对象

### 错误处理

## 生命周期

![image](https://ae01.alicdn.com/kf/Ud4458bacfe104120895dcf56864f3f4cz.jpg)

## 插件

## 模块

## Vuex 状态管理

> [https://nuxtjs.org/guide/vuex-store](https://nuxtjs.org/guide/vuex-store)

## Nuxt 渲染流程

下图阐述了 Nuxt.js 应用一个完整的服务器请求到渲染（或用户通过 `<nuxt-link>` 切换路由渲染页面）的流程：

![image](https://ae01.alicdn.com/kf/U2fd3467b4d084749b0f5e1f8946fdcac9.jpg)

## Nuxt 常见问题

> [https://zh.nuxtjs.org/faq/](https://zh.nuxtjs.org/faq/)

## Nuxt 官方示例

> [https://zh.nuxtjs.org/examples](https://zh.nuxtjs.org/examples)