

* 使用npm

```sh
# 如果选择npm创建项目再执行
$ npm create vite@latest
```

* 使用yarn，如果电脑没有安装yarn `cnpm i yarn -g`

```sh
$ yarn create vite
```

* 使用pnpm：如果电脑尚未安装 pnpm `cnpm i pnpm -g`

```
$ pnpm create vite
```

| 对比                     | yarn                       | npm                      | pnpm                                               |
| ------------------------ | -------------------------- | ------------------------ | -------------------------------------------------- |
| 初始化                   | yarn init                  | npm init                 | 利用硬链接和符号连接来避免复制所有本地缓存资源文件 |
| 安装依赖                 | yarn install 或者yarn      | npm install 或 npm i     | pnpm install                                       |
| 新增依赖                 | yarn add vant              | npm i vant -S            | pnpm i vant                                        |
| 删除依赖                 | yarn remove vant           | npm uninstall vant -S    |                                                    |
| 删除devDependencies 依赖 |                            | npm uninstall vant -D    |                                                    |
| 更新依赖                 | yarn upgrade               | npm update               | pnpm update                                        |
| 全局安装或者删除         | yarn global remove vue-cli | npm uninstall vue-cli -g |                                                    |
| 同时下载多个             | yarn add axios vue-axios   | npm i axis vue-axios -S  |                                                    |

# 1.创建项目

```sh
$ cnpm init vue@latest
```

```sh
|- vue3-admin-app  # 项目名称
	|- node_modules  # 项目依赖包
  |- public
  	favicon.ico 	 # 网页图标
  |- src					 # 写代码的主场
  	|- assets			 # 资源文件
  		base.css     # 基础样式
  		logo.svg     # logo
  		main.css     # 项目样式
		|- components  # 自定义组件
    	|- icons     # 图标组件
  		HelloWorld.vue # 自定义组件
  		TheWelcome.vue # 自定义组件
  		welcomeItem.vue # 自定义组件
  	|-router       # 路由文件夹
  		index.js     # 路由配置
  	|- stores      # 状态管理器文件夹
  		counter.js   # 状态管理器模块
  	|- views       # 项目页面组件
  		AboutView.vue # 页面
  		HomeView.vue  # 页面
  	App.vue         # 项目根组件
  	main.js         # 项目入口文件
  .eslintrc.cjs     # 代码格式化说明
  .gitignore        # git上传忽略文件
  .prettierrc.json  # 格式化配置
  index.html        # 页面模版
  package.json      # 项目依赖说明以及运行命令
  README.md 				# 说明文档
  vite.config.js			 # vite的配置文件
```

# 2.准备工作

?？样式处理 css、sass、less 、stylus

sass、less、stylus 为 css 预处理器

?? 本项目用什么，建议大家先选择UI组件库（element-plus / ant-design-vue）

* 样式 css - sass - 可以重新创建项目

  ```sh
  # 需要安装
  $ cnpm i sass -D
  ```

  使用重置样式表

  ```sh
  # 需要安装
  $ cnpm i normalize.css -D
  ```

  ```ts
  // src/main.js
  import { createApp } from 'vue'
  import { createPinia } from 'pinia'
  
  import App from './App.vue'
  import router from './router'
  
  // 重置样式表
  import 'normalize.css/normalize.css'
  
  // import './assets/main.css' // 不使用默认样式
  
  const app = createApp(App)
  
  app.use(createPinia())
  app.use(router)
  
  app.mount('#app')
  
  ```

  

* 路由 vue-router

  ```sh
  # 创建项目时已经选择了，此处不需要安装
  $ cnpm i vue-router -S
  ```

* 状态管理 pinia   /   vuex

  ```sh
  # 创建项目时已经选择了，此处不需要安装
  $ cnpm i pinia -S
  ```

* 数据请求方案 axios / fetch

  ```sh
  # 需要安装
  $ cnpm i axios -S
  ```

* 组件库 element plus   

  ```sh
  # 需要安装(如果安装失败， 更新cnpm）  
  # npm install -g cnpm --registry=https://registry.npmmirror.com
  $ cnpm i element-plus -S
  ```

  > Element-plus 默认使用英文，如果需要使用中文包，如下操作

```js
// src/main.ts
import { createApp } from 'vue'
import { createPinia } from 'pinia'

// 引入UI库 ++++++
import ElementPlus from 'element-plus'
import 'element-plus/dist/index.css'
import zhCn from 'element-plus/dist/locale/zh-cn.mjs'

import App from './App.vue'
import router from './router'

// 重置样式表
import 'normalize.css/normalize.css'

// import './assets/main.css' // 不使用默认样式

const app = createApp(App)

// 配置UI库  ++++++
app.use(ElementPlus, { locale: zhCn })
app.use(createPinia())
app.use(router)

app.mount('#app')

```

* 本地存储   localStorage / store2  /

  ```sh
  # 安装
  $ cnpm i store2 -S
  ```

* 数据可视化 ECharts

  ```sh
  # 安装
  $ cnpm i echarts -S
  ```

# 3.创建主布局文件

```vue
<!-- src/App.vue -->
<script  setup>
</script>

<template>
  <div class="common-layout">
    <el-container>
      <el-aside width="200px">Aside</el-aside>
      <el-container>
        <el-header>Header</el-header>
        <el-main>Main</el-main>
        <el-footer>Footer</el-footer>
      </el-container>
    </el-container>
  </div>
</template>

<style lang="scss">
/* 审查元素从而设定样式 */
html, body, #app, .common-layout, .el-container {
  height: 100%;
}
.common-layout {
  .el-container {
    background-color: #efefef;
    .el-aside {
      background-color: #001529;
    }
    .el-container {
      .el-header {
        background-color: #fff;
      }
      .el-main {
        background-color: #fff;
        margin: 16px;
      }
      .el-footer {
        background-color: #fff;
      }
    }
  }
}
</style>
```

# 4.对于整个系统的设计思路

# 5.设置路由

## 5.1 设置基本布局组件

```vue
<!-- src/layout/index.vue -->
<!-- 后台管理系统两种布局：登录布局 + 其他布局 -->
<script  setup>
</script>

<template>
  <div class="common-layout">
    <el-container>
      <el-aside width="200px">Aside</el-aside>
      <el-container>
        <el-header>Header</el-header>
        <el-main>Main</el-main>
        <el-footer>Footer</el-footer>
      </el-container>
    </el-container>
  </div>
</template>
```

```vue
<!-- src/App.vue -->
<!-- 组合式API中如何使用 组件 -->
<script  setup>
  import Layout from './layout/index.vue'
</script>

<template>
  <Layout />
</template>

<style lang="scss">
/* 审查元素从而设定样式 */
html, body, #app, .common-layout, .el-container {
  height: 100%;
}
.common-layout {
  .el-container {
    background-color: #efefef;
    .el-aside {
      background-color: #001529;
    }
    .el-container {
      .el-header {
        background-color: #fff;
      }
      .el-main {
        background-color: #fff;
        margin: 16px;
      }
      .el-footer {
        background-color: #fff;
      }
    }
  }
}
</style>
```

## 5.2 设置基本页面

### 5.2.1 系统首页

```vue
<!-- src/views/home/index.vue -->
<script  setup></script>

<template>
  <div>系统首页</div>
</template>
```

### 5.2.2 轮播图管理

* 轮播图列表

  * ```vue
    <!-- src/views/banner/list.vue -->
    <script setup>
    </script>
    
    <template>
      <div>轮播图列表</div>
    </template>
    
    ```

  * ```vue
    <!-- src/views/banner/components/home.vue -->
    <script  setup>
    </script>
    
    <template>
      <div>首页轮播图列表</div>
    </template>
    
    ```

  * ```vue
    <!-- src/views/banner/components/kind.vue -->
    <script  setup>
    </script>
    
    <template>
      <div>分类轮播图列表</div>
    </template>
    
    ```

* 添加轮播图

  ```vue
  <!-- src/views/banner/add.vue -->
  <script  setup>
  </script>
  
  <template>
    <div>添加轮播图</div>
  </template>
  
  ```

### 5.2.3 产品管理

```vue
<!-- src/views/pro/list.vue -->
<script  setup>
</script>

<template>
  <div>产品列表</div>
</template>

```

```vue
<!-- src/views/pro/search.vue -->
<script  setup>
</script>

<template>
  <div>筛选列表</div>
</template>


```

### 5.2.4 账户管理

```vue
<!-- src/views/account/admin.vue -->
<script  setup>
</script>

<template>
  <div>管理员列表</div>
</template>

```

```vue
<!-- src/views/account/user.vue -->
<script  setup>
</script>

<template>
  <div>用户列表</div>
</template>

```

### 5.2.5 登录页面

```vue
<!-- src/views/login/index.vue -->
<script  setup>
</script>

<template>
  <div>登录页面</div>
</template>

```

## 5.3 设置路由模块

### 5.3.1 账户管理路由

```js
// src/router/modules/account.js
// @符号代表 src 目录结构
import Layout from '@/layout/index.vue'
import User from '@/views/account/user.vue'
import Admin from '@/views/account/Admin.vue'
export default {
  path: '/account', // 地址栏显示的路径
  redirect: '/account/user', // 当用户输入 /account 路由时，自动跳转到 /account/user 路由
  component: Layout, // 账户管理使用主界面布局结构
  name: 'account', // 给路由起名字 - 命名路由 - 具有唯一性 - 后期会使用
  meta: {
    title: '账户管理', // 左侧菜单栏显示的名字
    icon: 'User' // 左侧菜单栏显示的图标
  },
  children: [ // 代表账户管理下有二级路由
    {
      path: '/account/user',
      component: User,
      meta: {
        title: '用户列表'
      }
    },
    {
      path: '/account/admin',
      component: Admin,
      meta: {
        title: '管理员列表'
      }
    }
  ]
}
```

### 5.3.2 轮播图路由

