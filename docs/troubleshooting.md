# 问题排查与解决方案

> 记录学习和开发过程中遇到的各种问题及其解决方案

## 🚨 常见问题索引

### React/Next.js 相关

#### 1. Hydration 错误
**问题**: `Hydration failed because the server rendered HTML didn't match the client`

**常见原因**:
- 浏览器翻译插件修改HTML
- 服务器和客户端的随机数不一致
- 日期格式化差异
- 无效的HTML嵌套

**解决方案**:
```typescript
// 1. 添加防翻译属性
<html lang="en" suppressHydrationWarning translate="no">
  <body suppressHydrationWarning>

// 2. 使用suppressHydrationWarning（谨慎使用）
<div suppressHydrationWarning>
  {/* 可能不匹配的内容 */}
</div>

// 3. 使用useEffect处理客户端特定内容
const [isClient, setIsClient] = useState(false)
useEffect(() => setIsClient(true), [])
return isClient ? <ClientOnlyContent /> : <ServerContent />
```

#### 2. TypeScript 类型错误
**问题**: 各种TypeScript类型相关错误

**解决方案**:
```typescript
// 正确的组件类型定义
interface Props {
  children: React.ReactNode;
  title?: string;
}

export default function Component({ children, title }: Props) {
  return <div>{children}</div>
}

// Next.js页面组件类型
import { NextPage } from 'next'
const HomePage: NextPage = () => {
  return <div>Home</div>
}
```

### 开发环境问题

#### 1. PowerShell 语法错误
**问题**: `标记"&&"不是此版本中的有效语句分隔符`

**解决方案**:
```powershell
# 错误写法
git add . && git commit -m "message"

# 正确写法
git add .; git commit -m "message"
# 或者分开执行
git add .
git commit -m "message"
```

#### 2. 端口占用问题
**问题**: `Port 3000 is already in use`

**解决方案**:
```bash
# 查找占用端口的进程
netstat -ano | findstr :3000

# Windows结束进程
taskkill /PID <PID> /F

# 或者使用其他端口
npm run dev -- -p 3001
```

### 样式相关问题

#### 1. Tailwind CSS 不生效
**问题**: Tailwind样式不显示

**检查清单**:
```typescript
// 1. 确认 globals.css 正确导入
@tailwind base;
@tailwind components;
@tailwind utilities;

// 2. 检查 tailwind.config.ts
export default {
  content: [
    "./app/**/*.{js,ts,jsx,tsx,mdx}",
    // 确保路径正确
  ],
}

// 3. 重启开发服务器
npm run dev
```

#### 2. 暗色模式切换问题
**解决方案**:
```typescript
// 使用 next-themes
import { useTheme } from 'next-themes'

function ThemeToggle() {
  const { theme, setTheme } = useTheme()
  
  return (
    <button onClick={() => setTheme(theme === 'dark' ? 'light' : 'dark')}>
      切换主题
    </button>
  )
}
```

### 构建和部署问题

#### 1. 构建失败
**常见原因**:
- TypeScript错误
- ESLint错误
- 依赖版本冲突

**解决方案**:
```bash
# 检查错误
npm run lint
npm run build

# 修复常见问题
npm run lint -- --fix
```

#### 2. 静态资源404
**解决方案**:
```typescript
// 正确的静态资源引用
import Image from 'next/image'

<Image
  src="/images/logo.png"  // public目录下的文件
  alt="Logo"
  width={100}
  height={100}
/>
```

### Git 相关问题

#### 1. 推送到GitHub失败
**问题**: 认证失败或权限问题

**解决方案**:
```bash
# 检查远程仓库
git remote -v

# 更新远程仓库URL
git remote set-url origin https://github.com/username/repo.git

# 使用Personal Access Token
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

#### 2. 合并冲突
**解决方案**:
```bash
# 查看冲突文件
git status

# 手动解决冲突后
git add .
git commit -m "resolve conflicts"
```

## 🔍 调试技巧

### 1. React DevTools
```typescript
// 在组件中添加调试信息
console.log('Component props:', props)
console.log('Component state:', state)

// 使用 React DevTools 浏览器扩展
```

### 2. Next.js 调试
```typescript
// next.config.ts 中启用调试
/** @type {import('next').NextConfig} */
const nextConfig = {
  experimental: {
    logging: {
      level: 'verbose',
    },
  },
}
```

### 3. 网络请求调试
```typescript
// 使用浏览器开发者工具的Network面板
// 或者添加请求日志
fetch('/api/data')
  .then(res => {
    console.log('Response status:', res.status)
    return res.json()
  })
  .then(data => console.log('Data:', data))
  .catch(err => console.error('Error:', err))
```

## 📋 预防措施

### 1. 代码质量
```bash
# 设置Git hooks
npx husky install
npx husky add .husky/pre-commit "npm run lint && npm run build"
```

### 2. 依赖管理
```bash
# 锁定依赖版本
npm install --save-exact package-name

# 定期更新依赖
npm audit
npm update
```

### 3. 备份策略
```bash
# 定期推送到GitHub
git push origin main

# 创建功能分支
git checkout -b feature/new-feature
```

## 🛠️ 有用的工具

### 1. 调试工具
- React DevTools
- Next.js DevTools
- 浏览器开发者工具

### 2. 代码检查
- ESLint
- Prettier
- TypeScript编译器

### 3. 性能监控
- Lighthouse
- Web Vitals
- Next.js Analytics

## 📚 参考资源

### 官方文档
- [Next.js Troubleshooting](https://nextjs.org/docs/app/building-your-application/configuring/debugging)
- [React DevTools](https://react.dev/learn/react-developer-tools)

### 社区资源
- [Stack Overflow](https://stackoverflow.com/questions/tagged/next.js)
- [GitHub Issues](https://github.com/vercel/next.js/issues)
- [Next.js Discord](https://discord.gg/nextjs)

---

*最后更新: 2025年6月3日*

> 💡 **提示**: 遇到新问题时，记得更新这个文档！ 