# ArXiv MCP Server

一个支持自定义 LLM API 的 ArXiv 论文智能解读助手。支持 Model Context Protocol (MCP) 标准，将学术论文一键转为通俗中文解读和微信公众号文章。

## 功能亮点

- 🔍 **arXiv 论文智能搜索** - 关键词检索，快速定位你关心的论文
- 📥 **一键下载 PDF** - 自动获取并保存原始论文
- 📝 **中英文智能转换** - 将 PDF 英文内容解析为高质量的中文 Markdown
- 📱 **微信文章生成** - 自动生成适配微信阅读体验的文章草稿
- 🗑️ **一键清理文件** - 支持一键清空所有历史处理文件
- 🤖 **自定义 LLM API** - 支持使用任意 OpenAI 兼容的 API

## 安装

```bash
# 克隆仓库
git clone https://github.com/rouse2617/mcp-arxiv-server.git
cd mcp-arxiv-server

# 安装依赖
npm install

# 构建
npm run build
```

## 配置

### 环境变量

创建 `.env` 文件或直接在 MCP 配置中设置：

```bash
# LLM API 配置（必需）
LLM_API_ENDPOINT=https://your-api-endpoint.com/v1
LLM_API_KEY=your_api_key_here
LLM_MODEL=your_model_name
LLM_MAX_TOKENS=4096
LLM_TIMEOUT=120000

# 工作目录（必需）
WORK_DIR=/path/to/your/data/directory
```

### Claude Desktop 配置

在 Claude Desktop 的配置文件中添加：

```json
{
  "mcpServers": {
    "arxiv-mcp-server": {
      "command": "node",
      "args": ["/path/to/mcp-arxiv-server/build/index.js"],
      "env": {
        "LLM_API_ENDPOINT": "https://your-api-endpoint.com/v1",
        "LLM_API_KEY": "your_api_key",
        "LLM_MODEL": "your_model",
        "LLM_MAX_TOKENS": "4096",
        "LLM_TIMEOUT": "120000",
        "WORK_DIR": "/path/to/data/arxiv"
      }
    }
  }
}
```

### Claude Code (.mcp.json)

在项目根目录创建 `.mcp.json`：

```json
{
  "mcpServers": {
    "arxiv-mcp-server": {
      "command": "node",
      "args": ["./mcp-arxiv-server/build/index.js"],
      "env": {
        "LLM_API_ENDPOINT": "https://your-api-endpoint.com/v1",
        "LLM_API_KEY": "your_api_key",
        "LLM_MODEL": "your_model",
        "WORK_DIR": "./data/arxiv"
      }
    }
  }
}
```

## 可用工具

| 工具 | 描述 |
|------|------|
| `search_arxiv` | 搜索 arXiv 论文 |
| `download_arxiv_pdf` | 下载 PDF |
| `parse_pdf_to_text` | 解析 PDF 为文本 |
| `parse_pdf_to_markdown` | 翻译为中文 Markdown |
| `convert_to_wechat_article` | 转换为微信文章 |
| `process_arxiv_paper` | 完整流程处理 |
| `clear_workdir` | 清空工作区 |

## 使用示例

```
# 搜索论文
"帮我搜索关于 transformer 的 arxiv 论文"

# 下载论文
"下载 arxiv 论文 1706.03762 的 PDF"

# 翻译论文
"将论文 1706.03762 翻译成中文 Markdown"

# 生成微信文章
"将论文 1706.03762 转换为微信文章格式"

# 完整处理
"完整处理 arxiv 论文 1706.03762"
```

## 支持的 LLM API

本项目使用 OpenAI 兼容的 API 格式，理论上支持所有兼容的 API：

- OpenAI API
- DeepSeek API
- SiliconFlow API
- 任何其他 OpenAI 兼容的 API

## 项目结构

```
mcp-arxiv-server/
├── src/
│   └── index.ts          # 主服务器文件
├── build/                # 编译输出目录
├── package.json          # 项目配置
├── tsconfig.json         # TypeScript 配置
└── README.md             # 项目说明
```

## 开发

```bash
# 开发模式运行
npm run dev

# 构建
npm run build

# 运行构建版本
npm start
```

## 技术栈

- Node.js >= 18.0.0
- TypeScript
- Model Context Protocol SDK
- @agentic/arxiv - ArXiv API 客户端
- axios - HTTP 请求
- pdfreader - PDF 解析

## 许可证

MIT License

## 原项目

基于 [yzfly/arxiv-mcp-server](https://github.com/yzfly/arxiv-mcp-server) 修改，将 SiliconFlow API 替换为自定义 LLM API 支持。

## 作者

[@rouse2617](https://github.com/rouse2617)