```js
// src/router/modules/banner.js
import Layout from '@/layout/index.vue'
import BannerAdd from '@/views/banner/add.vue'
import BannerList from '@/views/banner/list.vue'
import BannerHomeList from '@/views/banner/components/home.vue'
import BannerKindList from '@/views/banner/components/kind.vue'
export default {
  path: '/banner',
  name: 'banner',
  redirect: '/banner/list',
  component: Layout,
  meta: {
    title: '轮播图管理',
    icon: 'PictureFilled'
  },
  children: [
    {
      path: '/banner/list',
      component: BannerList,
      redirect: '/banner/list/home',
      meta: {
        title: '轮播图列表'
      },
      children: [
        {
          path: '/banner/list/home',
          component: BannerHomeList,
          meta: {
            title: '首页轮播图'
          },
        },
        {
          path: '/banner/list/kind',
          component: BannerKindList,
          meta: {
            title: '分类页轮播图'
          },
        }
      ]
    },
    {
      path: '/banner/add',
      component: BannerAdd,
      meta: {
        title: '添加轮播图'
      }
    }
  ]
}
```

### 5.3.3 产品管理路由

```js
// src/router/modules/pro.js
import Layout from '@/layout/index.vue'
import ProList from '@/views/pro/list.vue'
import ProSearch from '@/views/pro/search.vue'
export default {
  path: '/pro',
  redirect: '/pro/list',
  component: Layout,
  meta: {
    title: '产品管理',
    icon: 'Fries'
  },
  children: [
    {
      path: '/pro/list',
      component: ProList,
      meta: {
        title: '产品列表'
      }
    },
    {
      path: '/pro/search',
      component: ProSearch,
      meta: {
        title: '筛选列表'
      }
    }
  ]
}
```

### 5.3.4 整合路由

```js
// src/router/index.js

import { createRouter, createWebHistory } from 'vue-router'
// 1.引入自定义分模块的路由
import bannerRoutes from './modules/banner'
import proRoutes from './modules/pro'
import accountRoutes from './modules/account'


// 2.引入主界面布局，生成 首页和登录的路由 -- 常规路由 -- 任何人都可以访问路由
import Layout from '@/layout/index.vue'
import Home from '@/views/home/index.vue'
import Login from '@/views/login/index.vue'




// 3.定义常规路由-任何人可以访问的路由
export const constantRoutes= [
  { // 地址栏输入 /login, 整个页面展示登录页面
    path: '/login',
    component: Login,
    hidden: true
  },
  {
    path: '/',
    redirect: '/home',
    component: Layout,
    children: [
      {
        path: '/home',
        component: Home,
        meta: {
          title: '系统首页',
          icon: 'HomeFilled'
        }
      }
    ]
  }
]

// 4.整合模块路由
export const asyncRoutes = [
  bannerRoutes,
  proRoutes,
  accountRoutes,
]

// 5.合并路由
const router = createRouter({
  // createWebHistory http://localhost:5173/home
  // createWebHashHistory   http://localhost:5173/#/home
  history: createWebHistory(import.meta.env.BASE_URL),
  // routes: constantRoutes.concat(asyncRoutes)
  routes: [...constantRoutes, ...asyncRoutes]
})

export default router

```

### 5.3.5 入口文件配置路由

```ts
// src/main.js
import { createApp } from 'vue'
import { createPinia } from 'pinia'

// 引入UI库
import ElementPlus from 'element-plus'
import 'element-plus/dist/index.css'
import zhCn from 'element-plus/dist/locale/zh-cn.mjs'

import App from './App.vue'
import router from './router'

// 重置样式表
import 'normalize.css/normalize.css'

// import './assets/main.css' // 不使用默认样式

const app = createApp(App)

// 配置UI库
app.use(ElementPlus, { locale: zhCn })
app.use(createPinia())
app.use(router)

app.mount('#app')

```

### 5.3.6 App.vue使用路由

```vue
<!-- src/App.vue -->
<!-- 组合式API中如何使用 组件 -->
<script  setup>
</script>

<template>
  <!-- 路由映射的组件  
    /login   Login
    /pro/list  Layout
  -->
  <RouterView/>
</template>

<style lang="scss">
/* 审查元素从而设定样式 */
html, body, #app, .common-layout, .el-container {
  height: 100%;
}
.common-layout {
  .el-container {
    background-color: #efefef;
    .el-aside {
      background-color: #001529;
    }
    .el-container {
      .el-header {
        background-color: #fff;
      }
      .el-main {
        background-color: #fff;
        margin: 16px;
      }
      .el-footer {
        background-color: #fff;
      }
    }
  }
}
</style>
```

### 5.3.7 主界面设置路由视图

```vue
<!-- src/layout/index.vue -->
<!-- 后台管理系统两种布局：登录布局 + 其他布局 -->
<script  setup>
</script>

<template>
  <div class="common-layout">
    <el-container>
      <el-aside width="200px">Aside</el-aside>
      <el-container>
        <el-header>Header</el-header>
        <el-main>
          <!--  内容区域变化 -->
          <RouterView />
        </el-main>
        <el-footer>Footer</el-footer>
      </el-container>
    </el-container>
  </div>
</template>
```

### 5.3.8 轮播图列表视图

```vue
<!-- src/views/banner/list.vue -->
<script  setup></script>

<template>
  <div>轮播图列表</div>
  <RouterView />
</template>
```

# 6.渲染左侧菜单栏

## 6.1 重新设置路由表

页面展示靠路由，但是左侧菜单并不见得所有的路由都得出现

将不需要出现在左侧菜单栏的数据 做一个标识`hidden: true`

```js
// src/router/index.js

import { createRouter, createWebHistory } from 'vue-router'
// 1.引入自定义分模块的路由
import bannerRoutes from './modules/banner'
import proRoutes from './modules/pro'
import accountRoutes from './modules/account'

// 2.引入主界面布局，生成 首页和登录的路由 -- 常规路由 -- 任何人都可以访问路由
import Layout from '@/layout/index.vue'
import Home from '@/views/home/index.vue'
import Login from '@/views/login/index.vue'



// 3.定义常规路由-任何人可以访问的路由
export const constantRoutes= [
  { // 地址栏输入 /login, 整个页面展示登录页面
    path: '/login',
    component: Login,
    hidden: true  ++
  },
  {
    path: '/',
    redirect: '/home',
    component: Layout,
    children: [
      {
        path: '/home',
        component: Home,
        meta: {
          title: '系统首页',
          icon: 'HomeFilled'
        }
      }
    ]
  }
]

// 4.整合模块路由
export const asyncRoutes = [
  bannerRoutes,
  proRoutes,
  accountRoutes
]

// 5.合并路由
const router = createRouter({
  // createWebHistory http://localhost:5173/home
  // createWebHashHistory   http://localhost:5173/#/home
  history: createWebHistory(import.meta.env.BASE_URL),
  // routes: constantRoutes.concat(asyncRoutes)
  routes: [...constantRoutes, ...asyncRoutes]
})

export default router

```

```js
// src/router/modules/banner.js
import Layout from '@/layout/index.vue'
import BannerAdd from '@/views/banner/add.vue'
import BannerList from '@/views/banner/list.vue'
import BannerHomeList from '@/views/banner/components/home.vue'
import BannerKindList from '@/views/banner/components/kind.vue'
export default {
  path: '/banner',
  name: 'banner',
  redirect: '/banner/list',
  component: Layout,
  meta: {
    title: '轮播图管理',
    icon: 'PictureFilled'
  },
  children: [
    {
      path: '/banner/list',
      component: BannerList,
      redirect: '/banner/list/home',
      meta: {
        title: '轮播图列表'
      },
      children: [
        {
          path: '/banner/list/home',
          component: BannerHomeList,
          meta: {
            title: '首页轮播图'
          },
        },
        {
          path: '/banner/list/kind',
          component: BannerKindList,
          meta: {
            title: '分类页轮播图'
          },
        }
      ]
    },
    {
      path: '/banner/add',
      component: BannerAdd,
      meta: {
        title: '添加轮播图'
      },
      hidden: true
    }
  ]
}
```

## 6.2 构建左侧菜单的组件

```vue
<!-- src/layout/components/Sidebar/index.vue -->
<script  setup></script>
<template>
  <el-aside width="200px">
    <div class="logo"></div>
    <div>左侧菜单</div>
  </el-aside>
</template>
```

```vue

<!-- src/layout/index.vue -->
<script setup>
import Sidebar from "./components/Sidebar/index.vue"
</script>

<template>
  <div class="common-layout">
    <el-container>
      <!-- <el-aside width="200px">Aside</el-aside> -->
      <Sidebar></Sidebar>
      <el-container>
        <el-header>Header</el-header>
        <el-main>
          <RouterView></RouterView>
        </el-main>
        <el-footer>Footer</el-footer>
      </el-container>
    </el-container>
  </div>
</template>
```

## 6.3 处理左侧菜单栏数据

左侧菜单对应的每个数据的菜单项

```vue
<!-- src/layout/components/Sidebar/SidebarItem.vue -->
<script setup></script>

<template>
  <div>左侧菜单选项</div>
</template>
```

```vue
<!-- src/layout/components/Sidebar/index.vue -->
<script  setup>
  import SidebarItem from './SidebarItem.vue'

  // 整合路由
  import { constantRoutes, asyncRoutes } from '@/router'

  const menuList = constantRoutes.concat(asyncRoutes)
  console.log(menuList)
</script>
<template>
  <el-aside width="200px">
    <div class="logo"></div>
    <!-- 菜单组件
    https://element-plus.gitee.io/zh-CN/component/menu.html#%E4%BE%A7%E6%A0%8F
    -->
    <!-- <div>左侧菜单</div> -->
    <el-menu>
      <!-- 路由中的每一个选项都需要单独去渲染菜单项
      有的不需要出现在左侧的菜单栏
      有的只有一个菜单项
      有的有二级菜单和三级菜单
      建议把每个菜单项单独封装成一个组件  SidebarItem
      登录  系统首页   产品管理   账户管理  轮播图管理
      将每一项数据 item 传输到子组件，子组件接收数据，并且渲染
      -->
      <SidebarItem 
        v-for="item of menuList"
        :key="item.path"
        :item = "item"  <!>使用v-bind指令，将当前元素item作为props传递给SidebarItem组件
      ></SidebarItem>
    </el-menu>
  </el-aside>
</template>
```



## 6.4 渲染左侧菜单的数据

说明：需要使用图标

```sh
$ cnpm install @element-plus/icons-vue
```

