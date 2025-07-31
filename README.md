# marsshort
火星短剧
# 短剧娱乐平台 - 多内容类型娱乐平台

## 🎬 项目简介

这是一个综合性娱乐平台，支持**短剧、小说、漫画、听书**四种主要内容类型。项目采用前后端分离架构，Flutter移动端 + Spring Boot微服务后端 + 管理后台的完整解决方案。

## 项目架构

### 技术栈
- **后端**: Spring Boot + Spring Cloud Gateway + MySQL + Redis + RabbitMQ + MinIO + Elasticsearch
- **前端**: Vue 3 + TypeScript + Ant Design Vue (管理后台)
- **移动端**: Flutter + GetX (客户端应用)
- **部署**: Docker + Docker Compose + Nginx

### 系统架构图
```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   Flutter App   │    │   Vue3 Admin    │    │   Mobile Web    │
│    (移动端)      │    │   (管理后台)     │    │   (Web端)       │
└─────────────────┘    └─────────────────┘    └─────────────────┘
         │                       │                       │
         └───────────────────────┼───────────────────────┘
                                 │
                    ┌─────────────────┐
                    │      Nginx      │
                    │   (反向代理)     │
                    └─────────────────┘
                                 │
                    ┌─────────────────┐
                    │  API Gateway    │
                    │   (Spring CLoud) │
                    └─────────────────┘
                                 │
         ┌───────────────────────┼───────────────────────┐
         │                       │                       │
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│  User Service   │    │ Content Service │    │ Payment Service │
│   (用户服务)     │    │   (内容服务)     │    │   (支付服务)     │
└─────────────────┘    └─────────────────┘    └─────────────────┘
         │                       │                       │
         │              ┌─────────────────┐              │
         │              │Notification Svc │              │
         │              │   (通知服务)     │              │
         │              └─────────────────┘              │
         │                       │                       │
         └───────────────────────┼───────────────────────┘
                                 │
    ┌─────────────────────────────────────────────────────────┐
    │                    基础设施层                            │
    │  MySQL  │  Redis  │ RabbitMQ │  MinIO  │ Elasticsearch  │
    └─────────────────────────────────────────────────────────┘
```

## 效果预览
![](2.png)
![](3.png)
![](4.png)
![](5.png)
![](6.png)
![](7.png)
![](8.png)
## 功能模块

### 用户端功能
- ✅ 用户注册/登录/找回密码
- ✅ 个人资料管理
- ✅ 视频播放/点赞/评论/分享
- ✅ 关注/粉丝系统
- ✅ 钻石充值/消费
- ✅ 观看历史记录
- ✅ 推送通知

### 管理端功能
- ✅ 用户管理和权限控制
- ✅ 内容审核和管理
- ✅ 财务数据统计
- ✅ 系统配置管理
- ✅ 数据分析报表
- ✅ 日志监控

### 核心业务
- ✅ 剧集/视频管理
- ✅ 分类标签系统
- ✅ 评论互动系统
- ✅ 钻石经济系统
- ✅ VIP会员系统
- ✅ 搜索推荐系统

## 快速开始

### 环境要求
- Docker >= 20.0
- Docker Compose >= 2.0
- Git
- Node.js >= 16 (开发环境)
- Flutter SDK >= 3.0 (开发环境)
- Java 17+ (开发环境)

### 一键部署
```bash
# 克隆项目
git clone <repository-url>
cd shortVideo

# 执行部署脚本
./scripts/deploy.sh install
```

### 手动部署

1. **启动基础服务**
```bash
docker-compose up -d mysql redis rabbitmq minio elasticsearch
```

2. **构建应用服务**
```bash
# 构建后端服务
./scripts/deploy.sh build_backend

# 构建前端应用
./scripts/deploy.sh build_frontend
```

3. **启动所有服务**
```bash
docker-compose up -d
```

4. **初始化数据**
```bash
# 执行数据库初始化
docker-compose exec mysql mysql -uroot -proot123456 < scripts/init.sql
```

## 访问地址

### 前端应用
- 🌐 **移动端应用**: https://localhost/app
- 🛠️ **管理后台**: https://localhost/admin
- 📖 **API文档**: https://localhost/api/swagger-ui

### 管理界面
- 📦 **MinIO控制台**: http://localhost:9001
- 🐰 **RabbitMQ管理**: http://localhost:15672
- 🔍 **Elasticsearch**: http://localhost:9200

### 默认账号

#### 管理后台
| 角色 | 用户名 | 密码 | 权限 |
|------|--------|------|------|
| 超级管理员 | admin | admin123 | 全部权限 |
| 内容管理员 | content | content123 | 内容管理 |
| 财务管理员 | finance | finance123 | 财务管理 |

