<h1 align="center">Run Skills</h1>

<p align="center">
    <a href="./README.md">English</a> | <strong>简体中文</strong>
</p>

这是一个用于管理和分发 Gemini CLI 技能（Skills）的项目。每个技能都旨在增强模型在特定领域（如系统操作、代码分析等）的处理能力。

## 技能列表

| 技能名称                                               | 描述                                                         | 安装方法                                                     |
| :----------------------------------------------------- | :----------------------------------------------------------- | :----------------------------------------------------------- |
| [desktop-commander](skills/desktop-commander/SKILL.md) | 使用 Desktop Commander MCP 进行本地文件/目录操作、精确文本替换、进程管理、搜索及 Excel/PDF 处理。 | `npx skills add https://github.com/ry-run/run-skills --skill desktop-commander` |
| [jetbrains-skill](skills/jetbrains-skill/SKILL.md)     | 使用 JetBrains IDE MCP Server (IntelliJ 2025.2+) 驱动 IDE 动作：运行配置、终端命令、诊断、重构、索引搜索等。 | `npx skills add https://github.com/ry-run/run-skills --skill jetbrains-skill` |
