# MathArt Studio 分发仓库管理手册

本文档旨在指导管理员如何维护 `mathart-dist` 仓库，包括发布流程、文档维护及 Issue 管理。

## 1. 仓库结构说明

`mathart-dist` 是一个公开仓库，仅用于：
1.  **托管二进制安装包 (Releases)**：利用 GitHub Releases 功能作为全球 CDN。
2.  **用户反馈 (Issues)**：作为公开的反馈渠道。
3.  **文档 (README)**：提供下载引导。

**注意**：不要将任何源代码或私有密钥上传到此仓库。

## 2. Release 发布标准流程

每次发布新版本（如 v1.0.1）时，请严格按照以下步骤操作：

### 步骤 1: 准备工作
确保你已经编译并打包好了安装文件：
*   macOS: `MathArt-Studio-v1.0.1-mac.dmg`
*   Windows: `MathArt-Studio-v1.0.1-win.exe`

### 步骤 2: 创建 Tag (标签)
虽然可以在 GitHub 网页上直接创建 Tag，但建议在本地使用 git 命令行以保持严谨：
```bash
# 在 mathart-dist 仓库目录下
git pull
git tag v1.0.1
git push origin v1.0.1
```
*(如果不想用命令行，直接跳到步骤 3，在网页上创建 Tag 也可以)*

### 步骤 3: 草拟 Release (Draft a new release)
1.  打开仓库主页 -> 点击右侧 **Releases** -> 点击 **Draft a new release**。
2.  **Choose a tag**: 选择刚才创建的 `v1.0.1`（或者在这里直接输入新 Tag 名创建）。
3.  **Release title**: 标题格式建议为 `MathArt Studio v1.0.1`。
4.  **Describe this release**: 填写更新日志（详见下文模板）。
5.  **Attach binaries**: 将 `.dmg` 和 `.exe` 文件拖入下方的上传区域。**必须确保上传完成**。
6.  勾选 **Set as the latest release**。
7.  点击 **Publish release**。

### 步骤 4: 同步国内源 (重要)
发布完成后，立即将这两个安装包上传到 **123 云盘** 的 `MathArt 最新版` 文件夹中，以供国内用户下载。

---

## 3. Release Log 编写规范

Release Log 是用户了解版本更新的窗口，建议采用中英双语，清晰列出变更点。

**模板：**

```markdown
## 🎉 What's New / 更新亮点

### ✨ New Features / 新特性
- **Real-time Raymarching**: Added support for real-time raymarching rendering.
- **实时光线步进**: 新增了实时光线步进渲染支持。
- **Video Export**: Now supports 4K 60FPS export.
- **视频导出**: 现在支持 4K 60FPS 导出。

### 🐞 Bug Fixes / 问题修复
- Fixed a crash on macOS Sequoia when resizing window.
- 修复了 macOS Sequoia 下调整窗口大小时崩溃的问题。

### 📦 Installation / 安装说明
- **macOS**: Download `.dmg`, drag to Applications. (Require macOS 12+)
- **Windows**: Download `.exe`, follow the setup wizard. (Require Windows 10/11)

---
*If you are in Mainland China, please download from our [Official Website](https://mathart.vercel.app/zh/download) for faster speed.*
*中国大陆用户请前往 [官网](https://mathart.vercel.app/zh/download) 获取高速下载链接。*
```

## 4. Issue 管理规范

### 模板使用
我们已经预置了两个模板：
1.  **Bug Report**: 用于报告错误，强制用户填写复现步骤和环境信息。
2.  **Feature Request**: 用于功能建议。

### 处理流程
1.  **定期检查 (Daily/Weekly)**：管理员应定期查看 Issues。
2.  **打标签 (Labeling)**：
    *   确认是 Bug -> 加上 `bug` 标签。
    *   确认是建议 -> 加上 `enhancement` 标签。
    *   无法复现/无效 -> 加上 `invalid` 标签并关闭。
3.  **回复与关闭**：
    *   回复用户时请保持专业和礼貌。
    *   问题解决后，务必关闭 Issue。

## 5. README 维护

`README.md` 是仓库的门面。
*   **双语对照**：标题和正文尽量使用中英双语，方便全球用户。
*   **链接检查**：确保指向官网和下载页的链接永远有效。

---
**常见问题 FAQ**

Q: 如果我想撤回一个版本怎么办？
A: 在 Releases 页面找到该版本，点击 Edit -> Delete release。注意这会删除该版本下的所有附件。

Q: 如何更新 Latest 链接？
A: GitHub 会自动将最新的 Release 标记为 Latest。只要你发布了新版本，`releases/latest` 的链接就会自动指向新版本。
