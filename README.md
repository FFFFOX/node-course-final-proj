## 前言

此项目是 Vue + TypeScript + Bootstrap 仿造知乎专栏构建的（🤖）项目，它的接口[zhiye-api](https://github.com/liangtiao4/zhiye-api.git) 是用 Node.js express 框架实现的，数据从MySQL数据库获取，具有真实的登录、注册、权限验证、专栏、文章等功能。

## 技术栈1

Vue3 + Vuex + vue-router + ES6  + TypeScript + Bootstrap4 + express + nodemon + MySQL

## 后台项目运行

1 下载项目

```
git clone https://github.com/liangtiao4/zhiye-api
```

2 修改数据库配置

在 /config/db.js 文件中修改 database 和 password

```
MYSQL_CONF = {
    host: 'localhost',
    port: '3306',
    database: 'test_db',  // 你的数据库
    user: 'root',
    password: '123456'    // 你的密码
  }
```

3 运行项目

```
cd zhiye-api

npm install

npm run start.dev
```

## 实现功能

- [x] 登录接口（post） -- 完成
- [x] 用户信息接口（post） -- 完成
- [x] 注册接口（post） -- 完成
- [x] 验证邮箱接口（post） -- 完成
- [x] 专栏列表接口（get） -- 完成
- [x] 专栏详情接口（get） -- 完成
- [x] 文章接口（get） -- 完成
- [x] 文章详情接口（get） -- 完成
- [x] 新建文章接口（post） -- 完成

## 前端项目运行


```
git clone https://https://github.com/liangtiao4/vue3-zhiye.git

cd vue3-zhiye

npm install (安装node_modules依赖)

npm run serve (运行项目)

App running at: http://localhost:8080/
```



## 文件结构 

```
│  package-lock.json								// 包信息
│  package.json								        // 包管理
│  README.md							        	// 说明文档
│  tsconfig.json								    // ts配置文件
│
├─effectDiagram										// 项目效果图
│      1.login.png									// 登录页
│      2.home-login.png								// 首页（登录时）
│      3.home-logout.png							// 首页（未登录）
│      4.column.png									// 专栏
│      5.colum-detail.png							// 专栏详情
│      6.create.png									// 创建文章
│
├─public											// 公共资源
│      index.html									// 入口html文件
│      title_icon.png								// 图标
│
└─src
    │  App.vue										// 页面入口
    │  main.ts										// 程序入口文件，加载各种公共组件
    │  public.css									// 公共样式
    │  router.ts								    // 路由
    │  shims-vue.d.ts								// vue 兼容 ts 配置
    │
    ├─components									// 组件
    │      ColumnList.vue							// 专栏列表
    │      Dropdown.vue								// 下拉框
    │      DropdownItem.vue							// 下拉框子项目
    │      GlobalFooter.vue							// 全局底部
    │      GlobalHeader.vue							// 全局头部导航栏
    │      HomeItem.vue								// 首页项目
    │      Loader.vue								// 加载动画
    │      PostList.vue								// 文章列表
    │      Toast.vue								// 轻提示
    │      TopicList.vue							// 专题列表
    │      UploadFile.vue							// 图片/文件上传
    │      ValidateForm.vue							// 验证表单
    │      ValidateInput.vue						// 验证文本框/文本域
    │
    ├─hooks											// 钩子
    │      useClickOutside.ts						// 区域外点击
    │      useCreateToast.ts						// 生成轻提示
    │
    ├─http
    │      index.ts									// http请求
    │
    ├─store
    │      index.ts									// 状态管理
    │      type.ts									// 数据类型
    │
    ├─utils											// 工具
    │      getCurrentTime.ts					    // 获取当前时间
    │      validateRules.ts                      	// 验证规则
    │
    └─views											// 路由页面
            Column.vue								// 专栏页
            ColumnDetail.vue						// 专栏详情页
            CreatePost.vue							// 创建文章页
            Home.vue								// 首页
            Login.vue								// 登录页
            Register.vue							// 注册页
```