```ts
// src/main.ts
import { createApp } from 'vue'
import { createPinia } from 'pinia'

// 引入UI库
import ElementPlus from 'element-plus'
import 'element-plus/dist/index.css'
import zhCn from 'element-plus/dist/locale/zh-cn.mjs'

// 引入图标
import * as ElementPlusIconsVue from '@element-plus/icons-vue'

import App from './App.vue'
import router from './router'

// 重置样式表
import 'normalize.css/normalize.css'

// import './assets/main.css' // 不使用默认样式

const app = createApp(App)
// 配置图标
for (const [key, component] of Object.entries(ElementPlusIconsVue)) {
  app.component(key, component)
}

// 配置UI库
app.use(ElementPlus, { locale: zhCn })
app.use(createPinia())
app.use(router)

app.mount('#app')

```

```vue
<!-- src/layout/components/Sidebar/SidebarItem.vue -->
<!-- 动态渲染数据 -->

<!-- src/layout/components/Sidebar/SidebarItem.vue -->
<script  setup>
  // 1.接收父组件所传递的数据 item 并且加以验证
  // https://cn.vuejs.org/guide/typescript/composition-api.html#typing-component-props
  const props = defineProps({
    // item 为父组件传递给子组件的标识
    item: { type: Object, required: true }
  })
</script>
<!-- 
  遇到 类似登录的路由含有 hidden：true  不希望出现左侧菜单栏
 -->
<template>
  <!-- 过滤了 含有 hidden：true 的数据 -->
  <div v-if="!item.hidden">
    <!-- 系统首页的路由 children 的长度只为1，认为只需要写一个一级路由即可 
    index属性代表唯一标志 -->
    <el-menu-item :index="item.path" v-if="item.children && item.children.length === 1">
      <el-icon>
        <!-- 动态组件 -->
        <component :is="item.children[0].meta.icon"></component>
      </el-icon>
      <span>{{ item.children[0].meta.title }}</span>
    </el-menu-item>
    <!-- 路由选项既没有 children 也没有 hidden 时候
      {
        path: '/setting',
        component: Setting,
        meta: {
          title: '设置',
          icon: 'Setting'
        }
      },
      { // 二级菜单子菜单
        path: '/account/user',
        component: User,
        meta: {
          title: '用户列表'
        }
      },
    -->
    <el-menu-item :index="item.path" v-else-if="!item.children">
      <el-icon>
        <!-- 动态组件 -->
        <component :is="item.meta.icon"></component>
      </el-icon>
      <span>{{ item.meta.title }}</span>
    </el-menu-item>
    <!-- 剩余的包含有多级菜单的数据
      函数 - 函数递归
      组件 - 组件递归
        组合式API的组件递归，自己调用自己的组件，必须确保组件的名字和组件的文件名字保持一致
        假设组件文件名为 TestCom.vue ，那么递归调用时   <test-com></text-com>
        递归目的：自动渲染多级菜单

    -->
    <el-sub-menu :index="item.path" v-else>
      <!-- 插槽实现一级菜单 -->
      <template #title>
        <el-icon>
          <!-- 动态组件 -->
          <component :is="item.meta.icon"></component>
        </el-icon>
        <span>{{ item.meta.title }}</span>
      </template>
      <!-- 递归组件 -->
      <sidebar-item v-for="itm of item.children" :key="item.path" :item="itm"></sidebar-item>
    </el-sub-menu>
 <!-- 遍历item.children数组中的每个元素，将每个元素赋值给变量itm -->
<!-- 设置每个遍历的组件的唯一标识，使用item.path作为标识 -->
<!-- 将itm作为props传递给<sidebar-item>组件 -->
  </div>
</template>
```

## 6.5 点击左侧菜单切换路由

```vue
<!-- src/layout/components/Sidebar/SidebarItem.vue -->
<script  setup>
  import { useRouter } from 'vue-router';

  const props = defineProps({
    item: { type: Object, required: true }
  })
  // https://router.vuejs.org/zh/guide/advanced/composition-api.html
  // router.push()       从A push 到B，从B push 到C，C可以返回到B，B可以返回到A
  // router.replace()    从A push 到B，从B replace 到C， C返回的实际上是 A
  // router.back()       返回
  // router.go(num)       num为正，前进几步，num为负，后退几步
  // 选项式API  this.$router.push()  .replace()
  const router = useRouter()
  const changeUrl = (path) => {
    console.log(path)
    router.push(path) // js 跳转页面 ---- 编程式导航跳转
  }
</script>
<template>
  <div v-if="!item.hidden">
    <el-menu-item @click="changeUrl(item.path)" :index="item.path" v-if="item.children && item.children.length === 1">
      <el-icon>
        <component :is="item.children[0].meta.icon"></component>
      </el-icon>
      <span>{{ item.children[0].meta.title }}</span>
    </el-menu-item>
    <el-menu-item @click="changeUrl(item.path)" :index="item.path" v-else-if="!item.children">
      <el-icon>
        <component :is="item.meta.icon"></component>
      </el-icon>
      <span>{{ item.meta.title }}</span>
    </el-menu-item>
    <el-sub-menu :index="item.path" v-else>
      <template #title>
        <el-icon>
          <component :is="item.meta.icon"></component>
        </el-icon>
        <span>{{ item.meta.title }}</span>
      </template>
      <sidebar-item v-for="itm of item.children" :key="item.path" :item="itm"></sidebar-item>
    </el-sub-menu>
  </div>
</template>
```

## 6.6 只展开一个以及刷新选中

```vue
<!-- src/layout/components/Sidebar/index.vue -->
<script  setup>
  import SidebarItem from './SidebarItem.vue'

  // 整合路由
  import { constantRoutes, asyncRoutes } from '@/router'
  import { useRoute } from 'vue-router';

  const menuList = constantRoutes.concat(asyncRoutes)
  console.log(menuList)

  // 获取路由地址
  // 选项式API  this.$route
  const route = useRoute()
  console.log(route)
</script>
<template>
  <el-aside width="200px">
    <div class="logo"></div>
    <!-- 菜单组件
    https://element-plus.gitee.io/zh-CN/component/menu.html#%E4%BE%A7%E6%A0%8F
    -->
    <!-- <div>左侧菜单</div> -->
    <el-menu
      :unique-opened="true"
      :default-active="route.path"
      background-color="#001529"
      text-color="#fff"
      :collapse-transition="false"
    >
      <!-- 路由中的每一个选项都需要单独去渲染菜单项
      有的不需要出现在左侧的菜单栏
      有的只有一个菜单项
      有的有二级菜单和三级菜单
      建议把每个菜单项单独封装成一个组件  SidebarItem
      登录  系统首页   产品管理   账户管理  轮播图管理
      将每一项数据 item 传输到子组件，子组件接收数据，并且渲染
      -->
      <SidebarItem 
        v-for="item of menuList"
        :key="item.path"
        :item = "item"
      ></SidebarItem>
    </el-menu>
  </el-aside>
</template>
```

## 6.7 logo

```vue
<!-- src/layout/components/logo/index.vue -->
<script  setup>
  import { computed } from 'vue'
  import logo from '@/assets/logo.svg'
  import settings from '@/settings'

  const title = computed(() => settings.title)
</script>

<template>
  <div class="logo">
    <el-image style="width: 40px; height: 40px" :src="logo" fit="fill" />
    <span>{{  title  }}</span>
  </div>
</template>

<style lang="scss">
.logo {
  width: 100%;
  height: 60px;
  overflow: hidden;
  padding: 10px;
  box-sizing: border-box;
  color: #fff;
  display: flex;
  align-items: center;
}
</style>
```

```vue
<!-- src/layout/components/Sidebar/index.vue -->
<script  setup>
  import SidebarItem from './SidebarItem.vue'
  import Logo from './../logo/index.vue'

  // 整合路由
  import { constantRoutes, asyncRoutes } from '@/router'
  import { useRoute } from 'vue-router';

  const menuList = constantRoutes.concat(asyncRoutes)
  console.log(menuList)

  // 获取路由地址
  // 选项式API  this.$route
  const route = useRoute()
  console.log(route)
</script>
<template>
  <el-aside width="200px">
    <!-- <div class="logo"></div> -->
    <Logo />
    <!-- 菜单组件
    https://element-plus.gitee.io/zh-CN/component/menu.html#%E4%BE%A7%E6%A0%8F
    -->
    <!-- <div>左侧菜单</div> -->
    <el-menu
      :unique-opened="true"
      :default-active="route.path"
    >
      <!-- 路由中的每一个选项都需要单独去渲染菜单项
      有的不需要出现在左侧的菜单栏
      有的只有一个菜单项
      有的有二级菜单和三级菜单
      建议把每个菜单项单独封装成一个组件  SidebarItem
      登录  系统首页   产品管理   账户管理  轮播图管理
      将每一项数据 item 传输到子组件，子组件接收数据，并且渲染
      -->
      <SidebarItem 
        v-for="item of menuList"
        :key="item.path"
        :item = "item"
      ></SidebarItem>
    </el-menu>
  </el-aside>
</template>
```

## 6.8 左侧菜单的收缩

logo组件接收变量，控制文件的显示

```vue
<!-- src/layout/components/logo/index.vue -->
<script  setup>
  import { computed } from 'vue'
  import logo from '@/assets/logo.svg'
  import settings from '@/settings'

  const props = defineProps({
    collapse: { type: Boolean, required: true }
  })

  const title = computed(() => settings.title)
</script>

<template>
  <div class="logo">
    <el-image style="width: 40px; height: 40px" :src="logo" fit="fill" />
    <span v-if="!collapse">{{  title  }}</span>
  </div>
</template>

<style lang="scss">
.logo {
  width: 100%;
  height: 60px;
  overflow: hidden;
  padding: 10px;
  box-sizing: border-box;
  color: #fff;
  display: flex;
  align-items: center;
}
</style>
```

