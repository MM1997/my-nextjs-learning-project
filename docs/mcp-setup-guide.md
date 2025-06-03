# MCP工具配置完全指南

> 为AI辅助开发配置强大的MCP工具生态

## 🎯 目标

建立一个功能强大的MCP工具链，让AI助手能够：
- 💾 直接操作数据库
- 📁 管理文件系统
- 🌐 发送网络请求
- 🔍 进行网页自动化测试
- 📊 分析和处理数据

---

## 🛠️ 核心MCP工具安装

### 1. 文件系统操作 📁

**安装**:
```bash
npm install -g @modelcontextprotocol/server-filesystem
```

**配置** (添加到 `C:\Users\ZongM\.cursor\mcp.json`):
```json
{
  "mcpServers": {
    "filesystem": {
      "command": "npx",
      "args": ["@modelcontextprotocol/server-filesystem"],
      "env": {
        "ALLOWED_DIRECTORIES": "C:/Users/ZongM/Desktop/learn,C:/Users/ZongM/Desktop/projects,C:/workspace"
      }
    }
  }
}
```

**功能**:
- 📖 读取文件内容
- ✏️ 写入文件
- 📁 创建目录
- 🔍 搜索文件
- 📋 列出目录内容

### 2. 网络请求工具 🌐

**安装**:
```bash
npm install -g @modelcontextprotocol/server-fetch
```

**配置**:
```json
{
  "fetch": {
    "command": "npx",
    "args": ["@modelcontextprotocol/server-fetch"]
  }
}
```

**功能**:
- 🌐 发送HTTP请求
- 📡 调用第三方API
- 📊 获取外部数据
- 🔄 处理响应数据

### 3. SQLite数据库 🗄️

**安装**:
```bash
npm install -g @modelcontextprotocol/server-sqlite
```

**配置**:
```json
{
  "sqlite": {
    "command": "npx",
    "args": ["@modelcontextprotocol/server-sqlite"],
    "env": {
      "SQLITE_DB_PATH": "./data/development.db"
    }
  }
}
```

**功能**:
- 📊 执行SQL查询
- 🏗️ 创建表结构
- 💾 插入/更新数据
- 📈 数据分析
- 🔄 数据迁移

### 4. PostgreSQL数据库 🐘

**安装**:
```bash
npm install -g @modelcontextprotocol/server-postgresql
```

**配置**:
```json
{
  "postgresql": {
    "command": "npx",
    "args": ["@modelcontextprotocol/server-postgresql"],
    "env": {
      "POSTGRES_CONNECTION_STRING": "postgresql://username:password@localhost:5432/database_name"
    }
  }
}
```

### 5. 网页自动化 (Puppeteer) 🤖

**安装**:
```bash
npm install -g @modelcontextprotocol/server-puppeteer
```

**配置**:
```json
{
  "puppeteer": {
    "command": "npx",
    "args": ["@modelcontextprotocol/server-puppeteer"]
  }
}
```

**功能**:
- 🔍 自动化测试
- 📸 网页截图
- 📄 生成PDF
- 🕷️ 网页爬虫
- 🧪 E2E测试

---

## 📋 完整配置文件

### 基础配置
```json
{
  "mcpServers": {
    "github": {
      "command": "npx",
      "args": ["@modelcontextprotocol/server-github"],
      "env": {
        "GITHUB_PERSONAL_ACCESS_TOKEN": "your_github_token_here"
      }
    },
    "filesystem": {
      "command": "npx",
      "args": ["@modelcontextprotocol/server-filesystem"],
      "env": {
        "ALLOWED_DIRECTORIES": "C:/Users/ZongM/Desktop/learn,C:/Users/ZongM/Desktop/projects"
      }
    },
    "fetch": {
      "command": "npx",
      "args": ["@modelcontextprotocol/server-fetch"]
    },
    "sqlite": {
      "command": "npx",
      "args": ["@modelcontextprotocol/server-sqlite"],
      "env": {
        "SQLITE_DB_PATH": "./data/app.db"
      }
    }
  }
}
```

### 高级配置 (添加更多工具)
```json
{
  "mcpServers": {
    "github": {
      "command": "npx",
      "args": ["@modelcontextprotocol/server-github"],
      "env": {
        "GITHUB_PERSONAL_ACCESS_TOKEN": "your_github_token_here"
      }
    },
    "filesystem": {
      "command": "npx",
      "args": ["@modelcontextprotocol/server-filesystem"],
      "env": {
        "ALLOWED_DIRECTORIES": "C:/Users/ZongM/Desktop/learn,C:/Users/ZongM/Desktop/projects,C:/workspace"
      }
    },
    "fetch": {
      "command": "npx",
      "args": ["@modelcontextprotocol/server-fetch"]
    },
    "sqlite": {
      "command": "npx",
      "args": ["@modelcontextprotocol/server-sqlite"],
      "env": {
        "SQLITE_DB_PATH": "./data/app.db"
      }
    },
    "postgresql": {
      "command": "npx",
      "args": ["@modelcontextprotocol/server-postgresql"],
      "env": {
        "POSTGRES_CONNECTION_STRING": "postgresql://localhost:5432/myapp"
      }
    },
    "puppeteer": {
      "command": "npx",
      "args": ["@modelcontextprotocol/server-puppeteer"]
    }
  }
}
```

---

## 🚀 安装步骤

