# 我的Next.js学习项目

> 这是一个用于学习Next.js的项目，基于Next.js 15.3.3构建。

## 🚀 项目概述

这个项目是我学习Next.js的实践项目，包含了现代Web开发的最佳实践：

- ⚡ **Next.js 15.3.3** - 使用最新版本的Next.js框架
- 🎨 **Tailwind CSS** - 现代化的CSS框架
- 📝 **TypeScript** - 类型安全的JavaScript
- 🔧 **ESLint** - 代码规范检查
- ⚡ **Turbopack** - 快速的构建工具

## 🛠️ 技术栈

- **Frontend**: Next.js, React 19, TypeScript
- **样式**: Tailwind CSS 4.0
- **开发工具**: ESLint, Turbopack
- **包管理器**: npm

## 📦 安装与运行

### 1. 克隆项目
```bash
git clone https://github.com/MM1997/my-nextjs-learning-project.git
cd my-nextjs-learning-project
```

### 2. 安装依赖
```bash
npm install
```

### 3. 启动开发服务器
```bash
npm run dev
```

### 4. 打开浏览器
访问 [http://localhost:3000](http://localhost:3000) 查看项目

## 📝 可用脚本

- `npm run dev` - 启动开发服务器（使用Turbopack）
- `npm run build` - 构建生产版本
- `npm run start` - 启动生产服务器
- `npm run lint` - 运行ESLint检查

## 🎯 学习目标

- [x] 创建Next.js项目
- [x] 配置TypeScript
- [x] 集成Tailwind CSS
- [x] 修复Hydration错误
- [x] 配置GitHub MCP
- [x] 部署到GitHub

## 🔧 项目配置

### GitHub MCP集成
项目已配置GitHub MCP（Model Context Protocol），支持：
- GitHub仓库管理
- Issues和Pull Requests
- 代码搜索和查看
- 自动化工作流

### 防翻译配置
为解决React Hydration错误，项目已配置：
- HTML `translate="no"` 属性
- `suppressHydrationWarning` 配置

## 📁 项目结构

```
my-nextjs-learning-project/
├── app/                    # Next.js App Router
│   ├── layout.tsx         # 根布局
│   ├── page.tsx           # 首页
│   └── globals.css        # 全局样式
├── public/                # 静态资源
├── .vscode/               # VS Code配置
│   └── mcp.json          # GitHub MCP配置
├── docs/                  # 文档
├── package.json           # 项目配置
├── tsconfig.json          # TypeScript配置
├── tailwind.config.ts     # Tailwind配置
├── next.config.ts         # Next.js配置
└── README.md             # 项目说明
```

## 🌟 特性

- ✅ 服务端渲染 (SSR)
- ✅ 静态生成 (SSG)
- ✅ 响应式设计
- ✅ 类型安全
- ✅ 热重载
- ✅ 代码分割
- ✅ 性能优化

## 🎓 学习资源

- [Next.js 官方文档](https://nextjs.org/docs)
- [React 官方文档](https://react.dev)
- [Tailwind CSS 文档](https://tailwindcss.com/docs)
- [TypeScript 文档](https://www.typescriptlang.org/docs)

## 📄 许可证

MIT License - 详见 [LICENSE](LICENSE) 文件

## 👤 作者

**MM1997**
- GitHub: [@MM1997](https://github.com/MM1997)
- 项目链接: [my-nextjs-learning-project](https://github.com/MM1997/my-nextjs-learning-project)

---

⭐ 如果这个项目对您有帮助，请给个星标！