```vue
<!-- src/layout/components/Sidebar/index.vue -->
<script  setup>
  import { ref } from 'vue'
  import SidebarItem from './SidebarItem.vue'
  import Logo from './../logo/index.vue'

  // 整合路由
  import { constantRoutes, asyncRoutes } from '@/router'
  import { useRoute } from 'vue-router';

  const menuList = constantRoutes.concat(asyncRoutes)
  console.log(menuList)

  // 获取路由地址
  // 选项式API  this.$route
  const route = useRoute()
  console.log(route) // route.path.value

  const collapse = ref(false)
</script>
<template>
  <el-aside :width="collapse ? '50px' : '200px'">
    <!-- <div class="logo"></div> -->
    <Logo :collapse="collapse"/>
    <!-- 菜单组件
    https://element-plus.gitee.io/zh-CN/component/menu.html#%E4%BE%A7%E6%A0%8F
    -->
    <!-- <div>左侧菜单</div> -->
    <el-menu
      :collapse="collapse"
      :unique-opened="true"
      :default-active="route.path"
    >
      <!-- 路由中的每一个选项都需要单独去渲染菜单项
      有的不需要出现在左侧的菜单栏
      有的只有一个菜单项
      有的有二级菜单和三级菜单
      建议把每个菜单项单独封装成一个组件  SidebarItem
      登录  系统首页   产品管理   账户管理  轮播图管理
      将每一项数据 item 传输到子组件，子组件接收数据，并且渲染
      -->
      <SidebarItem 
        v-for="item of menuList"
        :key="item.path"
        :item = "item"
      ></SidebarItem>
    </el-menu>
    <div class="changeIcon" :style="{ width: collapse ? '50px' : '200px'}">
        <!-- 如果collapse为真，则显示一个带有白色图标的元素 -->
      <el-icon color="#fff" v-if="collapse" @click="collapse = !collapse"><ArrowRight /></el-icon>
        <!-- 如果collapse为假，则显示一个带有白色图标的元素 -->
      <el-icon color="#fff" v-else @click="collapse=!collapse"><ArrowLeft /></el-icon>
    </div>
  </el-aside>
</template>

<style lang="scss">
.changeIcon {
  position: absolute;
  bottom: 10px;
  display: flex;
  justify-content: center;
}
</style>
```

## 6.9 面包屑

```vue
<!-- src/layout/components/breadcrumb/index.vue -->
<script setup></script>

<template>
  <div>面包屑</div>
</template>
```

获取需要的对象数据

```vue
<!-- src/layout/components/breadcrumb/index.vue -->
<script setup>
  // 准备数据
  // const breadcrumbNameMap = {
  //   '/home': '系统首页',
  //   '/banner': '轮播图管理',
  //   '/banner/list': '轮播图列表',
  //   '/banner/list/home': '首页轮播图',
  //   '/banner/list/kind': '分类轮播图',
  //   '/banner/add': '添加轮播图',
  //   '/pro': '产品管理',
  //   '/pro/list': '产品列表',
  //   '/pro/search': '筛选列表',
  //   '/account': '账户管理',
  //   '/account/user': '用户列表',
  //   '/account/admin': '管理员列表' 
  // }
  import { constantRoutes, asyncRoutes} from '@/router'
  
  const menuList = [...constantRoutes, ...asyncRoutes]

  let breadcrumbNameMap = {}

// 定义一个函数，传入一个名为 menuList 的参数
function getBreadcrumbNameMap(menuList) {
  // 对 menuList 数组进行遍历
  menuList.forEach(item => {
    // 如果当前遍历到的 item 的路径不是 '/login'
    if (item.path !== '/login') {
      // 如果 item 有子菜单
      if (item.children) {
        // 如果 item 的子菜单只有一个
        if (item.children.length === 1) {
          // 将子菜单的路径作为键，子菜单的标题作为值，存入 breadcrumbNameMap 对象中
          breadcrumbNameMap[item.children[0].path] = item.children[0].meta.title
        } else {
          // 如果子菜单不止一个
          // 将当前 item 的路径作为键，当前 item 的标题作为值，存入 breadcrumbNameMap 对象中
          breadcrumbNameMap[item.path] = item.meta.title
          // 递归调用 getBreadcrumbNameMap 函数，传入当前 item 的子菜单作为参数
          getBreadcrumbNameMap(item.children)
        }
      } else {
        // 如果 item 没有子菜单
        // 将当前 item 的路径作为键，当前 item 的标题作为值，存入 breadcrumbNameMap 对象中
        breadcrumbNameMap[item.path] = item.meta.title
      }
    }
  })
}

// 调用 getBreadcrumbNameMap 函数，传入 menuList 作为参数
getBreadcrumbNameMap(menuList)

// 打印 breadcrumbNameMap 对象
console.log(breadcrumbNameMap)

  // /banner/list/kind 
  // breadcrumbNameMap['/banner']  breadcrumbNameMap['/banner/list'] breadcrumbNameMap['/banenr/list/kind']
  // 轮播图管理 轮播图列表 分类轮播图
</script>

<template>
  <div>面包屑</div>
</template>
```

根据地址栏获取路由

```vue
<!-- src/layout/components/breadcrumb/index.vue -->
<script setup>
  // 准备数据
  // const breadcrumbNameMap = {
  //   '/home': '系统首页',
  //   '/banner': '轮播图管理',
  //   '/banner/list': '轮播图列表',
  //   '/banner/list/home': '首页轮播图',
  //   '/banner/list/kind': '分类轮播图',
  //   '/banner/add': '添加轮播图',
  //   '/pro': '产品管理',
  //   '/pro/list': '产品列表',
  //   '/pro/search': '筛选列表',
  //   '/account': '账户管理',
  //   '/account/user': '用户列表',
  //   '/account/admin': '管理员列表' 
  // }
  import { constantRoutes, asyncRoutes} from '@/router'
  import { watchEffect, ref } from 'vue';
  import { useRoute } from 'vue-router';
  
  const menuList = [...constantRoutes, ...asyncRoutes]

  let breadcrumbNameMap = {}

  function getBreadcrumbNameMap (menuList) {
    menuList.forEach(item => {
      if (item.path !== '/login') {
        if (item.children) {
          if (item.children.length === 1) {
          
            breadcrumbNameMap[item.children[0].path] = item.children[0].meta.title 
          } else {
            breadcrumbNameMap[item.path] = item.meta.title 
            getBreadcrumbNameMap(item.children)
          }
        } else {
          breadcrumbNameMap[item.path] = item.meta.title 
        }
      }
    })
  }
  getBreadcrumbNameMap(menuList)
  // console.log(breadcrumbNameMap) // 需要准备的数据

  // /banner/list/kind 
  // breadcrumbNameMap['/banner']  breadcrumbNameMap['/banner/list'] breadcrumbNameMap['/banenr/list/kind']
  // 轮播图管理 轮播图列表 分类轮播图

  const route = useRoute()
  // const url = route.path
  // console.log(url) // /banner/list/kind 

  function getData () {
    const arr = route.path.split('/') // ['', 'banner', 'list', 'kind']
    arr.shift() // ['banner', 'list', 'kind']
    // ['/banner', '/banner/list', '/banner/list/kind']

    const newArr = []
    arr.map((_, index) => {
      // join('/') 拼接时使用 / 拼接，默认是 ，
      const newUrl = '/' + arr.slice(0, index + 1).join('/')
      console.log(newUrl)
      newArr.push(newUrl)
    })
    // console.log(newArr)
    return newArr
  }  //3.   //value: 代表数组中的每一个元素    //   //index: 代表数组中的每一个下标*
     //map(function(value,index,array){return ...}) : 遍历数组,返回数组
  let breadcrumbArr = ref([])
  watchEffect(() => { // 路由变化时 重新获取面包屑 ---- 保证数据的双向绑定
    console.log(11111)
    breadcrumbArr.value = getData() // 修改使用 value 保证响应式
    console.log('66', breadcrumbArr)
  })
</script>

<template>
  <el-breadcrumb separator="/">
    <el-breadcrumb-item :to="{ path: '/' }">系统首页</el-breadcrumb-item>
    <el-breadcrumb-item v-for="(item, index) of breadcrumbArr" :key="index">
      <a :href="item">{{ breadcrumbNameMap[item] }}</a>
    </el-breadcrumb-item>
  </el-breadcrumb>
</template>
```

垂直居中显示面包屑

```vue
<!-- src/layout/index.vue -->
<!-- 后台管理系统两种布局：登录布局 + 其他布局 -->
<script  setup>
import SideBar from './components/Sidebar/index.vue'
import Breadcrumb from './components/breadcrumb/index.vue'
</script>

<template>
  <div class="common-layout">
    <el-container>
      <!-- <el-aside width="200px">Aside</el-aside> -->
      <SideBar />
      <el-container>
        <el-header :style="{ display: 'flex', alignItems: 'center'}">
          <Breadcrumb />
        </el-header>
        <el-main>
          <!--  内容区域变化 -->
          <RouterView />
        </el-main>
        <el-footer>Footer</el-footer>
      </el-container>
    </el-container>
  </div>
</template>
```



# 7.封装数据请求

axios https://www.axios-http.cn/docs/intro

```js
// restful api
// get
// post
// put    更新
// patch  更新
// delete 删除

// get
fetch('url?a=1&b=2').then(res => res.json()).then(res => { console.log(res) })
axios.get('url?a=1&b=2').then(res => { console.log(res) })
axios.get('url', {  params: { a: 1, b: 2} }).then(res => { console.log(res) })
axios({
  url: 'url?a=1&b=2',
  method: 'get'
}).then(res => { console.log(res) })
axios({
  url: 'url',
  method: 'get',
  params: { a: 1, b: 2}
}).then(res => { console.log(res) })

// post
axios.post('url', { a: 1, b: 2 }).then(res => { console.log(res) })
axios({
  url: 'url',
  method: 'post',
  data: { a: 1, b: 2}
}).then(res => { console.log(res) })

// axios 拦截器
// 请求拦截器
// 响应拦截器
// 添加请求拦截器
axios.interceptors.request.use(function (config) {
    // 在发送请求之前做些什么
  	// 显示loading动画效果
    return config;
  }, function (error) {
    // 对请求错误做些什么
    return Promise.reject(error);
  });

// 添加响应拦截器
axios.interceptors.response.use(function (response) {
    // 2xx 范围内的状态码都会触发该函数。
    // 对响应数据做点什么
  	// loading动画消失
    return response;
  }, function (error) {
    // 超出 2xx 范围的状态码都会触发该函数。
    // 对响应错误做点什么
    return Promise.reject(error);
  });
```

一般项目中都需要重新定义axios，需要对axios进行配置

```js
// 创建实例时配置默认值
const instance = axios.create({
  baseURL: 'https://api.example.com'
});

// 创建实例后修改默认值
instance.defaults.headers.common['Authorization'] = AUTH_TOKEN;
// https://api.example.com/api/pro/list
instance.get('/api/pro/list')
```

# 8.pinia状态管理器

## 8.1 入口注册pinia

