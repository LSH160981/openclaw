# OpenClaw
 

------------------------------------------------------------------------

# Overview

**OpenClaw** 是一个 **AI Agent 自动化网关系统**。

它将 **AI、消息平台、浏览器自动化、远程节点控制**整合到一个 CLI 中。

核心能力：

-   多平台消息发送
-   AI Agent 自动对话
-   WebSocket Gateway
-   浏览器自动化
-   定时任务系统
-   远程设备控制
-   记忆系统

支持平台：

    WhatsApp
    Telegram
    Discord
    Slack
    Signal
    iMessage
    Google Chat
    Microsoft Teams
    Mattermost

------------------------------------------------------------------------

# Features

### AI Agent

``` bash
openclaw agent --message "总结今天新闻"
```

-   AI 自动回复
-   多模型支持
-   长期记忆系统
-   Agent 自动化

------------------------------------------------------------------------

### Messaging Gateway

统一发送消息到多个平台：

``` bash
openclaw message send --channel telegram --target @chat --message "hello"
```

支持：

    WhatsApp
    Telegram
    Discord
    Slack
    Signal

------------------------------------------------------------------------

### Browser Automation

``` bash
openclaw browser open https://github.com
openclaw browser screenshot
```

支持：

    点击
    输入
    截图
    抓取 DOM
    自动化操作

------------------------------------------------------------------------

### Scheduler

``` bash
openclaw cron add --cron "0 9 * * *" --system-event "早安"
```

------------------------------------------------------------------------

### Remote Nodes

``` bash
openclaw nodes run --node macbook -- ls
```

------------------------------------------------------------------------

# Installation

### Install via npm

``` bash
npm install -g openclaw
```

### Install via npx

``` bash
npx openclaw setup
```

### Verify installation

``` bash
openclaw --version
```

------------------------------------------------------------------------

# Quick Start

初始化：

``` bash
openclaw setup --wizard
```

启动网关：

``` bash
openclaw gateway start
```

检查状态：

``` bash
openclaw status
```

------------------------------------------------------------------------

# Gateway

``` bash
openclaw gateway start
openclaw gateway status
openclaw gateway stop
```

------------------------------------------------------------------------

# Messaging

``` bash
openclaw message send --target +8613800138000 --message "你好"
```

Telegram：

``` bash
openclaw message send --channel telegram --target @mychat --message "Hello"
```

Discord：

``` bash
openclaw message send --channel discord --target channel:123456 --message "Hello"
```

发送媒体：

``` bash
openclaw message send --target +8613800138000 --message "看这个" --media ./image.jpg
```

------------------------------------------------------------------------

# Channels

查看频道：

``` bash
openclaw channels list
```

检查状态：

``` bash
openclaw channels status
```

添加 Telegram：

``` bash
openclaw channels add --channel telegram --token $TELEGRAM_BOT_TOKEN
```

登录 WhatsApp：

``` bash
openclaw channels login --channel whatsapp
```

------------------------------------------------------------------------

# Agent

``` bash
openclaw agent --message "帮我写一封邮件"
```

指定会话：

``` bash
openclaw agent --message "继续" --to +8613800138000
```

本地模式：

``` bash
openclaw agent --local --message "你好"
```

------------------------------------------------------------------------

# Models

``` bash
openclaw models list
openclaw models set claude-3-opus
openclaw models status
```

------------------------------------------------------------------------

# Cron Scheduler

``` bash
openclaw cron add --name "早间提醒" --cron "0 9 * * *" --system-event "早安"
openclaw cron list
openclaw cron run 1
```

------------------------------------------------------------------------

# Browser Automation

``` bash
openclaw browser start
openclaw browser open https://github.com
openclaw browser screenshot --full-page
openclaw browser snapshot
```

------------------------------------------------------------------------

# Node Control

``` bash
openclaw nodes list
openclaw nodes run --node my-mac -- ls
openclaw nodes location get --node my-phone
```

------------------------------------------------------------------------

# Memory System

工作空间：

    ~/.openclaw/workspace

    MEMORY.md
    memory/
      2026-03-10.md
      2026-03-09.md
    HEARTBEAT.md

------------------------------------------------------------------------

# Security

``` bash
openclaw security audit
openclaw security audit --deep
openclaw doctor
```

------------------------------------------------------------------------

# Maintenance

``` bash
openclaw update
openclaw backup create
openclaw reset --scope config
```

------------------------------------------------------------------------

# Global Options

  Option      Description
  ----------- -------------
  --dev       开发模式
  --profile   使用配置
  --json      JSON 输出
  --plain     纯文本输出

------------------------------------------------------------------------

# Contributing

欢迎贡献代码。

开发环境：

``` bash
npm install
npm run dev
```

流程：

    fork
    clone
    branch
    commit
    pull request

------------------------------------------------------------------------

# License

MIT License
