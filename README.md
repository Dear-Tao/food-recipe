# 今天吃什么？- 美食菜谱推荐应用

一个基于 Vue 3 + Vite 开发的美食菜谱推荐应用，帮助用户随机选择今天想吃的菜品，并提供详细的烹饪步骤指导。

## 功能特点

- 支持多个中国传统菜系（川菜、粤菜、苏菜、鲁菜）
- 随机推荐功能，帮助解决"今天吃什么"的困扰
- 精美的卡片式界面设计
- 菜品详细信息展示，包括描述和制作步骤
- 流畅的翻转动画效果

## 技术栈

- Vue 3 - 渐进式 JavaScript 框架
- Vite - 下一代前端构建工具
- Vue SFC (Single File Components) - 单文件组件
- CSS3 动画和过渡效果

## 快速开始

### 环境要求

- Node.js >= 14.0.0
- npm >= 6.0.0

### 安装依赖

```bash
npm install
```

### 开发模式

```bash
npm run dev
```

启动后访问 http://localhost:3000

### 构建生产版本

```bash
npm run build
```

## 项目结构

```
├── src/                # 源代码目录
│   ├── assets/        # 静态资源
│   ├── components/    # 组件
│   ├── App.vue        # 根组件
│   └── main.js        # 入口文件
├── public/            # 公共资源
├── index.html         # HTML 模板
└── vite.config.js     # Vite 配置文件
```

## 贡献指南

1. Fork 本仓库
2. 创建你的特性分支 (git checkout -b feature/AmazingFeature)
3. 提交你的改动 (git commit -m 'Add some AmazingFeature')
4. 推送到分支 (git push origin feature/AmazingFeature)
5. 开启一个 Pull Request

## 开源协议

本项目基于 MIT 协议开源。
