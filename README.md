
- terminal：用于git add/commit/push


### Appearance
主题：
字体：KXGW wenkai

### AI辅助
选择插件：copilot
内接模型：gemini
	因为这样得到的结果不会乱码（包含一些html渲染的比如`\[ \]` 或 `\( \)`），可以直接复制进obsidian里。
prompt: 在copilot- command里设置。
	做题用：
平时的思维模式：先做题-做题过程中遇到知识点，直接双方括号外接一个单独文件-写入相关知识点-回到原题目。


# Obsidian 配置指南

欢迎来到我的知识库配置说明。

## 🛠 插件配置

### 1. PDF 批注 (插件名：Annotator)
用于对 PDF 文件进行批注。
- **使用方法**：新建一个 Markdown 文件，并在文件头（Frontmatter）中添加以下内容：

```yaml
---
annotation-target: 附件/你的作业文件名.pdf
---
```

### 2. 版本控制 (插件名：Terminal)
集成终端插件，用于执行 Git 命令：
- `git add .`
- `git commit -m "..."`
- `git push`

---

## 🎨 外观设置 (Appearance)

- **主题**：Blue Topaz
- **字体**：KXGW WenKai

---

## 🤖 AI 辅助 (Copilot)

- **插件选择**：Copilot
- **模型配置**：Gemini
  - *理由*：Gemini 对 LaTeX 公式（如 $...$）的渲染兼容性更好，能够直接复制到 Obsidian 中使用，避免乱码。
- **Prompt 设置**：请在 Copilot 的 Command 设置中进行配置。

---

## 💡 学习工作流

我的日常思维模式遵循“**原子化笔记**”原则：

1. **解题**：开始处理题目。
2. **拆解**：遇到关键知识点时，使用 `[[知识点名称]]` 创建双链。
3. **沉淀**：跳转至该独立文件，记录详细知识点。
4. **回归**：回到原题目继续解题。