```js


import { createApp } from 'vue'
import { createPinia } from 'pinia'

import App from './App.vue'
import router from './router'

// 重置样式表
import 'normalize.css/normalize.css'
// import './assets/main.css' // 不使用默认样式

//引入uI组件库的模块
import ElementPlus from 'element-plus'
//引入uI组件库的样式
import 'element-plus/dist/index.css'
//导入中文语言包
import zhCn from 'element-plus/dist/locale/zh-cn.mjs'


//引入图标
import * as ElementPlusIconsVue from '@element-plus/icons-vue'
const app = createApp(App)


// 配置图标
for (const [key, component] of Object.entries(ElementPlusIconsVue)) {
    app.component(key, component)
  }
  
// 配置UI库  ++++++
app.use(ElementPlus, { locale: zhCn })
app.use(createPinia())
app.use(router)


app.mount('#app')

```

## 8.2 定义状态管理器模块

```js
// src/store/counter.js
import { ref, computed } from 'vue'
import { defineStore } from 'pinia'


// 组合式API
export const useCounterStore = defineStore('counter', () => {
  // 初始化
  const count = ref(0)
  // 计算属性
  const doubleCount = computed(() => count.value * 2)
  // 方法
  function increment() {
    count.value += 10
  }
  function decrement() {
    count.value -= 10
  }
  // 返回˙状态和方法
  return { count, doubleCount, increment, decrement }
})
```

## 8.3 组件中使用

### 8.3.1 模版中使用对象渲染

```vue
<!-- src/views/home/index.vue -->
<script  setup>
  import { computed } from 'vue'
  import { useCounterStore } from '@/stores/counter'

  const counter = useCounterStore()

  // 提取模版中需要使用的数据
  const count = computed(() => counter.count)
  const doubleCount = computed(() => counter.doubleCount)

  const reduce = () => {
    counter.decrement()
  }
  const add = () => {
    counter.increment()
  }
</script>

<template>
  <div>系统首页</div>
  <button @click="reduce">-10</button> 
  {{ count }} - {{ counter.count }}  - {{ counter.doubleCount }} - {{  doubleCount }}
  <button @click="add">+10</button>
</template>
```

```vue
<!-- src/views/account/user.vue -->
<script  setup>
  import { useCounterStore } from '@/stores/counter'

  const counter = useCounterStore()

  const reduce = () => {
    counter.decrement()
  }
  const add = () => {
    counter.increment()
  }
</script>

<template>
  <div>用户列表</div>
  <button @click="reduce">-10</button> 
  {{ counter.count }} - {{ counter.doubleCount }}
  <button @click="add">+10</button>
</template>
```

# 9.登录功能实现

## 9.1 构建登录页面

```vue
<!-- src/views/login/index.vue -->
<script  setup>
  import { ref, computed } from 'vue';

  const adminname = ref('')
  const password = ref('')

  // 按钮是否可点
  const flag = computed(() => { return adminname.value === '' || password.value === ''})
</script>

<template>
  <div class="loginBox">
    <div class="loginForm">
      <div class="loginTitle">系统登录</div>
      <div class="loginInput">
        <el-input v-model="adminname" placeholder="管理员账户" clearable prefix-icon="User"/>
      </div>
      <div class="loginInput">
        <el-input type="password" v-model="password" clearable placeholder="管理员密码" show-password prefix-icon="Lock"/>
      </div>
      <el-button type="primary" :disabled="flag" class="loginBtn">登录</el-button>

      <span>默认账户名：admin 默认密码：123456</span>
    </div>
  </div>
</template>

<style lang="scss">
  .loginBox {
    width: 100%;
    height: 100%;
    background-color: #2b2b2b;
    display: flex;
    justify-content: center;
    align-items: center;
    color: #fff;
    .loginForm {
      width: 500px;
      min-height: 300px;
      /* background-color: #fff; */
      .loginTitle {
        text-align: center;
        font-size: 24px;
        font-weight: bold;
      }
      .loginInput {
        margin: 20px 0;
        .el-input {
          height: 40px;
          .el-input__wrapper {
            background-color: #2b2b2b;
            .el-input__inner {
              background-color: #2b2b2b;
            }
          }
          
        }
      }
      .loginBtn {
        width: 100%;
        height: 36px;
        margin-bottom: 20px;
      }
    }
  }
</style>
```

## 9.2 封装管理员登录的数据请求

```js
// src/api/admin.js
import request from '@/utils/request'

export function adminLogin (params) {
  return request.post('/admin/login', params)
}
```

## 9.3 登录页面调用登录接口

```vue
<!-- src/views/login/index.vue -->
<script  setup>
  import { ref, computed } from 'vue';
  import { ElMessage } from 'element-plus'
  import { adminLogin } from '@/api/admin'
  import { useRouter } from 'vue-router';
  const adminname = ref('')
  const password = ref('')

  // 按钮是否可点
  const flag = computed(() => { return adminname.value === '' || password.value === ''})

  const router = useRouter()
  const login = () => {
    adminLogin({
      adminname: adminname.value,
      password: password.value
    }).then(res => {
      console.log(res)
      if (res.data.code === '10005') {
        console.log('账户未注册')
        ElMessage.error('账户未注册.')
      } else if (res.data.code === '10003') {
        ElMessage.warning('密码错误')
      } else {
        ElMessage.success('登录成功')

        // 将登陆信息保存到本地
        localStorage.setItem('adminname', res.data.data.adminname)
        localStorage.setItem('checkedkeys', res.data.data.checkedkeys)
        localStorage.setItem('role', res.data.data.role)
        localStorage.setItem('token', res.data.data.token)

        router.replace('/')
      }
    })
  }
</script>

<template>
  <div class="loginBox">
    <div class="loginForm">
      <div class="loginTitle">系统登录</div>
      <div class="loginInput">
        <el-input v-model="adminname" placeholder="管理员账户" clearable prefix-icon="User"/>
      </div>
      <div class="loginInput">
        <el-input type="password" v-model="password" clearable placeholder="管理员密码" show-password prefix-icon="Lock"/>
      </div>
      <el-button type="primary" @click="login" :disabled="flag" class="loginBtn">登录</el-button>

      <span>默认账户名：admin 默认密码：123456</span>
    </div>
  </div>
</template>

<style lang="scss">
  .loginBox {
    width: 100%;
    height: 100%;
    background-color: #2b2b2b;
    display: flex;
    justify-content: center;
    align-items: center;
    color: #fff;
    .loginForm {
      width: 500px;
      min-height: 300px;
      /* background-color: #fff; */
      .loginTitle {
        text-align: center;
        font-size: 24px;
        font-weight: bold;
      }
      .loginInput {
        margin: 20px 0;
        .el-input {
          height: 40px;
          .el-input__wrapper {
            background-color: #2b2b2b;
            .el-input__inner {
              background-color: #2b2b2b;
            }
          }
          
        }
      }
      .loginBtn {
        width: 100%;
        height: 36px;
        margin-bottom: 20px;
      }
    }
  }
</style>
```

## 9.4 退出登录

```vue
<!-- src/layout/index.vue -->
<!-- 后台管理系统两种布局：登录布局 + 其他布局 -->
<script setup>
  import SideBar from './components/Sidebar/index.vue'
  import Breadcrumb from './components/breadcrumb/index.vue'
  import { ArrowDown } from '@element-plus/icons-vue'
  import { useRouter } from 'vue-router';

  const router = useRouter()
  const adminname = localStorage.getItem('adminname')

  const logout = () => {
    localStorage.removeItem('adminname')
    localStorage.removeItem('token')
    localStorage.removeItem('checkedkeys')
    localStorage.removeItem('role')

    router.push('/login')
  }
</script>

<template>
  <div class="common-layout">
    <el-container>
      <!-- <el-aside width="200px">Aside</el-aside> -->
      <SideBar />
      <el-container>
        <el-header :style="{ display: 'flex', alignItems: 'center'}">
          <Breadcrumb />
          <el-dropdown :style="{ position: 'absolute', right: '16px'}">
            <span class="el-dropdown-link">
              欢迎您，{{  adminname  }}
              <el-icon class="el-icon--right">
                <arrow-down />
              </el-icon>
            </span>
            <template #dropdown>
              <el-dropdown-menu>
                <el-dropdown-item>个人中心</el-dropdown-item>
                <el-dropdown-item divided @click="logout">退出</el-dropdown-item>
              </el-dropdown-menu>
            </template>
          </el-dropdown>
        </el-header>
        <el-main>
          <!--  内容区域变化 -->
          <RouterView />
        </el-main>
        <el-footer>Footer</el-footer>
      </el-container>
    </el-container>
  </div>
</template>
```

## 9.5 登录信息状态管理

```js
// src/store/admins.js
import { ref} from 'vue'
import { defineStore } from 'pinia'

// 组合式API
export const useAdminStore = defineStore('admin', () => {
  // 初始化 初始状态从本地获取的目的是为了实现状态的持久化。通过从本地存储中获取初始值，可以在页面刷新或重新加载时保留之前的状态。
  const adminname = ref(localStorage.getItem('adminname') || '')
  const token = ref(localStorage.getItem('token') || '')
  //changeAdminname 方法用于修改管理员名称，接受一个参数 val，
  //将其赋值给adminname.value，从而更新管理员名称的状态。
//changeToken 方法用于修改令牌，接受一个参数 val，将其赋值给 token.value，从而更新令牌的状态。
  //val 是一个参数，它在调用 changeAdminname 和 changeToken 方法时传入的值。在这段代码中，val 是表示要修改的新数值的变量名，可以根据具体的调用情况自行命名。例如，当调用 changeAdminname('新管理员名称') 时，val 的值就是 '新管理员名称'。类似地，当调用 changeToken('新令牌') 时，val 的值就是 '新令牌'。在这两个方法中，val 的作用是将新的数值赋给对应的状态变量，从而更新状态。
  const changeAdminname = (val) => {
    adminname.value = val
  }

  const changeToken = (val) => {
    token.value = val
  }

  // 返回˙状态和方法
  return { adminname, token, changeAdminname, changeToken }
})
```

## 9.6 登录页面修改 状态以及布局页面使用状态

