# Claudian (AndySuen1 Fork)

**[English](README_en.md) | 中文**

![GitHub stars](https://img.shields.io/github/stars/AndySuen1/claudian?style=social)
![GitHub release](https://img.shields.io/github/v/release/AndySuen1/claudian)
![License](https://img.shields.io/github/license/AndySuen1/claudian)

本仓库是 [YishenTu/claudian](https://github.com/YishenTu/claudian) 的 fork，在其基础上增加了若干个人偏好的功能改动。

**原插件的介绍、安装、配置、使用方法、权限模型、隐私说明、故障排除等完整文档，请参见上游仓库：** [YishenTu/claudian](https://github.com/YishenTu/claudian)

本 README 仅描述本 fork 相较上游的差异功能。

## 本 Fork 新增功能

### Sandbox 模式
工具栏新增 Sandbox 开关，默认启用：
- **启用时**：自动切换至 Haiku 模型并关闭外部文件访问，为默认会话提供轻量、安全的沙箱环境。
- **关闭时**：恢复之前使用的模型并重新开放外部访问。
- 该设置按 Tab 单独保存（`tabAllowExternalAccess`），不同 Tab 之间互不干扰。

### 标题栏会话标题
单 Tab 模式下，标题栏在品牌名旁实时显示当前会话标题，方便快速识别当前对话。

### 拖拽切换当前笔记
将笔记库中的任意文件拖拽到输入框，即可将其设置为当前笔记上下文。

### FileContext 自动切换修复
会话开始后切换到未被排除的笔记时，当前笔记会自动更新并重置 sent 状态，使新笔记能在下一轮对话中被重新发送。

## 安装

与上游仓库完全一致，只需把仓库 URL 换成本 fork 即可：

### GitHub Release
从 [最新版本](https://github.com/AndySuen1/claudian/releases/latest) 下载 `main.js`、`manifest.json`、`styles.css`，放入 `/path/to/vault/.obsidian/plugins/claudian/`，然后在 Obsidian 的第三方插件中启用。

### BRAT
在 BRAT 中添加仓库 URL：`https://github.com/AndySuen1/claudian`。

### 源码构建
```bash
cd /path/to/vault/.obsidian/plugins
git clone https://github.com/AndySuen1/claudian.git
cd claudian
npm install
npm run build
```

更详细的步骤请见 [上游 README](https://github.com/YishenTu/claudian)。

## 许可证

基于 [MIT 许可证](LICENSE) 授权。

## 致谢

- 原项目 [YishenTu/claudian](https://github.com/YishenTu/claudian)：本 fork 的所有基础功能均来自该项目。
- [Obsidian](https://obsidian.md)、[Anthropic](https://anthropic.com)、[OpenAI](https://openai.com)。
