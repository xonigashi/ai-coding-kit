# AI Coding Kit

> Protocols, templates, and scripts for AI-augmented software development.
>
> AI 增强软件开发的协议、模板和脚本。

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

---

## Why This Exists / 为什么需要这个

AI coding assistants (Claude, Cursor, Copilot) are powerful but work best with structured guidance. This kit provides:

- **Protocols** - Rules for AI to follow when writing/maintaining code
- **Templates** - Ready-to-use document templates for AI collaboration
- **Scripts** - Automation for server setup, project bootstrapping, and more
- **Prompts** - Battle-tested prompts for common development tasks

AI 编码助手功能强大，但在有结构化指导时效果最佳。本工具包提供：

- **协议** - AI 编写/维护代码时遵循的规则
- **模板** - 用于 AI 协作的即用型文档模板
- **脚本** - 服务器设置、项目初始化等自动化脚本
- **提示词** - 经过实战检验的常用开发提示词

---

## Quick Start / 快速开始

### Use a Protocol / 使用协议

Copy the protocol to your project's `CLAUDE.md`, `.cursorrules`, or AI config:

```bash
# Download fractal docs protocol
curl -o CLAUDE.md https://raw.githubusercontent.com/JessyTsui/ai-coding-kit/main/protocols/fractal-docs.md
```

Then tell your AI:
> "Follow the protocol in CLAUDE.md"

### Bootstrap a Project / 初始化项目

```bash
# Initialize fractal documentation structure
curl -fsSL https://raw.githubusercontent.com/JessyTsui/ai-coding-kit/main/scripts/project/init-fractal-docs.sh | bash
```

### Setup a Server / 配置服务器

```bash
# Ubuntu server initialization
curl -fsSL https://raw.githubusercontent.com/JessyTsui/ai-coding-kit/main/scripts/server/ubuntu-init.sh | bash
```

---

## Contents / 内容

```
ai-coding-kit/
├── protocols/          # AI behavior protocols / AI 行为协议
│   └── fractal-docs.md # Self-referential documentation system
│
├── templates/          # Document templates / 文档模板
│   ├── CLAUDE.md       # Claude Code configuration
│   ├── design-doc.md   # Design document template
│   └── ...
│
├── scripts/            # Automation scripts / 自动化脚本
│   ├── server/         # Server setup scripts
│   ├── project/        # Project bootstrapping
│   └── git/            # Git hooks and configs
│
├── prompts/            # Prompt library / 提示词库
│   ├── code-review/    # Code review prompts
│   ├── debugging/      # Debugging prompts
│   └── ...
│
├── configs/            # Config files / 配置文件
│   ├── eslint/         # ESLint configs
│   ├── prettier/       # Prettier configs
│   └── ...
│
├── checklists/         # Quality checklists / 质量检查清单
│   ├── security.md     # Security audit checklist
│   ├── performance.md  # Performance audit checklist
│   └── ...
│
└── guides/             # How-to guides / 指南文档
    ├── ai-pairing.md   # AI pair programming guide
    └── ...
```

---

## Protocols / 协议

### [Fractal Docs Protocol](./protocols/fractal-docs.md)

A self-referential documentation system inspired by "Gödel, Escher, Bach". Creates a fractal structure where:

- Every folder has a `.folder.md` with 3-line description + file list
- Every file has `[IN]/[OUT]/[POS]` header comments
- Changes automatically propagate through the documentation tree

一个受《哥德尔、埃舍尔、巴赫》启发的自指文档系统，创建分形结构：

- 每个文件夹有 `.folder.md`，包含3行描述 + 文件清单
- 每个文件有 `[IN]/[OUT]/[POS]` 头注释
- 变更自动传播到文档树

---

## Contributing / 贡献

Contributions are welcome! Please:

1. Fork this repository
2. Create a feature branch
3. Submit a pull request

欢迎贡献！请：

1. Fork 本仓库
2. 创建功能分支
3. 提交 Pull Request

---

## License / 许可证

[MIT](./LICENSE) - Use freely, attribution appreciated.

MIT 许可证 - 自由使用，感谢署名。

---

## Acknowledgments / 致谢

- Inspired by "Gödel, Escher, Bach" by Douglas Hofstadter
- Built for the AI-augmented development era

---

**Star this repo if you find it useful!**

**如果觉得有用，请给个 Star！**
