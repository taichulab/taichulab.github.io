# 太初元启 - Taichu Lab 官方网站

![Nuxt.js](https://img.shields.io/badge/Nuxt.js-00DC82?style=for-the-badge&logo=nuxt.js&logoColor=white)
![Vue.js](https://img.shields.io/badge/Vue.js-35495E?style=for-the-badge&logo=vue.js&logoColor=4FC08D)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-38B2AC?style=for-the-badge&logo=tailwind-css&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=white)

## 📖 项目简介

太初元启（Taichu Lab）官方网站，一个专注于前沿科技研究和技术创新的现代化企业官网。项目采用现代化的技术栈构建，提供流畅的用户体验和响应式设计。

## ✨ 主要特性

- 🚀 **现代化技术栈**：基于 Nuxt.js 3 + Vue.js 3 + TypeScript
- 🎨 **精美UI设计**：采用 Tailwind CSS + 自定义未来主义风格
- 🌍 **多语言支持**：完整的中英文国际化支持
- 📱 **响应式设计**：完美适配桌面端和移动端
- ⚡ **高性能**：优化的构建配置和资源加载
- 🔍 **SEO友好**：支持静态站点生成（SSG）

## 🛠️ 技术栈

- **框架**: Nuxt.js 3
- **前端**: Vue.js 3 + TypeScript
- **样式**: Tailwind CSS 4.0
- **UI组件**: useBootstrap
- **图标**: Iconify
- **国际化**: @nuxtjs/i18n
- **构建工具**: Vite

## 📦 项目结构

```
taichulab-web/
├── pages/           # 页面组件
│   ├── index.vue    # 首页
│   ├── research.vue # 研究领域
│   ├── solutions.vue # 解决方案
│   ├── tech-innovation.vue # 技术创新
│   └── social-experiment.vue # 社会实验
├── layouts/         # 布局组件
│   └── default.vue  # 默认布局
├── i18n/           # 国际化配置
│   └── locales/
│       ├── en.json  # 英文翻译
│       └── zh.json  # 中文翻译
├── public/         # 静态资源
│   ├── css/
│   │   └── global.css # 全局样式
│   └── imgs/       # 图片资源
├── app.vue         # 应用入口
└── nuxt.config.ts  # Nuxt配置
```

## 🚀 快速开始

### 环境要求

- Node.js 18+ 
- npm 或 yarn

### 安装依赖

```bash
# 使用 npm
npm install

# 或使用 yarn
yarn install
```

### 开发模式

启动本地开发服务器：

```bash
# 使用 npm
npm run dev

# 或使用 yarn
yarn dev
```

开发服务器将在 http://localhost:3000 启动，支持热重载。

### 构建项目

#### 1. 开发构建（SPA模式）

```bash
# 构建用于开发环境的SPA应用
npm run build
```

#### 2. 静态站点生成（SSG模式）

```bash
# 生成静态HTML文件，适合部署到静态服务器
npm run generate
```

构建完成后，静态文件将生成在 `.output/public` 目录中。

### 预览构建结果

```bash
# 预览构建后的应用
npm run preview
```

## 📋 部署说明

### 部署到 Nginx 静态服务器

1. **构建静态文件**：
   ```bash
   npm run generate
   ```

2. **配置 Nginx**：
   ```nginx
   server {
       listen 80;
       server_name your-domain.com;
       
       root /path/to/your/project/.output/public;
       index index.html;
       
       # SPA路由支持
       location / {
           try_files $uri $uri/ /index.html;
       }
       
       # 静态资源缓存
       location ~* \.(js|css|png|jpg|jpeg|gif|ico|svg)$ {
           expires 1y;
           add_header Cache-Control "public, immutable";
       }
   }
   ```

3. **复制文件到服务器**：
   ```bash
   sudo cp -r .output/public/* /var/www/html/
   ```

4. **重启 Nginx**：
   ```bash
   sudo systemctl reload nginx
   ```

### 部署到其他平台

- **Vercel**: 直接连接Git仓库，自动部署
- **Netlify**: 拖拽 `.output/public` 文件夹到部署区域
- **GitHub Pages**: 使用 GitHub Actions 自动部署

## 🔧 配置说明

### 渲染模式配置

项目默认配置为 SPA 模式（`ssr: false`），如需启用服务端渲染或静态站点生成，可修改 `nuxt.config.ts`：

```typescript
// 启用SSR（服务端渲染）
ssr: true,

// 或保持SSR启用，使用 nuxt generate 进行静态生成
```

### 多语言配置

多语言配置位于 `i18n/locales/` 目录，支持中英文切换。

## 📝 开发指南

### 添加新页面

1. 在 `pages/` 目录下创建新的 `.vue` 文件
2. 文件路径将自动映射为路由路径
3. 在导航组件中添加对应的路由链接

### 样式开发

- 使用 Tailwind CSS 工具类
- 自定义样式请添加到 `public/css/global.css`
- 组件级样式使用 `<style scoped>`

### 国际化开发

```vue
<template>
  <h1>{{ $t('page.title') }}</h1>
</template>

<script setup>
// 在脚本中使用
const title = useI18n().t('page.title')
</script>
```

## 🐛 故障排除

### 常见问题

1. **依赖安装失败**：确保 Node.js 版本符合要求，清除 node_modules 后重新安装
2. **构建错误**：检查 TypeScript 类型错误，确保所有导入路径正确
3. **路由问题**：确保页面文件位于正确的 pages 目录下

### 调试工具

项目已启用 Nuxt DevTools，在开发模式下可通过浏览器开发者工具访问。

## 🤝 贡献指南

欢迎提交 Issue 和 Pull Request 来改进项目。

## 📄 许可证

本项目采用 MIT 许可证。

---

**太初元启 - 启迪未来智能** 🌟