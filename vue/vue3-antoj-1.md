# 码艺OJ 项目开发文档

## 项目概述
码艺OJ（蚂蚁Ant，代码的艺术）是一个在线编程学习平台，旨在提供丰富的编程题库和学习资源，以帮助用户自由地学习和提升计算机知识。平台拥有多个题库和题目分类，提供在线编程环境、提交和评测系统、学习资源、排行榜和竞赛、社区和讨论等功能。

## 功能特点
1. **题库和题目分类**
   - 支持多个题库和丰富的题目分类。
   - 覆盖各种编程语言和算法题目。
   - 用户可以根据兴趣和需求选择题目进行练习和学习。
2. **在线编程环境**
   - 提供完整的在线编程环境，用户无需安装开发工具。
   - 用户可以在网页上编写、调试和运行代码。
3. **提交和评测系统**
   - 用户可以提交自己编写的代码进行评测。
   - 系统自动进行代码评测，给出结果和反馈。
   - 帮助用户检查代码正确性和性能。
4. **学习资源**
   - 提供丰富的学习资源，包括编程教程、视频课程、技术文章等。
   - 帮助用户系统地学习和掌握各种计算机知识。
5. **排行榜和竞赛**
   - 设有排行榜，用户可以通过解题和竞赛展示编程能力。
   - 定期举办编程竞赛，用户可以与其他用户比较和交流。
6. **社区和讨论**
   - 提供活跃的社区平台，用户可以交流、讨论问题、分享经验。
   - 用户可以相互学习、互相帮助。





## 模块划分



1. **题库管理模块**
   - 题目分类管理
   - 题目列表展示
   - 题目详情页面

2. **在线编程模块**
   - 在线代码编辑器集成
   - 代码运行和调试功能

3. **提交和评测模块**
   - 提交代码页面
   - 评测结果展示

4. **学习资源模块**
   - 编程教程页面
   - 视频课程展示
   - 技术文章展示

5. **排行榜和竞赛模块**
   - 排行榜展示
   - 编程竞赛页面

6. **社区和讨论模块**
   - 帖子列表展示
   - 帖子详情页面
   - 用户评论和交流功能

7. **界面美化和优化模块**
   - 项目整体界面设计
   - 用户体验优化
   - 响应速度优化

8. **测试和部署模块**
   - 单元测试和集成测试
   - 项目部署到服务器



## 配置vue3环境

1. 打开命令行终端。
2. 进入 希望创建项目的目录，例如：`G:\video\web_front\env`。
3. 运行以下命令来创建一个新的 Vue 3 项目：

```sh
npm create vue@latest
```

4. 在执行命令后， 会看到一系列配置选项。根据 的需求选择合适的选项，例如：
   - 是否添加 TypeScript 支持：选择 Yes 或 No，根据 是否需要 TypeScript。
   - 是否添加 JSX 支持：选择 Yes 或 No，根据 是否需要 JSX。
   - 是否添加 Vue Router：选择 Yes 或 No，根据 是否需要 Vue Router。
   - 是否添加 Pinia（状态管理库）：选择 Yes 或 No，根据 是否需要使用 Pinia。
   - 是否添加 Vitest（单元测试工具）：选择 Yes 或 No，根据 是否需要单元测试。
   - 是否添加 Cypress（端到端测试工具）：选择 Cypress。
   - 是否添加 ESLint（代码质量工具）：选择 Yes 或 No，根据 是否需要 ESLint。
   - 是否添加 Prettier（代码格式化工具）：选择 Yes 或 No，根据 是否需要 Prettier。

5. 根据 的选择，命令行会在指定目录下创建一个名为 `ant-oj-vue3` 的项目文件夹，并进行项目的初始化。
6. 进入项目文件夹：

```sh
cd ant-oj-vue3
```

7. 运行以下命令来安装项目的依赖：

```sh
npm install
```

8. 如果 在步骤 4 中选择了添加 Prettier 和 ESLint，运行以下命令来格式化代码并运行代码质量检查：

```sh
npm run format
```

9. 运行以下命令来启动开发服务器：

```sh
npm run dev
```

现在 的 Vue 3 项目已经成功创建并运行起来了。 可以在浏览器中访问相应的地址（通常是 `http://localhost:3000`）来查看项目运行效果。根据 的实际需求，进一步开发和配置项目。



### pinia持久化插件

使用 `pinia-plugin-persistedstate` 实现状态持久化：

1. 安装 `pinia` 和 `pinia-plugin-persistedstate`：

```bash
npm install pinia pinia-plugin-persistedstate
```

2. 在应用程序的入口文件中设置插件：

```javascript
// main.js
import { createApp } from 'vue';
import { createPinia } from 'pinia';
import App from './App.vue';
import piniaPersistedstate from 'pinia-plugin-persistedstate';

const app = createApp(App);
const pinia = createPinia();

// 使用 pinia-plugin-persistedstate 插件
pinia.use(piniaPersistedstate);

app.use(pinia);
app.mount('#app');
```



### 按需导入Element plus

按需导入是一种在项目中只导入你实际需要使用的 Element Plus 组件的方法，以减小项目的体积。以下是按需导入 Element Plus 的步骤：

1. 首先，安装 Element Plus 和所需插件：

   ```bash
   npm install element-plus
   npm install -D unplugin-vue-components unplugin-auto-import
   ```

2. 在你的构建工具配置文件中（如 `vite.config.ts` 或 `webpack.config.js`）进行插件配置。以下是在 Vite 中的配置示例：

   ```javascript
   // vite.config.ts
   import { defineConfig } from 'vite'
   import AutoImport from 'unplugin-auto-import/vite'
   import Components from 'unplugin-vue-components/vite'
   import { ElementPlusResolver } from 'unplugin-vue-components/resolvers'

   export default defineConfig({
     // ...
     plugins: [
       // ...
       AutoImport({
         resolvers: [ElementPlusResolver()],
       }),
       Components({
         resolvers: [ElementPlusResolver()],
       }),
     ],
   })
   ```

   在这个配置中，我们使用了 `unplugin-auto-import` 和 `unplugin-vue-components` 插件，同时配置了 `ElementPlusResolver` 来实现按需导入 Element Plus 组件。

3. 在你的代码中使用 Element Plus 组件时，无需手动导入组件，它们会自动被按需导入。例如：

   ```vue
   <template>
     <el-button type="primary">Primary Button</el-button>
   </template>
   ```

通过按需导入，只有你实际使用到的 Element Plus 组件会被导入，从而减小了项目的体积，提升了项目性能。这种方法能够让你更加高效地使用 Element Plus 来构建界面。



### 安装字体图标

可以使用以下命令来安装 Element Plus 的图标库：

```sh
npm install @element-plus/icons-vue
```

或者使用 Yarn 安装：

```sh
yarn add @element-plus/icons-vue
```

在main.ts里面配置

