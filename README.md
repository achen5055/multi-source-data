# 多源数据整合系统项目介绍

## 项目概述

多源数据整合系统是一个用于整合多种数据源的Web应用程序。该系统允许用户从不同的数据源（如CSV文件、数据库、API等）导入数据，并进行统一管理和分析。

## 技术架构

### 后端技术栈

- **FastAPI**: 现代、快速（高性能）的Web框架，用于构建API
- **SQLite**: 轻量级关系型数据库，用于存储数据源和记录信息
- **SQLAlchemy**: Python的ORM工具，用于数据库操作
- **Pydantic**: 数据验证和设置管理库

### 前端技术栈

- **Vue 3**: 渐进式JavaScript框架，用于构建用户界面
- **Vite**: 快速的构建工具，提供热重载功能
- **Vue Router**: 官方路由管理器

## 功能特性

### 1. 数据源管理

- 支持多种数据源类型：CSV文件、数据库、API接口
- 可视化管理数据源（添加、删除、查看）
- 数据源连接测试功能

### 2. 数据导入

- 分步向导式导入流程
- CSV文件上传与解析
- 数据库连接与数据预览
- API接口数据获取
- 数据去重机制

### 3. 数据记录管理

- 查看所有导入的数据记录
- 按数据源筛选记录
- 数据记录详情查看

### 4. 数据可视化

- 数据源分布图表展示
- 实时统计数据展示

## 目录结构

```
multi-source-data/
├── backend/                 # 后端服务
│   ├── database.py         # 数据库连接和操作
│   ├── main.py             # 应用入口文件
│   ├── models.py           # 数据模型定义
│   ├── routers.py          # API路由定义
│   ├── schemas.py          # 数据结构定义
│   └── env/                # Python虚拟环境
└── frontend/               # 前端应用
    └── multi-source-frontend/
        ├── src/            # 源代码目录
        │   ├── components/ # Vue组件
        │   ├── views/      # 页面视图
        │   ├── router/     # 路由配置
        │   └── assets/     # 静态资源
        ├── package.json    # 项目依赖配置
        └── vite.config.js  # 构建配置
```

## 后端API接口

### 数据源相关接口

- `GET /api/v1/data-sources/` - 获取数据源列表
- `POST /api/v1/data-sources/` - 创建新的数据源
- `GET /api/v1/data-sources/{source_id}` - 获取特定数据源
- `PUT /api/v1/data-sources/{source_id}` - 更新数据源
- `DELETE /api/v1/data-sources/{source_id}` - 删除数据源

### 数据记录相关接口

- `GET /api/v1/data-records/` - 获取数据记录列表
- `POST /api/v1/data-records/` - 创建新的数据记录
- `GET /api/v1/data-records/{record_id}` - 获取特定数据记录
- `PUT /api/v1/data-records/{record_id}` - 更新数据记录
- `DELETE /api/v1/data-records/{record_id}` - 删除数据记录

### 数据导入相关接口

- `POST /api/v1/test-database-connection` - 测试数据库连接
- `POST /api/v1/database-preview` - 预览数据库数据
- `POST /api/v1/import-data` - 导入数据

## 部署和运行

### 后端服务启动

1. 进入backend目录
2. 激活Python虚拟环境
3. 安装依赖包
4. 使用uvicorn启动服务

### 前端应用启动

1. 进入frontend/multi-source-frontend目录
2. 安装npm依赖
3. 使用npm run dev启动开发服务器

## 数据模型

### DataSource（数据源）

- id: 主键
- name: 数据源名称
- type: 数据源类型（CSV, JSON, Database, API）
- connection_string: 连接字符串
- created_at: 创建时间
- updated_at: 更新时间

### DataRecord（数据记录）

- id: 主键
- source_id: 关联的数据源ID
- content: 原始数据内容
- structured_data: 结构化数据（JSON格式）
- hash_value: 内容哈希值（用于去重）
- created_at: 创建时间
- updated_at: 更新时间
