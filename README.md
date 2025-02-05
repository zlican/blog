# Blog 项目

这是一个基于 Vue.js 和 Go 的全栈博客项目。前端使用 Vue.js 框架，后端使用 Go 语言和 Gin 框架。项目包含了博客文章的创建、管理、展示等功能。

## 项目结构

```
blog/
├── blog-frontend/          # 前端项目目录
│   ├── public/             # 公共资源目录
│   ├── src/                # 源代码目录
│   │   ├── assets/         # 静态资源，如图片、样式等
│   │   ├── components/     # Vue 组件
│   │   ├── composables/    # 可复用的组合式 API
│   │   ├── router/         # 路由配置
│   │   ├── store/          # Vuex 状态管理
│   │   ├── views/          # 页面视图组件
│   │   ├── App.vue         # 根组件
│   │   ├── main.js         # 入口文件
│   ├── package.json        # 项目依赖配置文件
│   ├── vite.config.js      # Vite 配置文件
│   └── ...                 # 其他配置文件
│
├── blog-backend/           # 后端项目目录
│   ├── controller/         # 控制器，处理请求逻辑
│   ├── model/              # 数据模型
│   ├── router/             # 路由配置
│   ├── service/            # 服务层，业务逻辑
│   ├── utils/              # 工具类
│   ├── main.go             # 入口文件
│   ├── go.mod              # Go 模块依赖文件
│   └── ...                 # 其他配置文件
│
└── README.md               # 项目说明文件
```

## 功能

- 用户注册和登录
- 博客文章的创建、编辑和删除
- 博客文章的展示和详情查看
- 标签管理
- 留言管理
- 管理员入口

## 前端项目

前端项目位于 `blog-frontend` 目录下，使用 Vue.js 构建。

### 安装依赖

```bash
cd blog-frontend
npm install
```

### 运行前端项目

```bash
npm run serve
```

前端项目将运行在 `http://localhost:5173`。

## 后端项目

后端项目位于 `blog-backend` 目录下，使用 Go 和 Gin 框架构建。

### 安装依赖

确保你已经安装了 Go 语言环境，然后运行以下命令安装依赖：

```bash
cd blog-backend
go mod tidy
```

### 运行后端项目

```bash
go run main.go
```

后端项目将运行在 `http://localhost:8000`。

## 配置

### Redis 配置

后端项目使用 Redis 作为 session 存储。你需要在本地安装并运行 Redis 服务器，默认连接地址为 `localhost:6379`。

### CORS 配置

后端项目配置了 CORS，允许来自 `http://localhost:5173` 的请求。如果你在生产环境中运行项目，请将 `config.AllowOrigins` 修改为你的前端项目地址。

## 运行项目

1. 启动 Redis 服务器。
2. 启动后端项目：
   ```bash
   cd blog-backend
   go run main.go
   ```
3. 启动前端项目：
   ```bash
   cd blog-frontend
   npm run serve
   ```

现在，你可以在浏览器中访问 `http://localhost:5173` 查看博客项目。

## 许可证

该项目使用 MIT 许可证，详情请参阅 [LICENSE](LICENSE) 文件。
