# 流年之书 (EpochLetter) 📮

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

一个基于 GitHub Actions 的零成本、去中心化时间胶囊服务。为你封存今日的思绪，寄给未来的自己。

[查看所有公开的时光胶囊 ->](https://your-username.github.io/EpochLetter/)

---

## 📖 项目简介 (About)

**流年之书 (EpochLetter)** 是一个独特的项目，它允许您向未来的自己发送邮件。不同于中心化的网站服务，ChronoPost 采用了一种完全去中心化的模式，充分利用了 GitHub 生态系统。

您只需要 Fork 这个项目，它就会在您自己的仓库中，成为一个只属于您的、完全独立的私人时间胶囊服务。所有的数据（您的信件内容、邮箱地址）都安全地存放在您自己的仓库中，由您完全掌控。

这一切都运行在 GitHub Actions 的免费额度上，真正实现了**零成本**运行。

## ✨ 核心特性 (Features)

- **💌 完全免费**: 无需服务器，无需付费，所有功能均基于 GitHub 的免费服务。
- **🔐 数据主权**: 您的所有信件和私人信息都存储在您自己的 GitHub 仓库中，绝不外泄。
- **🚀 高度自动化**: “Git Push 即 API”。您只需修改一个文件并推送，剩下的交给 GitHub Actions。
- **🎨 个性化展示**: 每个 Fork 的项目都可以拥有自己的 GitHub Pages 展示墙，展示您想公开的信件。
- **🌐 社区共享**: 您可以选择性地将某些信件分享到主项目的公共展示墙，成为全球记忆的一部分。
- **🔧 易于部署**: 只需三步（Fork -> 配置密钥 -> 修改文件），即可拥有自己的时间胶囊服务。

## 🚀 工作原理 (How It Works)

“流年之书”的魔法来自于 GitHub Actions 的强大自动化能力。

1.  **Fork 项目**: 您将主项目 Fork 到您的账户下，获得一份完整的代码副本。
2.  **配置密钥**: 您从免费邮件服务商 [Resend](https://resend.com) 获取一个 API Key，并将其作为 Secret 添加到您自己仓库的设置中。
3.  **添加胶囊**: 您在仓库的 `_data/capsules.yml` 文件中，按照简单格式写下您的信件内容、目标邮箱和发送日期。
4.  **Git Push**: 您将修改后的文件 `git push` 到您的仓库。
5.  **触发自动化**: 一个预设的 GitHub Action 工作流会每天定时被唤醒。
6.  **执行与发送**: 它会运行一个 Python 脚本，检查所有“待发送”的胶囊。如果发现有胶囊的日期已到，它就会使用您的 API Key，通过 Resend 将邮件发送出去，并自动更新该胶囊的状态为“已发送”。

## 快速上手 (Getting Started)

只需简单几步，即可启动您的流年之书。

### 1. Fork 本项目

点击本仓库页面右上角的 **Fork** 按钮。

### 2. 获取并配置 API 密钥

您需要一个免费的 Resend API Key 来发送邮件。

👉 **[点击查看详细的图文设置指南 (SETUP.md)](SETUP.md)**

这份指南会手把手教您如何获取 Key 并将其配置到您的仓库 Secrets 中，这是整个项目能运行起来的**最关键一步**。

### 3. 添加你的第一个时间胶囊

克隆您自己的 Fork 仓库到本地，然后编辑 `_data/capsules.yml` 文件，添加您的第一条内容：

```yaml
- id: 1
  email: "your-email@example.com" # 您的收件邮箱
  delivery_date: "2030-01-01" # 您期望的未来收信日期
  content: | # 在这里写下您想说的话
    你好，未来的我！
    希望你收到这封信时，一切都好。
  status: "scheduled" # 状态保持 "scheduled"
  is_public_to_fork_pages: true # 是否在您自己的主页展示
  is_public_to_main_project: true # 是否同意分享到主项目公共墙
```