### 第一步: 安装所有MCP工具
```bash
# 基础工具
npm install -g @modelcontextprotocol/server-github
npm install -g @modelcontextprotocol/server-filesystem  
npm install -g @modelcontextprotocol/server-fetch
npm install -g @modelcontextprotocol/server-sqlite

# 可选高级工具
npm install -g @modelcontextprotocol/server-postgresql
npm install -g @modelcontextprotocol/server-puppeteer
```

### 第二步: 创建项目数据目录
```bash
# 在项目根目录创建数据文件夹
mkdir data
```

### 第三步: 配置mcp.json
1. 打开 `C:\Users\ZongM\.cursor\mcp.json`
2. 将上面的配置复制进去
3. 替换GitHub token为您的实际token

### 第四步: 重启Cursor
完全关闭Cursor，然后重新打开以加载新的MCP配置。

---

## 🧪 测试MCP工具

### 测试文件系统工具
在Cursor的AI Chat中尝试：
```
请在项目中创建一个名为 test.md 的文件，内容是 "Hello MCP!"
```

### 测试网络请求工具
```
请帮我发送一个请求到 https://api.github.com/user，获取我的GitHub用户信息
```

### 测试SQLite工具
```
请创建一个用户表，包含id、name、email字段
```

### 测试GitHub工具
```
请列出我的GitHub仓库
```

---

## 🎯 使用场景示例

### 场景1: 全栈开发流程
```markdown
1. 使用filesystem创建项目结构
2. 使用github管理代码版本
3. 使用sqlite设计数据库
4. 使用fetch调试API
5. 使用puppeteer进行E2E测试
```

### 场景2: 数据处理管道
```markdown
1. 使用fetch获取外部数据
2. 使用sqlite存储和查询
3. 使用filesystem导出报告
4. 使用github提交结果
```

### 场景3: 自动化测试
```markdown
1. 使用puppeteer模拟用户操作
2. 使用filesystem保存测试结果
3. 使用github创建issue报告bug
```

---

## ⚠️ 安全注意事项

### 1. 文件系统权限
```json
// 只允许访问特定目录
"ALLOWED_DIRECTORIES": "C:/Users/ZongM/Desktop/learn,C:/Users/ZongM/Desktop/projects"
```

### 2. 数据库连接
```bash
# 使用环境变量保护敏感信息
export POSTGRES_CONNECTION_STRING="postgresql://user:pass@localhost:5432/db"
```

### 3. GitHub Token管理
- 🔒 定期轮换token
- 🎯 最小权限原则
- 📝 记录token用途

---

## 🔧 故障排除

### 问题1: MCP服务器启动失败
**解决方案**:
```bash
# 检查Node.js版本
node --version  # 需要 16+

# 重新安装MCP包
npm uninstall -g @modelcontextprotocol/server-*
npm install -g @modelcontextprotocol/server-github
```

### 问题2: 权限被拒绝
**解决方案**:
```json
// 检查mcp.json中的路径是否正确
"ALLOWED_DIRECTORIES": "C:/Users/YourUsername/Desktop/learn"
```

### 问题3: 数据库连接失败
**解决方案**:
```bash
# 检查数据库是否运行
# PostgreSQL
pg_isready

# SQLite - 检查文件路径
ls -la ./data/app.db
```

---

## 📈 性能优化

### 1. 缓存策略
```json
// 为频繁访问的数据库添加缓存
{
  "sqlite": {
    "env": {
      "SQLITE_CACHE_SIZE": "10000"
    }
  }
}
```

### 2. 连接池配置
```json
// PostgreSQL连接池
{
  "postgresql": {
    "env": {
      "POSTGRES_MAX_CONNECTIONS": "20"
    }
  }
}
```

---

## 🔮 扩展MCP生态

### 自定义MCP服务器
```typescript
// 创建自定义MCP服务器
// custom-mcp-server.ts
import { StdioServerTransport } from '@modelcontextprotocol/sdk/server/stdio.js';
import { Server } from '@modelcontextprotocol/sdk/server/index.js';

const server = new Server({
  name: "custom-server",
  version: "1.0.0"
});

// 添加自定义工具
server.setRequestHandler(ListToolsRequestSchema, async () => ({
  tools: [
    {
      name: "custom_tool",
      description: "My custom tool",
      inputSchema: {
        type: "object",
        properties: {
          input: { type: "string" }
        }
      }
    }
  ]
}));

server.setRequestHandler(CallToolRequestSchema, async (request) => {
  // 实现自定义逻辑
});
```

### 社区MCP工具
```bash
# 安装社区贡献的MCP工具
npm install -g mcp-server-docker      # Docker操作
npm install -g mcp-server-kubernetes  # K8s管理
npm install -g mcp-server-aws         # AWS服务
```

---

## 📚 学习资源

### 官方文档
- [MCP官方文档](https://modelcontextprotocol.io/docs)
- [GitHub MCP](https://github.com/modelcontextprotocol/servers)

### 社区资源  
- [MCP工具集合](https://github.com/modelcontextprotocol/servers)
- [自定义MCP教程](https://modelcontextprotocol.io/tutorials)

---

**下一步**: 
1. ✅ 安装推荐的MCP工具
2. ✅ 测试每个工具的功能
3. ✅ 在实际项目中使用
4. ✅ 根据需要添加更多工具

有了这些强大的MCP工具，您的AI助手将变得更加智能和有用！🚀 