#### 基础服务
| 服务 | 用户名 | 密码 |
|------|--------|------|
| MySQL | root | root123456 |
| Redis | - | redis123456 |
| MinIO | minioadmin | minioadmin123 |
| RabbitMQ | admin | admin123456 |

## 开发指南

### 后端开发

#### 项目结构
```
backend/
├── api-gateway/          # API网关
├── user-service/         # 用户服务
├── content-service/      # 内容服务
├── payment-service/      # 支付服务
└── notification-service/ # 通知服务
```

#### 本地开发
```bash
# 启动基础服务
docker-compose up -d mysql redis rabbitmq

# 启动微服务（在各服务目录下）
./mvnw spring-boot:run
```

### 前端开发

#### 管理后台
```bash
cd admin
npm install
npm run dev      # 开发环境
npm run build    # 生产构建
```

#### Flutter应用
```bash
cd flutter
flutter pub get
flutter run      # 开发运行
flutter build web # Web构建
```

## 部署运维

### 常用命令
```bash
# 查看服务状态
./scripts/deploy.sh status

# 查看日志
./scripts/deploy.sh logs [service-name]

# 备份数据
./scripts/deploy.sh backup

# 恢复数据
./scripts/deploy.sh restore backup.tar.gz

# 更新服务
./scripts/deploy.sh update

# 重启服务
./scripts/deploy.sh restart

# 停止服务
./scripts/deploy.sh stop

# 清理数据
./scripts/deploy.sh cleanup
```

### 监控告警
项目集成了以下监控功能：
- Spring Boot Actuator 健康检查
- 应用性能指标收集
- 错误日志聚合
- 系统资源监控

### 性能优化

#### 数据库优化
- 使用连接池优化数据库连接
- 合理设计索引提升查询性能
- 读写分离支持高并发
- 定期清理历史数据

#### 缓存策略
- Redis缓存热点数据
- CDN加速静态资源
- 浏览器缓存优化
- 数据库查询缓存

#### 服务优化
- 微服务水平扩展
- 负载均衡分发请求
- 异步消息处理
- 限流熔断保护

## API文档

### 用户相关接口
- `POST /api/auth/login` - 用户登录
- `POST /api/auth/register` - 用户注册
- `GET /api/user/profile` - 获取用户信息
- `PUT /api/user/profile` - 更新用户信息

### 内容相关接口
- `GET /api/videos` - 获取视频列表
- `GET /api/videos/{id}` - 获取视频详情
- `POST /api/videos/{id}/like` - 点赞视频
- `POST /api/videos/{id}/comments` - 添加评论

### 支付相关接口
- `GET /api/diamonds/packages` - 获取钻石套餐
- `POST /api/orders` - 创建订单
- `GET /api/orders/{id}` - 查询订单状态

更多API详情请查看在线文档：https://localhost/api/swagger-ui

## 数据库设计

### 核心表结构
- `users` - 用户表
- `dramas` - 剧集表
- `videos` - 视频表
- `categories` - 分类表
- `comments` - 评论表
- `likes` - 点赞表
- `orders` - 订单表
- `diamond_packages` - 钻石套餐表

详细的数据库设计请参考 `scripts/init.sql`

## 安全配置

### 数据安全
- JWT Token认证
- 密码BCrypt加密
- SQL注入防护
- XSS攻击防护
- CSRF保护

### 网络安全
- HTTPS强制跳转
- 安全头配置
- 限流防刷
- IP白名单

## 常见问题

### Q: 服务启动失败怎么办？
A: 
1. 检查Docker是否正常运行
2. 查看服务日志定位问题
3. 确认端口是否被占用
4. 检查配置文件是否正确

### Q: 数据库连接失败？
A:
1. 确认MySQL服务正常启动
2. 检查数据库连接配置
3. 验证用户名密码正确性
4. 确认网络连通性

### Q: 前端页面无法访问？
A:
1. 检查Nginx服务状态
2. 验证前端构建是否成功
3. 确认域名解析配置
4. 查看浏览器控制台错误

## 贡献指南

1. Fork 本仓库
2. 创建特性分支 (`git checkout -b feature/AmazingFeature`)
3. 提交改动 (`git commit -m 'Add some AmazingFeature'`)
4. 推送分支 (`git push origin feature/AmazingFeature`)
5. 创建 Pull Request

## 许可证

本项目采用 MIT 许可证 - 查看 [LICENSE](LICENSE) 文件了解详情

## 联系方式

- 项目地址: https://github.com/your-repo/shortvideo
- 问题反馈: https://github.com/your-repo/shortvideo/issues
- 技术文档: https://docs.shortvideo.com

---

**感谢使用短剧平台！** 🎬
