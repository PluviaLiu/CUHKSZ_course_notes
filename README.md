
# CUHK(SZ) - PluviaLiu - 课程笔记

本仓库是我从大二下开始的个人笔记合集，也是 **Obsidian 知识库（vault）的实时副本**。其内容以 **Markdown** 为主，主要记录个人在 CUHK(SZ) 的相关课程的课件、习题与笔记（含大量 LaTeX 公式与双链笔记结构）。

## 📚 课程范围（持续更新）

目前包含（或正在整理）的课程笔记：

- **CSC3001** 离散数学 
- **MAT3253** 复变函数  
- **STA2001H** 概率与统计（荣誉）  
- **ECO2011** 微观经济学  
- **GEB2508** AI 与社会  

（后续会按学期/学习进度继续添加。）

## ✅ 使用方式

### 作为 Obsidian Vault 打开（推荐）
1. 安装 Obsidian：https://obsidian.md/
2. 克隆仓库：
   ```bash
   git clone <https://github.com/PluviaLiu/CUHKSZ_course_notes>
   ```
3. Obsidian → **打开文件夹为 vault** → 选择克隆后的文件夹。

### 同步到手机端（iOS）
1. 手机上下载 Working Copy 软件，登录 GitHub
2. 从 GitHub 上 pull 同步到手机端
3. 从"文件"里把此文件夹从 Working Copy 里拖动到手机端 Obsidian 文件夹下
   - ⚠️ **不要拖到 iCloud**，可能会出现同步问题
4. 打开 Obsidian app 即可浏览

## 🛠 Obsidian 配置（可选）

阅读笔记不强依赖这些配置；如果你也用 Obsidian，下面设置能获得类似 VSCode 的 UI 界面，与完善的 AI 协助体验。

### 版本控制/终端操作
- **Terminal**（插件）：在 Obsidian 内执行 Git 命令
  - `git add .`
  - `git commit -m "..." `
  - `git push`
- 可以配合 Obsidian CLI 使用。在网页端下载完成后，打开 terminal 即可进行快速操作。

### 外观设置
- 主题：**Blue Topaz**
- 字体：**KXGW WenKai**
- **Stille**：调暗除光标所在段落外的内容，辅助专注

### AI 插件
- 插件：**Copilot**
- 模型：**Gemini**
- 理由：对 LaTeX 公式复制/渲染更友好，并支持图片提问（适合题目截图询问）。
- 用法：可在 Copilot Commands 里预设 Prompt；输入框 `/` 或选中文本右键调用。

*可以配合 **Text Extractor** 使用：Copilot 无法直接读取本地 PDF 文本，Text Extractor 可以轻便提取文本。
  用法：打开 PDF → 右上角菜单 → 执行提取。

### Claude/Claudian 支持
- **Claudian**：将 Claude Code 内嵌到 Obsidian 内
  - **适用场景**：
    - 批量化处理：”帮我给这一系列标题重命名为 Def/Thm/Lemma 等开头”
    - 双链处理：”给我扫描这个知识库下的知识点，在知识点的地方建立双链”

### 任务管理
- 插件：**Tasks**
- 我通常在文档开头记录任务与使用日期。之后，建立统一的任务看板，就可以纵览需要修改的文件和待整理的知识点。

## 📌 免责声明
本仓库为个人学习记录，内容可能存在不严谨或错误之处，仅供参考；如发现问题欢迎提 issue/讨论。