```ts
import * as ElementPlusIconsVue from '@element-plus/icons-vue'

const app = createApp(App)
for (const [key, component] of Object.entries(ElementPlusIconsVue)) {
  app.component(key, component)
}
```

这样就可以安装 Element Plus 的图标库，然后就可以在 Vue 组件中使用 Element Plus 提供的字体图标了。



### 安装 Sass 

1. 首先，确保你已经安装了 Node.js 和 npm。你可以在终端中运行以下命令来检查是否已安装：

```sh
node -v
npm -v
```

2. 如果你已经安装了 Node.js 和 npm，那么可以通过以下命令全局安装 Sass：

```sh
npm install -D sass
```



### `index.html` 

在 `index.html` 中，需要修改图标和标题

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8">
    <link rel="icon" href="/AntOJ-icon.png">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AntOJ</title>
  </head>
  <body>
    <div id="app"></div>
    <script type="module" src="/src/main.ts"></script>
  </body>
</html>
```













































# 社区和讨论模块

## 文件结构

```
src/
|-- views/
|   |-- Login/
|   |   |-- LoginView.vue          // 登录页面
|   |   |-- RegisterView.vue       // 注册页面
|   |-- User/
|   |    |-- ProfileView.vue    // 用户信息页面
|   |    |-- AvatarView.vue     // 更换头像页面
|   |    |-- PasswordView.vue   // 修改密码页面
|   |-- Community/
|   |   |-- Article/
|   |    |   |-- ArticleListView.vue    // 文章列表页面
|   |    |   |-- ArticleDetailView.vue  // 文章详情页面
|   |    |   |-- ArticleCreateView.vue  // 发布文章页面
|   |    |   |-- ArticleManageView.vue  // 文章管理页面
```



## 路由配置：

```javascript
const routes = [
  {
    path: '/login',
    name: 'Login',
    component: () => import('../views/Login/LoginView.vue'),
  },
  {
    path: '/register',
    name: 'Register',
    component: () => import('../views/Login/RegisterView.vue'),
  },
  {
    path: '/user',
    name: 'UserLayout',
    component: () => import('../views/User/UserLayout.vue'),
    children: [
      {
        path: 'profile',
        name: 'UserProfile',
        component: () => import('../views/User/ProfileView.vue'),
      },
      {
        path: 'avatar',
        name: 'UserAvatar',
        component: () => import('../views/User/AvatarView.vue'),
      },
      {
        path: 'password',
        name: 'UserPassword',
        component: () => import('../views/User/PasswordView.vue'),
      },
    ],
  },
  {
    path: '/community',
    name: 'CommunityLayout',
    component: () => import('../views/Community/CommunityLayout.vue'),
    children: [
      {
        path: 'articles',
        name: 'ArticleList',
        component: () => import('../views/Community/Article/ArticleListView.vue'),
      },
      {
        path: 'articles/:id',
        name: 'ArticleDetail',
        component: () => import('../views/Community/Article/ArticleDetailView.vue'),
      },
      {
        path: 'create-article',
        name: 'ArticleCreate',
        component: () => import('../views/Community/Article/ArticleCreateView.vue'),
      },
      {
        path: 'manage-articles',
        name: 'ArticleManage',
        component: () => import('../views/Community/Article/ArticleManageView.vue'),
      },
    ],
  },
];

export default routes;

```



## 组件划分

以下是组件代码示例：

1. **LoginView.vue** - 登录页面组件

```vue
<template>
  <div>
    <h1>Login</h1>
    <!-- 登录表单和逻辑 -->
  </div>
</template>

<script>
export default {
  name: 'LoginView',
  // 组件逻辑和方法
}
</script>
```

2. **RegisterView.vue** - 注册页面组件

```vue
<template>
  <div>
    <h1>Register</h1>
    <!-- 注册表单和逻辑 -->
  </div>
</template>

<script>
export default {
  name: 'RegisterView',
  // 组件逻辑和方法
}
</script>
```

3. **ProfileView.vue** - 用户信息页面组件

```vue
<template>
  <div>
    <h1>User Profile</h1>
    <!-- 用户信息展示和编辑表单 -->
  </div>
</template>

<script>
export default {
  name: 'ProfileView',
  // 组件逻辑和方法
}
</script>
```

4. **AvatarView.vue** - 更换头像页面组件

```vue
<template>
  <div>
    <h1>Change Avatar</h1>
    <!-- 头像上传和更换逻辑 -->
  </div>
</template>

<script>
export default {
  name: 'AvatarView',
  // 组件逻辑和方法
}
</script>
```

5. **PasswordView.vue** - 修改密码页面组件

```vue
<template>
  <div>
    <h1>Change Password</h1>
    <!-- 修改密码表单和逻辑 -->
  </div>
</template>

<script>
export default {
  name: 'PasswordView',
  // 组件逻辑和方法
}
</script>
```

6. **ArticleListView.vue** - 文章列表页面组件

```vue
<template>
  <div>
    <h1>Article List</h1>
    <!-- 文章列表展示 -->
  </div>
</template>

<script>
export default {
  name: 'ArticleListView',
  // 组件逻辑和方法
}
</script>
```

7. **ArticleDetailView.vue** - 文章详情页面组件

```vue
<template>
  <div>
    <h1>Article Detail</h1>
    <!-- 文章内容展示和评论功能 -->
  </div>
</template>

<script>
export default {
  name: 'ArticleDetailView',
  // 组件逻辑和方法
}
</script>
```

8. **ArticleCreateView.vue** - 发布文章页面组件

```vue
<template>
  <div>
    <h1>Create Article</h1>
    <!-- 文章发布表单和逻辑 -->
  </div>
</template>

<script>
export default {
  name: 'ArticleCreateView',
  // 组件逻辑和方法
}
</script>
```

9. **ArticleManageView.vue** - 文章管理页面组件

```vue
<template>
  <div>
    <h1>Manage Articles</h1>
    <!-- 文章管理列表和操作 -->
  </div>
</template>

<script>
export default {
  name: 'ArticleManageView',
  // 组件逻辑和方法
}
</script>
```

### App.vue

```vue
<template>
  <div>
    <router-view></router-view>
  </div>
</template>

<script>
export default {
  name:'App'
}
</script>

<style scoped>
</style>

```





### LoginView.vue

![image-20230812124823027](C:\Users\86157\AppData\Roaming\Typora\typora-user-images\image-20230812124823027.png)

下面是一个简单的登录页面的代码，使用了 Vue 3 和 Element Plus。

```vue
<template>
  <div class="login-container">
    <h2 class="login-title">用户登录</h2>
    <el-form :model="loginForm" ref="loginForm" class="login-form">
      <el-form-item label="用户名" prop="username">
        <el-input v-model="loginForm.username" placeholder="请输入用户名"></el-input>
      </el-form-item>
      <el-form-item label="密码" prop="password">
        <el-input
          v-model="loginForm.password"
          type="password"
          placeholder="请输入密码"
        ></el-input>
      </el-form-item>
      <el-form-item>
        <el-button type="primary" @click="login">登录</el-button>
      </el-form-item>
      <el-form-item>
        <router-link to="/register">没有账号？立即注册</router-link>
      </el-form-item>
    </el-form>
  </div>