```vue
<!-- src/views/login/index.vue -->
<script  setup>
  import { ref, computed } from 'vue';
  import { ElMessage } from 'element-plus'
  import { adminLogin } from '@/api/admin'
  import { useRouter } from 'vue-router';
  import { useAdminStore } from '@/stores/admins';
  const adminname = ref('admin')
  const password = ref('123456')

  const admin = useAdminStore()

  // 按钮是否可点
  const flag = computed(() => { return adminname.value === '' || password.value === ''})

  const router = useRouter()
  const login = () => {
    // 正则验证
    adminLogin({
      adminname: adminname.value,
      password: password.value
    }).then(res => {
      // console.log(res)
      if (res.data.code === '10005') {
        console.log('账户未注册')
        ElMessage.error('账户未注册.')
      } else if (res.data.code === '10003') {
        ElMessage.warning('密码错误')
      } else {
        ElMessage.success('登录成功')

        // 将登陆信息保存到本地
        localStorage.setItem('adminname', res.data.data.adminname)
        localStorage.setItem('checkedkeys', res.data.data.checkedkeys)
        localStorage.setItem('role', res.data.data.role)
        localStorage.setItem('token', res.data.data.token)

        // 可以将数据保存到状态管理器
        admin.changeAdminname(res.data.data.adminname)
        admin.changeToken(res.data.data.token)

        router.replace('/')
      }
    })
  }
</script>

<template>
  <div class="loginBox">
    <div class="loginForm">
      <div class="loginTitle">系统登录</div>
      <div class="loginInput">
        <el-input v-model="adminname" placeholder="管理员账户" clearable prefix-icon="User"/>
      </div>
      <div class="loginInput">
        <el-input type="password" v-model="password" clearable placeholder="管理员密码" show-password prefix-icon="Lock"/>
      </div>
      <el-button type="primary" @click="login" :disabled="flag" class="loginBtn">登录</el-button>

      <span>默认账户名：admin 默认密码：123456</span>
    </div>
  </div>
</template>

<style lang="scss">
  .loginBox {
    width: 100%;
    height: 100%;
    background-color: #2b2b2b;
    display: flex;
    justify-content: center;
    align-items: center;
    color: #fff;
    .loginForm {
      width: 500px;
      min-height: 300px;
      /* background-color: #fff; */
      .loginTitle {
        text-align: center;
        font-size: 24px;
        font-weight: bold;
      }
      .loginInput {
        margin: 20px 0;
        .el-input {
          height: 40px;
          .el-input__wrapper {
            background-color: #2b2b2b;
            .el-input__inner {
              background-color: #2b2b2b;
            }
          }
          
        }
      }
      .loginBtn {
        width: 100%;
        height: 36px;
        margin-bottom: 20px;
      }
    }
  }
</style>
```

```vue
<!-- src/layout/index.vue -->
<!-- 后台管理系统两种布局：登录布局 + 其他布局 -->
<script  setup>
  import SideBar from './components/Sidebar/index.vue'
  import Breadcrumb from './components/breadcrumb/index.vue'
  import { ArrowDown } from '@element-plus/icons-vue'
  import { useRouter } from 'vue-router';
  import { useAdminStore } from '@/stores/admins'
  import { computed } from 'vue';

  const router = useRouter()
  // const adminname = localStorage.getItem('adminname')
  const admin = useAdminStore()
  const adminname = computed(() => admin.adminname)

  const logout = () => {
    localStorage.removeItem('adminname')
    localStorage.removeItem('token')
    localStorage.removeItem('checkedkeys')
    localStorage.removeItem('role')

    router.push('/login')
  }
</script>

<template>
  <div class="common-layout">
    <el-container>
      <!-- <el-aside width="200px">Aside</el-aside> -->
      <SideBar />
      <el-container>
        <el-header :style="{ display: 'flex', alignItems: 'center'}">
          <Breadcrumb />
          <el-dropdown :style="{ position: 'absolute', right: '16px'}">
            <span class="el-dropdown-link">
              欢迎您1，{{  adminname  }}
              <el-icon class="el-icon--right">
                <arrow-down />
              </el-icon>
            </span>
            <template #dropdown>
              <el-dropdown-menu>
                <el-dropdown-item>个人中心</el-dropdown-item>
                <el-dropdown-item divided @click="logout">退出</el-dropdown-item>
              </el-dropdown-menu>
            </template>
          </el-dropdown>
        </el-header>
        <el-main>
          <!--  内容区域变化 -->
          <RouterView />
        </el-main>
        <el-footer>Footer</el-footer>
      </el-container>
    </el-container>
  </div>
</template>
```

# 10 管理员的操作

## 10.1 渲染管理员列表

封装获取管理员信息的接口

```js
// src/api/admin.js
import request from '@/utils/request'

export function adminLogin (params) {
  return request.post('/admin/login', params)
}
//封装获取管理员信息的接口
export function getAdminList () {
  return request.get('/admin/list')
}
```

```vue
<!-- src/views/account/Admin.vue -->
<script  setup>
  import { ref, onMounted } from 'vue';
  import { getAdminList } from '@/api/admin'


  const adminList = ref([])

  onMounted(() => {
    getAdminList().then(res => {
      console.log('admin', res.data)
      adminList.value = res.data.data
    })
  })
</script>

<template>
  <el-table :data="adminList" style="width: 100%">
    <el-table-column label="序号">
      <template #default="scope">
        <!-- scope.$index 表达式表示当前行的索引值，这是 Vue 在循环渲染时自动生成的一个变量，它会自动随着循环的进行而递增。在这段代码中，我们使用 scope.$index + 1 来实现从 1 开始的序号，因为默认的索引值是从 0 开始计数的。-->
        <span>{{ scope.$index + 1 }}</span>
      </template>
    </el-table-column>
    <el-table-column prop="adminname" label="管理员账户" width="180" />
    <el-table-column prop="role" label="角色" width="180" >
      <template #default="scope">
        <!-- scope.row 代表一条数据 -->
        <el-tag v-if="scope.row.role === 2" class="ml-2" type="success">超级管理员</el-tag>
        <el-tag v-else class="ml-2" type="info">管理员</el-tag>
      </template>
    </el-table-column>
    <el-table-column label="操作">
      <template #default="scope">
        <el-button size="small"
          >编辑</el-button
        >
        <el-button
          size="small"
          type="danger"
          >删除</el-button
        >
      </template>
    </el-table-column>
  </el-table>
</template>
```

## 10.2 分页实现

```vue
<!-- src/views/account/Admin.vue -->
<script  setup>
  import { ref, onMounted, computed } from 'vue';
  import { getAdminList } from '@/api/admin'


  // 将展示数据adminList 变为了 计算属性的数据
  // 将依据原始数据 originalList 以及 页码currentPage  和每页显示个数pageSize 一起计算出来显示的数据adminList
  const currentPage = ref(1) // 当前页码
  const pageSize = ref(10) // 每页显示个数
  const originalList = ref([])// 原始数据列表
  const changeCurrentPage = (val) => { // 页码改变函数
    currentPage.value = val
  }
  const changeSize = (val) => { // 每页显示个数改变的函数
    pageSize.value = val
  }

  const adminList = computed(() => {
    // 截取数组的某一些项
    // 深拷贝数据作为备份
    const arr = JSON.parse(JSON.stringify(originalList.value))
    const newArr = arr.splice((currentPage.value - 1) * pageSize.value, pageSize.value) // 根据页码和每页显示个数截取数据
    // console.log(originalList.value)
    return newArr
  })

  onMounted(() => {
    getAdminList().then(res => {
      // console.log('admin', res.data)
      originalList.value = res.data.data
    })
  })


</script>

<template>
  <el-table :data="adminList" style="width: 100%">
    <el-table-column label="序号">
      <template #default="scope">
        <!-- scope.$index 代表索引值 -->
        <span>{{ scope.$index + 1 }}</span>
      </template>
    </el-table-column>
    <el-table-column prop="adminname" label="管理员账户" width="180" />
    <el-table-column prop="role" label="角色" width="180" >
      <template #default="scope">
        <!-- scope.row 代表一条数据 -->
        <el-tag v-if="scope.row.role === 2" class="ml-2" type="success">超级管理员</el-tag>
        <el-tag v-else class="ml-2" type="info">管理员</el-tag>
      </template>
    </el-table-column>
    <el-table-column label="操作">
      <template #default="scope">
        <el-button size="small"
          >编辑</el-button
        >
        <el-button
          size="small"
          type="danger"
          >删除</el-button
        >
      </template>
    </el-table-column>
  </el-table>
  <el-pagination 
   background    <!-- 分页组件的背景色 -->
    layout="sizes, prev, pager, next"    <!-- 分页组件的布局，包含可选择的每页条数、上一页、页码和下一页 -->
    :page-sizes="[5, 10, 20, 30]"    <!-- 分页组件可选择的每页条数 -->
    :total="originalList.length"    <!-- 分页组件的总页数，根据原始列表的长度计算得出 -->
    @current-change="changeCurrentPage"    <!-- 当前页发生改变时触发的事件，调用changeCurrentPage方法 -->
    @size-change="changeSize"    <!-- 每页条数发生改变时触发的事件，调用changeSize方法 -->
    />
</template>
```

## 10.3 删除管理员

### 10.3.1删除管理员接口

```js
// src/api/admin.js
import request from '@/utils/request'

export function adminLogin (params) {
  return request.post('/admin/login', params)
}
export function getAdminList () {
  return request.get('/admin/list')
}
//删除管理员接口
export function deleteAdmin (params) {
  return request.post('/admin/delete', params)
}
```



