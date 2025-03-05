# Blog 博客秒杀系统
将博客系统和抽奖秒杀功能相结合的分布式应用。

### 技术栈

前端：Vue3

后端：Go + Gin + Gorm

数据库：MySQL + Redis

中间件：Kafka

微服务通信：gRPC

### 核心功能模块

博客系统

用户认证：采用 JWT 实现安全的身份验证

文章管理：支持 Markdown 格式的文章编辑

评论互动：实现用户间的互动交流

分布式搜索：自研搜索引擎，支持文章快速检索

抽奖秒杀系统

大转盘抽奖：前端使用 lucky-canvas 实现流畅的抽奖动画

库存管理：Redis 预热数据，实现高性能库存控制

限流保护：令牌桶算法防止系统被恶意请求击垮

异步处理：Kafka 消息队列处理订单生成和库存扣减

### 项目亮点

高并发架构设计

采用微服务架构，将博客和抽奖系统解耦

Redis 缓存热点数据，减轻数据库压力

goroutine 和 channel 实现并发控制

gRPC 实现服务间高效通信

数据一致性保障

分布式锁确保库存操作原子性

最终一致性方案处理分布式事务

Redis + MySQL 双写一致性方案

### 项目难点及解决方案

秒杀系统的并发控制

难点：大量用户同时抽奖导致系统压力剧增

解决方案：

Redis 预热库存数据

令牌桶限流

goroutine 池化复用

多级缓存架构

分布式事务处理

难点：跨服务操作的数据一致性保证

解决方案：

采用最终一致性方案

引入消息队列作为补偿机制

定时任务检查数据一致性

系统可用性保障

难点：高并发下的系统稳定性

解决方案：

服务熔断降级

请求限流保护

多级缓存策略

异步处理解耦



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