</template>

<script>
import { ref } from 'vue';

export default {
  name: 'LoginView',
  data() {
    return {
      loginForm: {
        username: '',
        password: '',
      },
    };
  },
  methods: {
    login() {
      // 登录逻辑
    },
  },
};
</script>

<style scoped>
.login-container {
  max-width: 400px;
  margin: 0 auto;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.login-title {
  text-align: center;
  font-size: 24px;
  margin-bottom: 20px;
}

.login-form {
  text-align: center;
}

.login-form .el-form-item {
  margin-bottom: 15px;
}

.login-form .el-button {
  width: 100%;
}
</style>
```



使用字体图标

```vue
<el-input v-model="loginForm.username">
  <template #prefix>
    <el-icon><User /></el-icon>
  </template>
</el-input>
```





### RegisterView.vue

![image-20230812124226742](C:\Users\86157\AppData\Roaming\Typora\typora-user-images\image-20230812124226742.png)

下面是一个简单的用户注册页面 `RegisterView.vue` 的代码：

```vue
<template>
  <div class="register-container">
    <el-card class="register-card">
      <h2 class="register-title">用户注册</h2>
      <el-form ref="registerForm" :model="registerForm" label-width="80px">
        <el-form-item label="用户名：" prop="username">
          <el-input v-model="registerForm.username" placeholder="请输入用户名"></el-input>
        </el-form-item>
        <el-form-item label="密码：" prop="password">
          <el-input
            v-model="registerForm.password"
            placeholder="请输入密码"
            type="password"
          ></el-input>
        </el-form-item>
        <el-form-item label="重复密码：" prop="repeatPassword">
          <el-input
            v-model="registerForm.repeatPassword"
            placeholder="请再次输入密码"
            type="password"
          ></el-input>
        </el-form-item>
        <el-form-item>
          <el-button class="register-button" type="primary" @click="register">注册</el-button>
        </el-form-item>
        <el-form-item>
          <span class="login-link">已有账户？<a @click="goToLogin">立即登录</a></span>
        </el-form-item>
      </el-form>
    </el-card>
  </div>
</template>

<script>
export default {
  data() {
    return {
      registerForm: {
        username: '',
        password: '',
        repeatPassword: ''
      }
    };
  },
  methods: {
    register() {
      // 实现注册逻辑
    },
    goToLogin() {
      // 跳转到登录页面
    }
  }
};
</script>

<style scoped>
.register-container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

.register-card {
  width: 360px;
}

.register-title {
  text-align: center;
  margin-bottom: 20px;
}

.register-button {
  width: 100%;
}

.login-link {
  text-align: center;
  display: block;
  margin-top: 10px;
  font-size: 12px;
  color: #999;
}
</style>
```



### 校验LoginView.vue

```vue
<template>
  <div class="login-container">
    <h2 class="login-title">用户登录</h2>
    <el-form :model="loginForm" class="login-form" ref="loginForm">
      <el-form-item  prop="username" :rules="loginRules.username">
        <el-input placeholder="请输入用户名" v-model="loginForm.username" >
          <template #prefix>
            <el-icon><User /></el-icon>
          </template>
        </el-input>
      </el-form-item>
      <el-form-item  prop="password" :rules="loginRules.password">
        <el-input placeholder="请输入密码" v-model="loginForm.password" type="password">
          <template #prefix>
            <el-icon><Lock /></el-icon>
          </template>
        </el-input>
      </el-form-item>
      <el-form-item>
        <el-button type="primary" @click="login">登录</el-button>
      </el-form-item>
      <el-form-item>
        没有账号？
        <router-link to="/register">立即注册</router-link>
      </el-form-item>
    </el-form>
  </div>
</template>

<script>
export default {
  name: 'LoginView',
  data() {
    return {
      loginForm: {
        username: '',
        password: '',
      },
      loginRules: {
        username: [
          { required: true, message: '用户名不能为空', trigger: 'blur' },
        ],
        password: [
          { required: true, message: '密码不能为空', trigger: 'blur' },
        ],
      },
    };
  },
  methods: {
    login() {
      // 登录逻辑
    },
  },
};
</script>

```



### 校验RegisterView.vue

普通校验规则

```vue
registerRules: {
        username: [
          { required: true, message: '用户名不能为空', trigger: 'blur' },
          { min: 3, max: 12, message: '用户名长度在 3 到 12 个字符', trigger: 'blur' },
          { pattern: /^[a-zA-Z0-9]+$/, message: '用户名只能包含字母和数字', trigger: 'blur' },
        ],
        password: [
          { required: true, message: '密码不能为空', trigger: 'blur' },
          { min: 6, max: 15, message: '密码长度在 6 到 15 个字符', trigger: 'blur' },
          { pattern: /^[a-zA-Z0-9_]+$/, message: '密码只能包含字母、数字和下划线', trigger: 'blur' },
        ],
        confirmPassword: [
          { required: true, message: '请再次输入密码', trigger: 'blur' },
          { validator: this.checkPasswordMatch, trigger: 'blur' },
        ],
      }
```

自定义校验规则

```vue
  methods: {
    register() {
      // 注册逻辑
    },
    checkPasswordMatch(rule, value, callback) {
      if (value !== this.registerForm.password) {
        callback(new Error('两次输入的密码不一致'));
      } else {
        callback();
      }
    },
  },
```



完整代码

```vue
<template>
  <div class="register-container">
    <h2 class="register-title">用户注册</h2>
    <el-form :model="registerForm" :rules="registerRules" class="register-form" ref="registerForm">
      <el-form-item  prop="username" >
        <el-input placeholder="用户名" v-model="registerForm.username" >
          <template #prefix>
            <el-icon><User /></el-icon>
          </template>
        </el-input>
      </el-form-item>
      <el-form-item  prop="password" >
        <el-input placeholder="请输入密码" v-model="registerForm.password" type="password">
          <template #prefix>
            <el-icon><Lock /></el-icon>
          </template></el-input>
      </el-form-item>
      <el-form-item  prop="confirmPassword" >
        <el-input placeholder="请重复密码" v-model="registerForm.confirmPassword" type="password">
          <template #prefix>
            <el-icon><Lock /></el-icon>
          </template></el-input>
      </el-form-item>
      <el-form-item>
        <el-button  type="primary"  @click="register">注册</el-button>
      </el-form-item>
      <el-form-item>
        已有账户？
        <router-link to="/login">立即登录</router-link>
      </el-form-item>
    </el-form>
  </div>
</template>

<script>
export default{
  name: 'registerView',
  data(){
    return {
      registerForm: {
        username: '',
        password: '',
        confirmPassword:''
      },
      registerRules:{
        username:[
          {required:true,message: '用户名不能为空',trigger: 'blur'},
          {min: 3, max: 12, message: '用户名长度在 3 到 12 个字符',trigger: 'blur'},
          { pattern: /^[a-zA-Z0-9]+$/,message: '用户名只能包含字母和数字',trigger: 'blur'}
        ],
        password:[
          {required:true,message: '密码不能为空',trigger: 'blur'},
          {min: 6, max: 15, message: '密码长度在 6 到 15 个字符',trigger: 'blur'},
          { pattern: /^[a-zA-Z0-9_]+$/,message: '密码只能包含字母、数字和下划线',trigger: 'blur'}
        ],
        confirmPassword:[
          { required: true, message: '请再次输入密码', trigger: 'blur'},
          {
            validator: this.checkPasswordMatch,
            trigger: 'blur'
          }
        ]
      }
    }
  },
  methods: {
    register() {
      // 注册逻辑
    },
    checkPasswordMatch(rule, value, callback){
      if(value !== this.registerForm.password ){
        callback(new Error('两次输入的密码不一致'));
      }else{
        callback();
      }
    }
  },
}
</script>

```



### 发送注册请求，实现跳转

可以在 `api` 文件夹中创建一个 `registerApi` 函数，以便测试。这个函数可以返回一个模拟的成功或失败响应。

假设 `api` 文件夹中有一个 `auth.js` 文件，用于存放认证相关的 API。在其中定义一个简单的 `registerApi` 函数：

```javascript
// api/auth.js

export function registerApi(userData) {
  // 在实际项目中，这里应该是发送注册请求到后端的代码
  // 这里只是一个简单的模拟，始终返回注册成功的结果
  return new Promise((resolve) => {
    // 假设这是模拟的异步操作
    setTimeout(() => {
      resolve({ success: true, message: '注册成功' });
    }, 1000);
  });
}
```

然后在组件中引入并使用这个模拟的 API 函数：

```vue
<script>
import { ref } from 'vue';
import { registerApi } from '../../api/auth'; // 引入模拟的 registerApi

export default {
  name: 'RegisterView',
  data() {
    return {
      // ... 其他 data
      registerForm: {
        username: '',
        password: '',
        confirmPassword: '',
      },
    };
  },
  methods: {
    async register() {
      try {
        // 首先等待表单的检验，调用 this.$refs.loginForm.validate() 方法
        const isValid = await this.$refs.registerForm.validate();
        if (!isValid) {
          return; // 表单校验失败，不继续执行
        }

        // 调用 API 函数发送注册请求
        const response = await registerApi(this.registerForm);

        // 根据后端返回的结果判断注册是否成功
        if (response.success) {
          // 注册成功，跳转到登录界面
          this.$router.push('/login');
        } else {
          // 注册失败，根据后端返回的错误信息给出提示
          console.log('注册失败')
        }
      } catch (error) {
        // 处理其他错误情况
        console.error('注册过程出现错误', error);
      }
    },
  },
};
</script>
```



### 发送登录请求，实现跳转

可以使用类似的逻辑来修改登录页面。以下是一个示例的修改过程：

1. 引入登录相关的 API 函数（假设在 `api/auth.js` 文件中定义了 `loginApi` 函数）：

```javascript
// api/auth.js

export function loginApi(userData) {
  // 在实际项目中，这里应该是发送登录请求到后端的代码
  // 这里只是一个简单的模拟，始终返回登录成功的结果
  return new Promise((resolve) => {
    // 假设这是模拟的异步操作
    setTimeout(() => {
      resolve({ success: true, message: '登录成功' });
    }, 1000);
  });
}
```

2. 修改登录页面组件的逻辑，类似于注册页面的逻辑，调用登录相关的 API 函数：

```vue
<template>
  <!-- ... 登录页面的模板内容 ... -->
</template>

<script>
import { ref } from 'vue';
import { loginApi } from '@/api/auth'; // 引入模拟的 loginApi

export default {
  name: 'LoginView',
  data() {
    return {
      // ... 其他 data
      loginForm: {
        username: '',
        password: '',
      },
    };
  },
  methods: {
    async login() {
      try {
        // 首先等待表单的检验，调用 this.$refs.loginForm.validate() 方法
        const isValid = await this.$refs.loginForm.validate();
        if (!isValid) {
          return; // 表单校验失败，不继续执行
        }

        // 调用 API 函数发送登录请求
        const response = await loginApi(this.loginForm);

        // 根据后端返回的结果判断登录是否成功
        if (response.success) {
            this.$router.push('/community');
          // 登录成功，根据实际情况进行跳转或其他操作
          console.log('登录成功');
        } else {
          // 登录失败，根据后端返回的错误信息给出提示
          console.log(response.message);
        }
      } catch (error) {
        // 处理其他错误情况
        console.error('登录过程出现错误', error);
      }
    },
  },
};
</script>
```



**Token（令牌）**是一种身份验证的机制，常用于验证用户身份以及在用户请求服务器时授权访问。在前后端分离的应用中，用户在登录成功后，通常会从后端获取一个 Token，然后在每次请求时携带该 Token，服务器会验证 Token 的有效性，以确定用户是否有权限访问资源。

生成一个简单的随机 Token 可以使用如下代码：

```javascript
function generateRandomToken(length) {
  const characters = 'ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789';
  let token = '';
  for (let i = 0; i < length; i++) {
    const randomIndex = Math.floor(Math.random() * characters.length);
    token += characters[randomIndex];
  }
  return token;
}

// 生成一个长度为 32 的随机 Token
const token = generateRandomToken(32);
console.log('Generated Token:', token);
```

在实际应用中，Token 的生成通常由后端完成，前端只需要将获取到的 Token 存储起来，并在每次请求中将 Token 添加到请求头中（通常是在 `Authorization` 头中）。

在`loginApi` 函数中，可以模拟生成一个 Token 并将其返回给前端，如下所示：

```javascript
export function loginApi(userData){
    return new Promise((resolve) => {
        // 假设这是模拟的异步操作
        setTimeout(() => {
          const generatedToken = generateRandomToken(32); // 随机生成一个 Token
          resolve({ success: true, message: '登录成功', token: generatedToken });
        }, 1000);
      });
}
```

上述代码中的 `token` 字段是模拟生成的 Token，实际应用中，Token 应该由后端生成和管理。





可以在 `stores/modules/user` 中定义一个 store 来存储用户相关的信息，包括 token。以下是一个简单的示例,在 `stores/modules/user.js` 中定义 store：

```javascript
import { defineStore } from 'pinia';

const userStore = defineStore('user', {
  state: () => ({
    token: '',
  }),
  actions: {
    setToken(token) {
      this.token = token;
    },
  },
  persist:true
});

export { userStore };
```

现在，可以在登录逻辑中使用 `userStore` 来存储 token：

```javascript
import { userStore } from '../../stores/modules/user';

// ...

data(){
    return{
              userStoreObj:userStore(),
    }
}

async login() {
  // 登录逻辑 
  const isValid = await this.$refs.loginForm.validate();
  const response = await loginApi(this.loginForm);
  if (response.success) {
    this.userStoreObj.setToken(response.token); // 存储 token
    this.$router.push('/community');
    console.log('登录成功');
  } else {
    console.log('登录失败');
  }
},
```









在 Vue Router 中实现登录拦截可以通过导航守卫来实现。Vue Router 提供了 `beforeEach` 导航守卫，它可以在路由跳转之前进行一些操作，例如判断用户是否已登录。

以下是一个简单的示例，演示如何在 Vue Router 中实现登录拦截：

```javascript
import { createRouter, createWebHistory } from 'vue-router';

const routes = [
  // 其他路由配置...
  {
    path: '/community',
    name: 'Community',
    component: () => import('@/views/CommunityView.vue'),
    meta: { requiresAuth: true } // 添加 meta 属性来标记需要登录验证的路由
  },
  // 更多路由配置...
];

const router = createRouter({
  history: createWebHistory(),
  routes
});

// 添加全局前置守卫
router.beforeEach((to, from, next) => {
  // 判断路由是否需要登录验证
  if (to.meta.requiresAuth) {
    // 模拟判断用户是否已登录，您需要根据实际情况来判断
    const isAuthenticated = checkUserAuthentication(); // 自定义函数，检查用户是否已登录
    if (isAuthenticated) {
      next(); // 用户已登录，继续跳转
    } else {
      next('/login'); // 用户未登录，跳转到登录页面
    }
  } else {
    next(); // 不需要登录验证的路由，直接跳转
  }
});

export default router;
```

在上述代码中，我们使用 `meta` 属性来标记需要登录验证的路由，然后在全局前置守卫中使用 `beforeEach` 判断用户是否已登录。如果用户已登录，允许跳转到目标路由，如果用户未登录，则跳转到登录页面或者其他需要的操作。



**实现 `checkUserAuthentication()` 函数**来判断用户是否已登录。可以使用 `userStore` 来获取持久化存储的 `token`，然后根据 `token` 是否为空来判断用户是否已登录。

```javascript
import { userStore } from '../stores/modules/user';

router.beforeEach((to, from, next) => {
  if (to.meta.requiresAuth) {
    const isAuthenticated = checkUserAuthentication();
    if (isAuthenticated) {
      next(); // 用户已登录，继续跳转
    } else {
      next('/login'); // 用户未登录，跳转到登录页面
    }
  } else {
    next(); // 不需要登录验证的路由，直接跳转
  }
});

function checkUserAuthentication() {
  const userStoreObj=userStore();
  const token = userStoreObj.token;
  return !!token; // 判断 token 是否非空来确定用户是否已登录
}
```

在上面的代码中，`checkUserAuthentication` 函数使用 `userStore.getToken()` 来获取存储的 `token`，然后通过 `!!token` 来判断用户是否已登录，如果 `token` 非空则返回 `true`，表示用户已登录。如果 `token` 为空则返回 `false`，表示用户未登录。



### CommunityLayout.vue

![image-20230818113819068](C:\Users\86157\AppData\Roaming\Typora\typora-user-images\image-20230818113819068.png)

配置额外的路由：

```ts

    path: '/community',
    name: 'CommunityLayout',
    component: () => import('../views/Community/CommunityLayout.vue'),
    children: [
      {
        path: 'profile',
        name: 'UserProfile',
        component: () => import('../views/User/ProfileView.vue'),
      },
      {
        path: 'avatar',
        name: 'UserAvatar',
        component: () => import('../views/User/AvatarView.vue'),
      },
      {
        path: 'password',
        name: 'UserPassword',
        component: () => import('../views/User/PasswordView.vue'),
      },
    ],
        
        
```



**CommunityLayout.vue的基本骨架**

```vue
<template>
  <h1>community</h1>
  <router-view></router-view>
</template>

<script>
export default {

}
</script>

<style>

</style>
```





**实现侧边栏和二级路由**

```vue
<template >
  <el-container class="community-layout">
    <el-aside width="200px">
      <el-menu :default-active="activeLink" class="el-menu-vertical-demo" @select="handleMenuSelect">
        <el-sub-menu index="article">
          <template #title>
            <el-icon><MessageBox /></el-icon>
            <span>文章</span>
          </template>
          <el-menu-item index="articles">文章列表</el-menu-item>
          <el-menu-item index="create-article">发布文章</el-menu-item>
          <el-menu-item index="manage-articles">文章管理</el-menu-item>
        </el-sub-menu>
        <el-sub-menu index="user">
          <template #title>
            <el-icon><User /></el-icon>
            <span>用户</span>
          </template>
          <el-menu-item index="profile">个人信息</el-menu-item>
          <el-menu-item index="avatar">更换头像</el-menu-item>
          <el-menu-item index="password">修改密码</el-menu-item>
        </el-sub-menu>
      </el-menu>
    </el-aside>
    <el-main>
      <router-view></router-view>
    </el-main>
  </el-container>
</template>

<script>
export default {
  name: 'CommunityLayout',
  data() {
    return {
      activeLink: 'articles', // 默认激活的链接
    };
  },
  methods: {
    handleMenuSelect(index) {
      this.activeLink = index;
      this.$router.push(`/community/${index}`);
    },
  },
};
</script>

<style scoped>
.community-layout {
  height: 100vh;
  width: 100vw;
}

.el-aside {
  background-color: #f2f6fc;
  padding-top: 20px;
}

.el-main {
  flex: 1;
  padding: 20px;
}


</style>




```







### 用户信息展示

当获取用户信息的API需要获取用户账号、用户名、邮箱、用户ID以及用户头像图片时，我们可以仿照之前的做法来设计一个假的API，先返回随机生成的用户信息。

**注意图片一律放在public文件夹里面，否则可能出问题**

**获取用户信息的api**

```javascript
export function getUserInfoApi() {
  return new Promise((resolve) => {
    // 假设这是模拟的异步操作
    const userInfo = {
      account: generateRandomString(8),
      username: generateRandomString(10),
      email: generateRandomEmail(),
      userId: generateRandomUserId(),
      avatar: generateRandomAvatarUrl(),
    };

    setTimeout(() => {
      resolve({ success: true, message: '获取用户信息成功', userInfo });
    }, 1000);
  });
}

// 生成随机字符串
function generateRandomString(length) {
  const characters = 'abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ';
  let result = '';
  for (let i = 0; i < length; i++) {
    result += characters.charAt(Math.floor(Math.random() * characters.length));
  }
  return result;
}

// 生成随机邮箱
function generateRandomEmail() {
  return `${generateRandomString(8)}@example.com`;
}

// 生成随机用户ID
function generateRandomUserId() {
  return Math.floor(Math.random() * 100000);
}



// 生成随机头像图片URL
function generateRandomAvatarUrl() {
  const avatarOptions = [
    'public/other_images/hpl.jpg',

    // ...更多头像URL
  ];
  return avatarOptions[Math.floor(Math.random() * avatarOptions.length)];
}
```

**将用户信息存储**

当需要异步获取用户信息并存储到 `userStore` 中时，可以创建一个新的 action 来处理这个异步操作。

```javascript
import { defineStore } from 'pinia';
import { getUserInfoApi } from '../../api/auth'; // 请根据实际路径修改
const userStore=defineStore('user',{
    state:()=>({
        token: '',
        userInfo: null, // 初始化为 null，表示还未获取用户信息
    }),
    actions:{
        setToken(token){
            this.token = token;
        },
        async fetchUserInfo() {
            try {
              const response = await getUserInfoApi(); // 异步获取用户信息
              if (response.success) {
                this.userInfo = response.userInfo; // 存储用户信息
              } else {
                console.error('获取用户信息失败');
              }
            } catch (error) {
              console.error('获取用户信息出错:', error);
            }
          },
    },
    persist:true
})

export { userStore };
```



**定义一个状态栏，靠右放置头像和用户名**

加载好了页面后，去获取用户头像信息，把头像加载在页面上

```vue
    <el-main>
      <div class="status-bar">
        <span>{{ userStoreObj.userInfo.username }}</span>
        <img :src="userStoreObj.userInfo.avatar" class="avatar" />
      </div>
      <router-view></router-view>
    </el-main>

<script>
import { ref, onMounted } from 'vue'; // 引入 onMounted 函数
import { userStore } from '../../stores/modules/user';

export default {
  name: 'CommunityLayout',
  setup() {
    const userStoreObj = userStore();

    // 使用 onMounted 在组件挂载后执行操作
    onMounted(() => {
      console.log('Community已经被加载');
      userStoreObj.fetchUserInfo();
    });
    return {
      userStoreObj,
    };
  },
};
</script>
```





**调整图片的大小**

```vue
<template>
  <div class="community-layout">
    <div class="status-bar">
      <span>{{ userStoreObj.userInfo.username }}</span>
      <img :src="userStoreObj.userInfo.avatar" class="avatar" />
    </div>
    <!-- ...其他内容... -->
    <el-main>
      <router-view></router-view>
    </el-main>
  </div>
</template>

<style scoped>

.status-bar {
  display: flex;
  justify-content: flex-end;
  align-items: center;
  background-color: #f2f6fc;
  padding: 10px;
}

.status-bar span {
  margin-right: 10px;
}

.avatar {
  width: 40px;
  height: 40px;
  border-radius: 50%;
}
</style>
```

在这个示例中，我使用了 `display: flex` 来让状态栏的内容在一行内排列，并使用 `justify-content: flex-end` 将内容靠右对齐。头像的大小和圆角也进行了调整。



**去掉边距**

```css
<style scoped>
*{
  margin: 0;
  padding: 0;
}
<style>
```







**创建用户头像下拉菜单并实现相关的路由导航：**

```vue
<template>
  <!-- ... 其他组件内容 ... -->
  <el-header class="status-bar">
    <span>{{ userStoreObj.userInfo.username }}</span>
    <div class="avatar-dropdown">
      <el-dropdown trigger="hover">
        <span class="el-dropdown-link">
          <img :src="userStoreObj.userInfo.avatar" class="avatar" />
          <el-icon class="el-icon--right"><arrow-down /></el-icon>
        </span>
        <template #dropdown>
          <el-dropdown-menu>
            <el-dropdown-item @click="goToProfile" >个人信息</el-dropdown-item>
            <el-dropdown-item @click="goToAvatar" >更换头像</el-dropdown-item>
            <el-dropdown-item @click="goToPassword" >修改密码</el-dropdown-item>
            <el-dropdown-item @click="logout" >退出</el-dropdown-item>
          </el-dropdown-menu>
        </template>
      </el-dropdown>
    </div>
  </el-header>
  <!-- ... 其他组件内容 ... -->
</template>

<script lang="ts" setup>

// ... 其他导入语句 ...
</script>

<script>
export default {
  // ... 组件的其他配置 ...

  methods: {
    goToProfile() {
      this.$router.push('/community/profile');
    },
    goToAvatar() {
      this.$router.push('/community/avatar');
    },
    goToPassword() {
      this.$router.push('/community/password');
    },
    logout() {
      this.$router.push('/login');
    },
    // ... 其他方法 ...
  },

  // ... 组件的其他配置 ...
};
</script>
```



**实现用户退出**

想要定义一个函数来清空 token 和用户信息，并在用户退出时调用它时，可以像这样在 `userStore` 中添加一个 `clearUser` 的 action。这个 action 可以清空 `token` 和 `userInfo`，然后可以在 `CommunityLayout` 组件的 `logout` 方法中调用这个 action，实现用户的退出功能。

首先，修改 `userStore` 的定义，添加 `clearUser` action：

```javascript

  actions: {
    setToken(token) {
      this.token = token;
    },
    async fetchUserInfo() {
      const response = await getUserInfoApi();
      this.userInfo = response.userInfo;
    },
    clearUser() {
      this.token = '';
      this.userInfo = null;
    },
  },

```

接下来，在 `CommunityLayout` 组件中的 `logout` 方法中调用 `clearUser` action，并进行页面跳转：

```vue

  methods: {
    logout() {
      this.$router.push('/login'); // 跳转到登录页面
      this.userStoreObj.clearUser(); // 清空用户信息和 token
    },

```

这样，在用户点击退出菜单项时，`clearUser` action 会被调用，清空用户信息和 token，然后跳转到登录页面，实现用户的退出功能。



完善三个组件：`ProfileView.vue`、`AvatarView.vue` 和 `PasswordView.vue`，分别实现查看用户信息、预览和上传头像、以及修改密码的功能。

![image-20230819134157861](C:\Users\86157\AppData\Roaming\Typora\typora-user-images\image-20230819134157861.png)

### ProfileView.vue

```vue
<template>
  <div>
    <h1>用户信息</h1>
    <div>
      <img :src="userStoreObj.userInfo.avatar" class="avatar" />
      <p>用户名：{{ userStoreObj.userInfo.username }}</p>
      <p>账号：{{ userStoreObj.userInfo.account }}</p>
      <p>Email：{{ userStoreObj.userInfo.email }}</p>
      <p>用户ID：{{ userStoreObj.userInfo.userId }}</p>
    </div>
  </div>
</template>

<script setup>
import { userStore } from '../../stores/modules/user';
const userStoreObj = userStore();
</script>

<style>
.avatar {
  width: 100px;
  height: 100px;
  border-radius: 50%;
  object-fit: cover;
}
</style>
```



当使用 Element Plus 组件来改进用户基本信息的样式时，可以利用它提供的丰富样式和组件来创建更具吸引力的界面。以下是使用 Element Plus 组件对用户基本信息进行美化：

```vue
<template>
  <div class="user-profile">
    <h1>用户信息</h1>
    <el-card class="user-card">
      <el-row>
        <el-col :span="8" class="avatar-col">
          <img :src="userStoreObj.userInfo.avatar" class="avatar" />
        </el-col>
        <el-col :span="16">
          <el-row class="info-row">
            <el-col :span="6">
              <p class="info-label">用户名：</p>
            </el-col>
            <el-col :span="18">
              <p class="info-value">{{ userStoreObj.userInfo.username }}</p>
            </el-col>
          </el-row>
          <el-row class="info-row">
            <el-col :span="6">
              <p class="info-label">账号：</p>
            </el-col>
            <el-col :span="18">
              <p class="info-value">{{ userStoreObj.userInfo.account }}</p>
            </el-col>
          </el-row>
          <el-row class="info-row">
            <el-col :span="6">
              <p class="info-label">Email：</p>
            </el-col>
            <el-col :span="18">
              <p class="info-value">{{ userStoreObj.userInfo.email }}</p>
            </el-col>
          </el-row>
          <el-row class="info-row">
            <el-col :span="6">
              <p class="info-label">用户ID：</p>
            </el-col>
            <el-col :span="18">
              <p class="info-value">{{ userStoreObj.userInfo.userId }}</p>
            </el-col>
          </el-row>
        </el-col>
      </el-row>
    </el-card>
  </div>
</template>

<script setup>
import { userStore } from '../../stores/modules/user';
const userStoreObj = userStore();
</script>

<style scoped>
.user-profile {
  padding: 20px;
}

.user-card {
  padding: 20px;
}

.avatar-col {
  display: flex;
  justify-content: center;
}

.avatar {
  width: 100px;
  height: 100px;
  border-radius: 50%;
  object-fit: cover;
}

.info-row {
  margin: 10px 0;
}

.info-label {
  font-weight: bold;
}

.info-value {
  margin-left: 10px;
}
</style>
```

在这个示例中，使用了 `el-card` 组件来为用户信息创建一个卡片效果，使用 `el-row` 和 `el-col` 组件来进行栅格布局。还使用了不同的样式类来定义标题、标签和值的样式。





### AvatarView.vue

![image-20230819153757721](C:\Users\86157\AppData\Roaming\Typora\typora-user-images\image-20230819153757721.png)

```vue
<template>
  <div>
    <h1>预览头像</h1>
    <img :src="previewAvatar" class="avatar" />
    <input type="file" @change="handleFileChange" accept="image/*" />
    <button @click="uploadAvatar">上传头像</button>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import { userStore } from '../../stores/modules/user';

const userStoreObj = userStore();
const previewAvatar = ref(userStoreObj.userInfo.avatar);

const handleFileChange = (event) => {
  const file = event.target.files[0];
  if (file) {
    const reader = new FileReader();
    reader.onload = () => {
      previewAvatar.value = reader.result;
    };
    reader.readAsDataURL(file);
  }
};

const uploadAvatar = () => {
  // 发送上传头像的请求，更新用户头像
  // 更新 userStoreObj.userInfo.avatar
};
</script>

<style>
.avatar {
  width: 100px;
  height: 100px;
  border-radius: 50%;
  object-fit: cover;
}
</style>
```



当上传用户头像时，可以按照以下方式补全 `uploadAvatar` 函数：

```javascript
import { changeAvatarApi } from '../../api/auth';
import { userStore } from '../../stores/modules/user';

const uploadAvatar = async () => {
  try {
    // 调用 changeAvatarApi 上传新头像
    const response = await changeAvatarApi(previewAvatar);

    if (response.success) {
      // 更新 userStoreObj.userInfo.avatar 为新头像
      userStoreObj.userInfo.avatar = response.newAvatarUrl;
    } else {
      // 处理上传失败的情况，显示错误信息等
    }
  } catch (error) {
    // 处理可能的异常，比如网络错误等
    console.error('上传头像失败:', error);
  }
};
```

在这个代码中，我们首先导入 `changeAvatarApi` 函数和 `userStore` 对象，然后在 `uploadAvatar` 函数中使用 `await` 来调用 `changeAvatarApi`，并等待它返回结果。如果上传成功（`response.success` 为 `true`），我们更新 `userStoreObj.userInfo.avatar` 为新头像的 URL。

上述代码中的 `response.newAvatarUrl` 是一个假设的属性，需要根据实际的 API 响应数据来获取新头像的 URL。



模拟头像传给后端，后端更改头像，发回头像链接

```js
export function changeAvatarApi(newAvatarDataURL){
  return new Promise((resolve)=>{
    setTimeout(() => {
      resolve({ success: true, message: '更改头像信息成功',newAvatarUrl: newAvatarDataURL });
    }, 1000);
  })
}
```

为了简化，把原头像返回



**美化样式**

```vue
<template>
  <div class="avatar-upload-container">
    <h1 class="upload-title">预览头像</h1>
    <img :src="previewAvatar" class="avatar" />
    <div class="upload-controls">
      <label for="file-input" class="file-label">
        选择文件
        <input id="file-input" type="file" accept="image/*" @change="handleFileChange" class="file-input">
      </label>
      <button @click="uploadAvatar" class="upload-button">上传头像</button>
    </div>
  </div>
</template>



<style scoped>
.avatar-upload-container {
  text-align: center;
  padding: 20px;
}

.upload-title {
  font-size: 24px;
  margin-bottom: 20px;
}

.avatar {
  width: 150px;
  height: 150px;
  border-radius: 50%;
  object-fit: cover;
  margin-bottom: 20px;
}

.upload-controls {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-top: 20px;
}

.file-label {
  background-color: #3498db;
  color: white;
  border: none;
  padding: 10px 20px;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s;
  margin-bottom: 10px;
}

.file-label:hover {
  background-color: #2980b9;
}

.file-input {
  display: none;
}

.upload-button {
  background-color: green;
  color: white;
  border: none;
  padding: 10px 20px;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s;
}

.upload-button:hover {
  background-color: green;
}
</style>
```





### PasswordView.vue

![image-20230821123805735](C:\Users\86157\AppData\Roaming\Typora\typora-user-images\image-20230821123805735.png)

```vue
<template>
  <div>
    <h1>修改密码</h1>
    <input type="password" v-model="oldPassword" placeholder="旧密码" />
    <input type="password" v-model="newPassword" placeholder="新密码" />
    <button @click="changePassword">确认修改</button>
    <p>{{ message }}</p>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import { changePasswordApi } from '../../api/auth';
import { userStore } from '../../stores/modules/user';

const oldPassword = ref('');
const newPassword = ref('');
const message = ref('');
const userStoreObj = userStore();

const changePassword = async () => {
  const response = await changePasswordApi(userStoreObj.userInfo.account,oldPassword.value, newPassword.value);
  if (response.success) {
    message.value = '密码修改成功！';

  } else {
    message.value = '密码修改失败，请重试。';
  }
};
</script>
```

模拟向后端发送更换密码请求

```ts
export function changePasswordApi(account,oldPassword,newPassword){
  return new Promise((resolve)=>{
    setTimeout(() => {
      resolve({ success: true, message: '更改密码成功' });
    }, 1000);
  })
}
```



美化样式

```vue
<template>
  <div class="password-view-container">
    <h1 class="password-title">修改密码</h1>
    <el-input
      v-model="oldPassword"
      type="password"
      placeholder="旧密码"
      class="password-input"
    />
    <el-input
      v-model="newPassword"
      type="password"
      placeholder="新密码"
      class="password-input"
    />
    <el-button @click="changePassword" type="primary" class="password-button">
      确认修改
    </el-button>
    <p class="password-message">{{ message }}</p>
  </div>
</template>


<style scoped>
.password-view-container {
  text-align: center;
  padding: 20px;
}

.password-title {
  font-size: 24px;
  margin-bottom: 20px;
}

.password-input {
  width: 100%;
  margin-bottom: 15px;
}

.password-button {
  width: 100%;
}

.password-message {
  margin-top: 20px;
  color: #e74c3c;
}
</style>
```





### ArticleListView.vue

![image-20230821123739154](C:\Users\86157\AppData\Roaming\Typora\typora-user-images\image-20230821123739154.png)

```vue
<template>
  <div class="recommendedArticles-list">
    <div v-for="article in recommendedArticles" :key="article.id" class="article">
      <h2 class="title" @click="goToArticle(article.id)">{{ article.title }}</h2>
      <div class="info">
        <p class="author">{{ article.author }}</p>
        <p class="time">{{ article.publishTime }}</p>
      </div>
      <p class="summary">{{ article.summary }}</p>
      <div class="stats">
        <p class="likes">{{ article.likes }} Likes</p>
        <p class="views">{{ article.views }} Views</p>
      </div>
    </div>
  </div>
</template>


<script>
import { getRecommendedArticleApi } from '../../../api/user';
export default {
  data() {
    return {
      recommendedArticles: [],
    };
  },
  async mounted() {
    try {
      const response = await getRecommendedArticleApi();
      if(response.success){
        console.log(response.recommendedArticles)
        this.recommendedArticles=response.recommendedArticles
      }
    } catch (error) {
      console.error('Error fetching recommended articles:', error);
    }
  },
  methods: {
    goToArticle(articleId) {
      this.$router.push(`/community/articles/${articleId}`);
    },
  },
};
</script>


```

**获取推荐给用户的文章**

```ts

export function getRecommendedArticleApi() {
    return new Promise((resolve)=>{
        const recommendedArticles = [
            {
              id: 1,
              title: '学习HTML的心得',
              author: '张三',
              publishTime: '2023-08-01',
              summary: '在学习HTML的过程中，我掌握了如何创建网页的结构和内容，控制文本格式、图片、链接等元素，以及创建表格和表单。通过HTML，我能够搭建出网页的骨架，将信息有条理地展示给用户',
              likes: Math.floor(Math.random() * 100),
              views: Math.floor(Math.random() * 1000),
            },
            {
              id: 2,
              title: '学习CSS的心得',
              author: '李四',
              publishTime: '2023-08-02',
              summary: '通过学习CSS，我学会了如何为网页添加样式和布局，控制元素的颜色、字体、边框等外观，实现响应式布局和页面排版。CSS让我能够将普通的网页变得更加美观和吸引人。',
              likes: Math.floor(Math.random() * 100),
              views: Math.floor(Math.random() * 1000),
            },
            {
              id: 3,
              title: '学习JS的心得',
              author: '王五',
              publishTime: '2023-08-03',
              summary: '深入学习JavaScript后，我能够为网页添加交互功能，实现用户与页面的互动。我掌握了变量、函数、条件语句等基本概念，也了解了事件处理、DOM操作等高级特性，使得网页更具动态性和实用性。',
              likes: Math.floor(Math.random() * 100),
              views: Math.floor(Math.random() * 1000),
            },
            {
              id: 4,
              title: '学习Ajax的心得',
              author: '赵六',
              publishTime: '2023-08-04',
              summary: '掌握了Ajax技术后，我可以实现页面的异步加载，通过与服务器进行数据交换，实现无需刷新页面即可更新内容的效果。这让用户能够更流畅地与网页进行交互，提升了用户体验。',
              likes: Math.floor(Math.random() * 100),
              views: Math.floor(Math.random() * 1000),
            },
            {
              id: 5,
              title: '学习Vue的心得',
              author: '刘七',
              publishTime: '2023-08-05',
              summary: 'Vue框架的学习让我能够构建更复杂的交互式前端应用，实现组件化开发和数据驱动视图。我可以轻松地创建可复用的组件，实现页面的模块化，同时通过Vue的响应式机制，让数据和视图保持同步，提高开发效率。',
              likes: Math.floor(Math.random() * 100),
              views: Math.floor(Math.random() * 1000),
            },
          ];
        setTimeout(() => {
            console.log('获取推荐文章成功')
            resolve({ success: true, message: '获取用户推荐文章成功',recommendedArticles:recommendedArticles });
        }, 1000);
    })
}
```







**美化样式**

```vue
<template>
  <div class="recommended-articles-list">
    <el-card v-for="article in recommendedArticles" :key="article.id" class="article-card"  @click="goToArticle(article.id)">
      <h2 class="title" >{{ article.title }}</h2>
      <div class="info">
        <p class="author">{{ article.author }}</p>
        <p class="time">{{ article.publishTime }}</p>
      </div>
      <p  class="summary">{{ article.summary }}</p>
      <div class="stats">
        <p class="likes">{{ article.likes }} Likes</p>
        <p class="views">{{ article.views }} Views</p>
      </div>
    </el-card>
  </div>
</template>
  
<script>
import { getRecommendedArticleApi } from '../../../api/user';
export default {
  name: 'ArticleListView',
  data() {
    return {
      recommendedArticles: [],
    }
  },
  async mounted(){
    const response = await getRecommendedArticleApi();
    this.recommendedArticles=response.recommendedArticles;
  },
  methods:{
      goToArticle(articleId){
        this.$router.push(`/community/articles/${articleId}`);
      }
  }
}
</script>


<style scoped>
  .recommended-articles-list {
    display: flex;
    flex-wrap: wrap;
    gap: 20px;
  }

  .article-card {
  width: calc(50% - 10px);
  cursor: pointer;
  }

  .title {
  font-size: 20px;
  color: #333;
  }

  .info {
  display: flex;
  justify-content: space-between;
  margin-top: 5px;
  color: #888;
  }

  .summary {
  margin-top: 10px;
  color: #555;
  }

  .stats {
  display: flex;
  justify-content: space-between;
  margin-top: 10px;
  color: #888;
  }
</style>
```



**跳转文章后知道文章编号**

```vue

<template>
  <div>
    <h1>Article Detail</h1>
    <p>Article ID: {{ $route.params.id }}</p>
    <!-- 其他组件内容 -->
  </div>
</template>
```



