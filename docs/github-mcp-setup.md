# GitHub MCP 集成指南

## 为Next.js项目设置GitHub MCP

### 快速开始

1. **安装Docker**
   ```bash
   # 确保Docker正在运行
   docker --version
   ```

2. **创建GitHub Token**
   - 访问: https://github.com/settings/tokens
   - 生成新token，选择必要权限
   - 复制并安全保存token

3. **VS Code配置 (推荐)**
   创建 `.vscode/mcp.json`:
   ```json
   {
     "inputs": [
       {
         "type": "promptString",
         "id": "github_token", 
         "description": "GitHub Personal Access Token",
         "password": true
       }
     ],
     "servers": {
       "github": {
         "command": "docker",
         "args": [
           "run", "-i", "--rm", "-e",
           "GITHUB_PERSONAL_ACCESS_TOKEN",
           "ghcr.io/github/github-mcp-server"
         ],
         "env": {
           "GITHUB_PERSONAL_ACCESS_TOKEN": "YOUR_GITHUB_TOKEN"
         }
       }
     }
   }
   ```

### 使用方式

1. 在VS Code中打开Copilot Chat
2. 选择"Agent"模式  
3. 现在您可以执行:
   - "在我的仓库中创建一个新issue"
   - "列出所有开放的pull requests"
   - "获取仓库的star数量"
   - "搜索特定的issues"

### 支持的操作

- ✅ 创建和管理Issues
- ✅ 查看和管理Pull Requests  
- ✅ 搜索仓库内容
- ✅ 获取仓库统计信息
- ✅ 管理分支和标签
- ✅ 查看提交历史

### 安全建议

- 使用最小权限原则配置token
- 定期轮换access token
- 不要在代码中硬编码token
- 考虑使用fine-grained tokens 