```vue
<!-- src/views/account/Admin.vue -->
<script  setup>
  import { ref, onMounted, computed } from 'vue';
  import { getAdminList, deleteAdmin } from '@/api/admin'

 

  // 将展示数据adminList 变为了 计算属性的数据
  // 将依据原始数据 originalList 以及 页码currentPage  和每页显示个数pageSize 一起计算出来显示的数据adminList

  const currentPage = ref(1)
  const pageSize = ref(10)
  const originalList = ref([])
  const changeCurrentPage = () => { // 页码改变函数
    currentPage.value = val
  }
  const changeSize = () => { // 每页显示个数改变的函数
    pageSize.value = val
  }

  const adminList = computed(() => {
    // 截取数组的某一些项
    // 深拷贝数据作为备份
    // const arr = JSON.parse(JSON.stringify(originalList.value))
    // const newArr = arr.splice((currentPage.value - 1) * pageSize.value, pageSize.value)
    const newArr = originalList.value.filter((item, index) => {
      return index >= (currentPage.value - 1) * pageSize.value && index < (currentPage.value - 1) * pageSize.value + pageSize.value
    })
    // console.log(originalList.value)
    return newArr
  })
  const getAdminListData = () => {
    getAdminList().then(res => {
      // console.log('admin', res.data)
      originalList.value = res.data.data
    })
  }
  onMounted(() => {
    getAdminListData()
  })

  const removeItem = (adminid) => {
    deleteAdmin({ adminid }).then(() => {
      getAdminListData()
    })
  }
</script>

<template>
  <el-table :data="adminList" style="width: 100%">
    <el-table-column label="序号">
      <template #default="scope">
        <!-- scope.$index 代表索引值 -->
        <span>{{ (currentPage - 1) * pageSize + scope.$index + 1 }}</span>
      </template>
    </el-table-column>
    <el-table-column prop="adminname" label="管理员账户" width="180" />
    <el-table-column prop="role" label="角色" width="180" >
      <template #default="scope">
        <!-- scope.row 代表一条数据 -->
        <el-tag v-if="scope.row.role === 2" class="ml-2" type="success">超级管理员</el-tag>
        <el-tag v-else class="ml-2" type="info">管理员</el-tag>
      </template>
    </el-table-column>
    <el-table-column label="操作">
      <template #default="scope">
        <el-button size="small"
          >编辑</el-button
        >
        <el-popconfirm title="确定删除吗?" @confirm="removeItem(scope.row.adminid)">
          <template #reference>
            <el-button
              size="small"
              type="danger"
              >删除</el-button
            >
          </template>
        </el-popconfirm>
        
      </template>
    </el-table-column>
  </el-table>
  <el-pagination 
    background 
    layout="sizes, prev, pager, next" 
    :page-sizes="[5, 10, 20, 30]"
    :total="originalList.length" 
    @current-change="changeCurrentPage"
    @size-change="changeSize"
    />
</template>
```

## 10.4 添加管理员

### 10.4.1 封装添加管理员接口

```js
// src/api/admin.js
import request from '@/utils/request'

export function adminLogin (params) {
  return request.post('/admin/login', params)
}
export function getAdminList () {
  return request.get('/admin/list')
}
//删除管理员接口
export function deleteAdmin (params) {
  return request.post('/admin/delete', params)
}
//添加管理员接口
export function addAdmin (params) {
  return request.post('/admin/add', params)
}
```

### 10.4.2 封装获取树形控件数据方法

```js
// src/utils/get-routes.js

export function getRoutes (menuList) {
  const arr = []
  menuList.forEach((item) => {
    let obj = {
      id: '',
      label: ''
    }
    if (item.meta) {
      if (item.children) { // 动态那些数据
          // 如果有children属性，则创建一个新的obj对象，包括id、label和children属性，并递归调用getRoutes函数处理children数组
        obj = {
          id: item.path,
          label: (item.meta.title),
          children: getRoutes(item.children)
        }
      } else {
            // 如果没有children属性，则创建一个新的obj对象，包括id和label属性
        obj = {
          id: item.path,
          label: (item.meta.title)
        }
      }
    } else {
         // 如果item没有meta属性，即没有动态数据，判断是否有children属性
      if (item.children) { // 系统首页
           // 如果有children属性，则创建一个新的obj对象，包括id和label属性，值分别为children数组的第一个元素的path和meta.title
        obj = {
          id: item.children[0].path,
          label: (item.children[0].meta.title)
        }
      }
    }
     //arr.push(obj)
    obj.id !== '' && arr.push(obj)
  });
  return arr
}

// getRoutes(menuList)
```

### 10.4.3 添加管理员

```vue
<!-- src/views/account/Admin.vue -->
<script  setup>
  import { ref, onMounted, computed } from 'vue';
  import { getAdminList, deleteAdmin, addAdmin } from '@/api/admin'
  import { constantRoutes, asyncRoutes } from '@/router'
  import { getRoutes } from '@/utils/get-routes'
 

  // 将展示数据adminList 变为了 计算属性的数据
  // 将依据原始数据 originalList 以及 页码currentPage  和每页显示个数pageSize 一起计算出来显示的数据adminList
 
  const currentPage = ref(1)
  const pageSize = ref(10)
  const originalList = ref([])
  const changeCurrentPage = (val) => { // 页码改变函数
    currentPage.value = val
  }
  const changeSize = (val) => { // 每页显示个数改变的函数
    pageSize.value = val
  }

  const adminList = computed(() => {
    // 截取数组的某一些项
    // 深拷贝数据作为备份
    // const arr = JSON.parse(JSON.stringify(originalList.value))
    // const newArr = arr.splice((currentPage.value - 1) * pageSize.value, pageSize.value)
    const newArr = originalList.value.filter((item, index) => {
      return index >= (currentPage.value - 1) * pageSize.value && index < (currentPage.value - 1) * pageSize.value + pageSize.value
    })
    // console.log(originalList.value)
    return newArr
  })
  const getAdminListData = () => {
    getAdminList().then(res => {
      // console.log('admin', res.data)
      originalList.value = res.data.data
    })
  }
  onMounted(() => {
    getAdminListData()
  })

  const removeItem = (adminid) => {
    deleteAdmin({ adminid }).then(() => {
      getAdminListData()
    })
  }

  // 添加管理员
  const drawer = ref(false)
  const adminname = ref('')
  const password = ref('')
  const role = ref(1)
  const checkedKeys = ref([])
  const menuList = [...constantRoutes, ...asyncRoutes]
  const treeData = getRoutes(menuList)

//使用sort()方法对数组进行排序是为了保证最终的checkedKeys数组是按照一定的顺序排列的。
//在这段代码中，obj对象的halfCheckedKeys和checkedKeys属性分别代表树状结构中半选中的节点和已选中的节点。这两个属性的值都是数组。
//通过将这两个数组合并成一个新的数组，并使用sort()方法对新数组进行排序，可以确保最终的checkedKeys数组中的元素是按照一定规则排列的。这样做有助于保持一致性和可预测性，方便后续对数组进行处理或者展示。
  const onTreeCheck = (_, obj) => {
    checkedKeys.value = [...obj.halfCheckedKeys, ...obj.checkedKeys].sort()
  }
   const treeAddRef = ref(null); // 在setup函数中添加ref引用
  const addAdminFn = () => {
    addAdmin({
      adminname: adminname.value,
      password: password.value,
      role: role.value,
      checkedKeys: checkedKeys.value
    }).then(() => {
      // 重置表单状态
      adminname.value = ''
      password.value = ''
      role.value = 1
      checkedKeys.value = []
      // 关闭抽屉效果
      drawer.value = false
      getAdminListData()
           // 重置树形控件的选中状态
       treeAddRef.value.setCheckedKeys([])
    })
  }
  const closeDrawer = () => {
    // 重置表单状态
    adminname.value = ''
    password.value = ''
    role.value = 1
    checkedKeys.value = []
    // 关闭抽屉效果
    drawer.value = false
  }
</script>

<template>
  <el-button type="primary" @click="drawer=true">添加管理员</el-button>
  <el-table :data="adminList" style="width: 100%">
    <el-table-column label="序号">
      <template #default="scope">
        <!-- scope.$index 代表索引值 -->
        <span>{{ (currentPage - 1) * pageSize + scope.$index + 1 }}</span>
      </template>
    </el-table-column>
    <el-table-column prop="adminname" label="管理员账户" width="180" />
    <el-table-column prop="role" label="角色" width="180" >
      <template #default="scope">
        <!-- scope.row 代表一条数据 -->
        <el-tag v-if="scope.row.role === 2" class="ml-2" type="success">超级管理员</el-tag>
        <el-tag v-else class="ml-2" type="info">管理员</el-tag>
      </template>
    </el-table-column>
    <el-table-column label="操作">
      <template #default="scope">
        <el-button size="small"
          >编辑</el-button
        >
        <el-popconfirm title="确定删除吗?" @confirm="removeItem(scope.row.adminid)">
          <template #reference>
            <el-button
              size="small"
              type="danger"
              >删除</el-button
            >
          </template>
        </el-popconfirm>
        
      </template>
    </el-table-column>
  </el-table>
  <el-pagination 
    background 
    layout="sizes, prev, pager, next" 
    :page-sizes="[5, 10, 20, 30]"
    :total="originalList.length" 
    @current-change="changeCurrentPage"
    @size-change="changeSize"
    />
    <!-- 添加管理员  抽屉效果 -->
    <el-drawer v-model="drawer" title="I am the title" :with-header="false" @close="closeDrawer">
      <h1>添加管理员</h1>
      <el-input v-model="adminname" placeholder="管理员账户" clearable/>
      <el-input v-model="password" placeholder="密码" clearable />
      <el-select v-model="role" placeholder="管理员角色" >
        <el-option
          label="管理员"
          :value="1"
        />
        <el-option
          label="超级管理员"
          :value="2"
        />
      </el-select>
      <el-tree
        ref=" treeAddRef"
        :data="treeData"
        show-checkbox
        node-key="id"
        @check="onTreeCheck"
      />
      <el-button type="primary" @click="addAdminFn">添加</el-button>
    </el-drawer>
</template>
```

## 10.5 编辑管理员

```js
// src/api/admin.js
import request from '@/utils/request'

export function adminLogin (params) {
  return request.post('/admin/login', params)
}
export function getAdminList () {
  return request.get('/admin/list')
}
//删除管理员接口
export function deleteAdmin (params) {
  return request.post('/admin/delete', params)
}
//添加管理员接口
export function addAdmin (params) {
  return request.post('/admin/add', params)
}

//编辑管理员接口
export function updateAdmin (params) {
  return request.post('/admin/update', params)
}
```

```vue
<!-- src/views/account/Admin.vue -->
<script setup>
  import { ref, onMounted, computed } from 'vue';
  import { getAdminList, deleteAdmin, addAdmin, updateAdmin } from '@/api/admin'
  import { constantRoutes, asyncRoutes } from '@/router'
  import { ElTree } from 'element-plus'
  import { getRoutes } from '@/utils/get-routes'


  // 将展示数据adminList 变为了 计算属性的数据
  // 将依据原始数据 originalList 以及 页码currentPage  和每页显示个数pageSize 一起计算出来显示的数据adminList
 
  const currentPage = ref(1)
  const pageSize = ref(10)
  const originalList = ref([])
  const changeCurrentPage = (val) => { // 页码改变函数
    currentPage.value = val
  }
  const changeSize = (val) => { // 每页显示个数改变的函数
    pageSize.value = val
  }

  const adminList = computed(() => {
    // 截取数组的某一些项
    // 深拷贝数据作为备份
    // const arr = JSON.parse(JSON.stringify(originalList.value))
    // const newArr = arr.splice((currentPage.value - 1) * pageSize.value, pageSize.value)
    const newArr = originalList.value.filter((item, index) => {
      return index >= (currentPage.value - 1) * pageSize.value && index < (currentPage.value - 1) * pageSize.value + pageSize.value
    })
    // console.log(originalList.value)
    return newArr
  })
  const getAdminListData = () => {
    getAdminList().then(res => {
      console.log('admin', res.data)
      originalList.value = res.data.data
    })
  }
  onMounted(() => {
    getAdminListData()
  })

  const removeItem = (adminid) => {
    deleteAdmin({ adminid }).then(() => {
      getAdminListData()
    })
  }

  // 添加管理员
  const drawer = ref(false)
  const adminname = ref('')
  const password = ref('')
  const role = ref(1)
  const checkedKeys = ref([])
  const menuList = [...constantRoutes, ...asyncRoutes]
  const treeData = getRoutes(menuList)
  const onTreeCheck = (_, obj) => {
    checkedKeys.value = [...obj.halfCheckedKeys, ...obj.checkedKeys].sort()
  }
  const addAdminFn = () => {
    addAdmin({
      adminname: adminname.value,
      password: password.value,
      role: role.value,
      checkedKeys: checkedKeys.value
    }).then(() => {
      // 重置表单状态
      adminname.value = ''
      password.value = ''
      role.value = 1
      checkedKeys.value = []
      // 关闭抽屉效果
      drawer.value = false
      getAdminListData()
    })
  }
  const closeDrawer = () => {
    // 重置表单状态
    adminname.value = ''
    role.value = 1
    checkedKeys.value = []
    // 关闭抽屉效果
    drawer.value = false
  }

  // 修改管理员
  const treeUpdateRef = ref()
  const dialog = ref(false)
  const updateAdminInfo = (item) => {
    dialog.value = true
    adminname.value = item.adminname
    role.value = item.role
    // console.log(item)
    // checkedKeys.value = item.checkedKeys
    // 添加延时器确保DOM加载完毕， 否则显示 setCheckedKeys 未定义
    setTimeout(() => {
      treeUpdateRef.value.setCheckedKeys(item.checkedKeys, false)
    }, 0)
  }
  const updateAdminInfoFn = () => {
    // console.log('111', {
    //   adminname: adminname.value,
    //   role: role.value,
    //   checkedKeys: checkedKeys.value
    // })
    updateAdmin({
      adminname: adminname.value,
      role: role.value,
      checkedKeys: checkedKeys.value
    }).then((res) => {
      // console.log('22222', res.data)
      // 重置表单状态
      adminname.value = ''
      role.value = 1
      checkedKeys.value = []
      // 关闭抽屉效果
      dialog.value = false
      getAdminListData()
    })
  }
</script>

<template>
  <el-button type="primary" @click="drawer=true">添加管理员</el-button>
  <el-table :data="adminList" style="width: 100%">
    <el-table-column label="序号">
      <template #default="scope">
        <!-- scope.$index 代表索引值 -->
        <span>{{ (currentPage - 1) * pageSize + scope.$index + 1 }}</span>
      </template>
    </el-table-column>
    <el-table-column prop="adminname" label="管理员账户" width="180" />
    <el-table-column prop="role" label="角色" width="180" >
      <template #default="scope">
        <!-- scope.row 代表一条数据 -->
        <el-tag v-if="scope.row.role === 2" class="ml-2" type="success">超级管理员</el-tag>
        <el-tag v-else class="ml-2" type="info">管理员</el-tag>
      </template>
    </el-table-column>
    <el-table-column label="操作">
      <template #default="scope">
        <el-button size="small" @click="updateAdminInfo(scope.row)">编辑</el-button>
        <el-popconfirm title="确定删除吗?" @confirm="removeItem(scope.row.adminid)">
          <template #reference>
            <el-button
              size="small"
              type="danger"
              >删除</el-button
            >
          </template>
        </el-popconfirm>
        
      </template>
    </el-table-column>
  </el-table>
  <el-pagination 
    background 
    layout="sizes, prev, pager, next" 
    :page-sizes="[5, 10, 20, 30]"
    :total="originalList.length" 
    @current-change="changeCurrentPage"
    @size-change="changeSize"
    />
    <!-- 添加管理员  抽屉效果 -->
    <el-drawer v-model="drawer" title="I am the title" :with-header="false" @close="closeDrawer">
      <h1>添加管理员</h1>
      <el-input v-model="adminname" placeholder="管理员账户" clearable/>
      <el-input v-model="password" placeholder="密码" clearable />
      <el-select v-model="role" placeholder="管理员角色" >
        <el-option
          label="管理员"
          :value="1"
        />
        <el-option
          label="超级管理员"
          :value="2"
        />
      </el-select>
      <el-tree
        ref="treeAddRef"
        :data="treeData"
        show-checkbox
        node-key="id"
        @check="onTreeCheck"
      />
      <el-button type="primary" @click="addAdminFn">添加</el-button>
    </el-drawer>
    <!-- 编辑管理员 -->
    <el-dialog v-model="dialog" title="编辑管理员信息">
      <el-input v-model="adminname" readonly placeholder="管理员账户" clearable/>
      <el-select v-model="role" placeholder="管理员角色" >
        <el-option
          label="管理员"
          :value="1"
        />
        <el-option
          label="超级管理员"
          :value="2"
        />
      </el-select>
      <el-tree
        ref="treeUpdateRef"
        :data="treeData"
        show-checkbox
        node-key="id"
        @check="onTreeCheck"
      />
      <template #footer>
        <span class="dialog-footer">
          <el-button type="primary" @click="updateAdminInfoFn">
            修改
          </el-button>
        </span>
      </template>
    </el-dialog>
</template>
```



# 11.左侧菜单栏动态渲染

## 11.1 处理左侧菜单数据

此算法建议直接拿来使用

```js
// src/utils/get-menu-list.js

// 导出一个名为getMenuList的函数，接收两个参数menus和checkedkeys
export function getMenuList (menus, checkedkeys) {
  // 如果没有设置权限，那么即将拥有所有的权限
  if (checkedkeys.length === 0) {
    checkedkeys = ['/home', '/banner', '/banner/list', '/banner/list/home', '/banner/list/kind', '/banner/add', '/pro', '/pro/list', '/pro/search', '/account', '/account/user', '/account/admin']
  }
  
  // 调用getResult函数，将结果存储在result变量中
  let result = getResult(menus)

  // 定义名为getResult的函数，接收一个参数menus
  function getResult(menus) {
    // 定义一个空数组arr
    let arr= []
    
    // 遍历menus数组中的每个元素
    menus.forEach(item => {
      // 如果item对象中有meta属性
      if (item.meta) {
        // 如果checkedkeys数组中包含item对象的path属性值
        if (checkedkeys.includes(item.path)) {
          // 将item对象的复制版本添加到arr数组中
          arr.push({...item})
          
          // 如果item对象中有children属性
          if (item.children) {
            // 将getResult函数的结果赋值给arr数组中最后一个元素的children属性
            arr[arr.length - 1].children = getResult(item.children)
          }
        }
      } else { // 系统首页
        // 将item对象添加到arr数组中
        arr.push(item)
      }
    });
    
    // 返回arr数组
    return arr 
  }
  
  // 返回result变量
  return result
} 
```

## 11.2 动态渲染左侧菜单

```vue
<!-- src/layout/components/Sidebar/index.vue -->
<script  setup>
  import { ref } from 'vue'
  import SidebarItem from './SidebarItem.vue'
  import Logo from './../logo/index.vue'
  import { getMenuList } from '@/utils/get-menu-list'

  // 整合路由
  import { constantRoutes, asyncRoutes } from '@/router'
  import { useRoute } from 'vue-router';
  // /banner,/banner/add,/banner/list,/banner/list/home,/banner/list/kind,/home
  const checkedkeys = localStorage.getItem('adminname') !== 'admin' ? localStorage.getItem('checkedkeys').split(',') : []
  console.log('checkedkeys', checkedkeys)
  // const menuList = constantRoutes.concat(asyncRoutes) // 所有数据
  const menuList = getMenuList(constantRoutes.concat(asyncRoutes), checkedkeys) // 真实数据
  // console.log(menuList)

  // 获取路由地址
  // 选项式API  this.$route
  const route = useRoute()
  // console.log(route) // route.path.value

  const collapse = ref(false)
</script>
<template>
  <el-aside :width="collapse ? '50px' : '200px'">
    <!-- <div class="logo"></div> -->
    <Logo :collapse="collapse"/>
    <!-- 菜单组件
    https://element-plus.gitee.io/zh-CN/component/menu.html#%E4%BE%A7%E6%A0%8F
    -->
    <!-- <div>左侧菜单</div> -->
    <el-menu
      :collapse="collapse"
      :unique-opened="true"
      :default-active="route.path"
      background-color="#001529"
      text-color="#fff"
      :collapse-transition="false"
    >
      <!-- 路由中的每一个选项都需要单独去渲染菜单项
      有的不需要出现在左侧的菜单栏
      有的只有一个菜单项
      有的有二级菜单和三级菜单
      建议把每个菜单项单独封装成一个组件  SidebarItem
      登录  系统首页   产品管理   账户管理  轮播图管理
      将每一项数据 item 传输到子组件，子组件接收数据，并且渲染
      -->
      <SidebarItem 
        v-for="item of menuList"
        :key="item.path"
        :item = "item"
      ></SidebarItem>
    </el-menu>
    <div class="changeIcon" :style="{ width: collapse ? '50px' : '200px'}">
      <el-icon color="#fff" v-if="collapse" @click="collapse = !collapse"><ArrowRight /></el-icon>
      <el-icon color="#fff" v-else @click="collapse=!collapse"><ArrowLeft /></el-icon>
    </div>
  </el-aside>
</template>

<style lang="scss">
.changeIcon {
  position: absolute;
  bottom: 10px;
  display: flex;
  justify-content: center;
}
</style>
```


