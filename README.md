# OpenClaw  
# 初始化与配置
```
  命令                   说明
  ---------------------- ----------------------
  `openclaw setup`       初始化配置和工作空间
  `openclaw configure`   交互式配置向导
  `openclaw onboard`     完整入门向导
  `openclaw doctor`      健康检查
  `openclaw status`      查看系统状态
  `openclaw dashboard`   打开控制面板
```
## setup 选项

``` bash
openclaw setup --workspace <目录>
openclaw setup --wizard
openclaw setup --non-interactive
openclaw setup --mode local|remote
openclaw setup --remote-url <URL>
openclaw setup --remote-token <令牌>
```

## onboard 选项

``` bash
openclaw onboard --reset
openclaw onboard --flow quickstart
openclaw onboard --flow advanced
openclaw onboard --gateway-port 18789
openclaw onboard --install-daemon
```

------------------------------------------------------------------------

# Gateway 网关
```
## 基本命令

  命令                           说明
  ------------------------------ ------------
  `openclaw gateway`             前台启动
  `openclaw gateway start`       后台启动
  `openclaw gateway stop`        停止
  `openclaw gateway restart`     重启
  `openclaw gateway status`      查看状态
  `openclaw gateway install`     安装为服务
  `openclaw gateway uninstall`   卸载服务
```
## 启动参数

``` bash
openclaw gateway --port 18789
openclaw gateway --bind lan
openclaw gateway --token <TOKEN>
openclaw gateway --auth token
openclaw gateway --password <PASSWORD>
openclaw gateway --force
openclaw gateway --dev
openclaw gateway --verbose
openclaw gateway --tailscale serve
```

## 日志

``` bash
openclaw logs
openclaw logs --follow
openclaw logs --limit 500
openclaw logs --json
openclaw logs --plain
```

## RPC 调用

``` bash
openclaw gateway call <method> --params '<JSON>'
openclaw gateway health
openclaw gateway probe
openclaw gateway discover
```

------------------------------------------------------------------------

# 消息与会话

## 发送消息

``` bash
openclaw message send --target <目标> --message "内容"
```

### 指定频道

``` bash
openclaw message send --channel whatsapp --target +8613800138000 --message "你好"

openclaw message send --channel telegram --target @mychat --message "Hi"

openclaw message send --channel discord --target channel:123456 --message "Hello"
```

### 发送媒体

``` bash
openclaw message send \
--target +8613800138000 \
--message "看这个" \
--media /path/to/image.jpg
```

------------------------------------------------------------------------

## 消息子命令
```
  命令                      说明
  ------------------------- ----------
  `message send`            发送消息
  `message poll`            投票
  `message react`           添加表情
  `message read`            标记已读
  `message edit`            编辑
  `message delete`          删除
  `message pin`             置顶
  `message search`          搜索
  `message thread create`   创建话题
  `message thread list`     列出话题
```
------------------------------------------------------------------------

# Agent 对话

``` bash
openclaw agent --message "帮我总结今天的新闻"
```

指定会话

``` bash
openclaw agent --message "继续" --to +8613800138000
```

本地模式

``` bash
openclaw agent --message "你好" --local
```

直接回复

``` bash
openclaw agent \
--message "总结" \
--to +8613800138000 \
--deliver
```

------------------------------------------------------------------------

# 频道管理

## 基本命令
```
  命令                说明
  ------------------- ----------
  `channels list`     列出频道
  `channels status`   查看状态
  `channels logs`     查看日志
  `channels add`      添加账号
  `channels remove`   删除账号
  `channels login`    登录
  `channels logout`   登出
```
------------------------------------------------------------------------

## 支持频道

-   WhatsApp
-   Telegram
-   Discord
-   Slack
-   Signal
-   iMessage
-   Google Chat
-   Microsoft Teams
-   Mattermost

------------------------------------------------------------------------

## 添加频道示例

### Telegram

``` bash
openclaw channels add \
--channel telegram \
--token $TELEGRAM_BOT_TOKEN
```

### Discord

``` bash
openclaw channels add \
--channel discord \
--account work \
--name "Work Bot" \
--token $DISCORD_BOT_TOKEN
```

### WhatsApp

``` bash
openclaw channels login --channel whatsapp
```

------------------------------------------------------------------------

# 模型配置
```
  命令                 说明
  -------------------- --------------
  `models list`        查看模型
  `models status`      查看状态
  `models set`         设置主模型
  `models set-image`   设置图像模型
  `models scan`        推荐模型
```
------------------------------------------------------------------------

# 定时任务

## 任务管理
```
  命令             说明
  ---------------- ----------
  `cron list`      查看任务
  `cron add`       添加任务
  `cron edit`      编辑
  `cron rm`        删除
  `cron enable`    启用
  `cron disable`   禁用
  `cron run`       立即执行
```
### 示例

``` bash
openclaw cron add \
--name "每小时提醒" \
--every 1h \
--system-event "该休息一下了"
```

``` bash
openclaw cron add \
--name "工作日早间" \
--cron "0 9 * * 1-5" \
--system-event "开始工作"
```

------------------------------------------------------------------------

# 记忆系统

``` bash
openclaw memory status
openclaw memory index
openclaw memory search "上次讨论的项目"
```

------------------------------------------------------------------------

# 浏览器自动化

``` bash
openclaw browser start
openclaw browser open https://example.com
openclaw browser snapshot --format aria
openclaw browser screenshot --full-page
openclaw browser stop
```

------------------------------------------------------------------------

# 节点管理

``` bash
openclaw devices list
openclaw devices approve <id>
openclaw devices reject <id>
openclaw devices remove <id>
```

远程执行

``` bash
openclaw nodes run --node my-mac ls -la
```

------------------------------------------------------------------------

# 更新与维护

``` bash
openclaw update
openclaw update --check
```

``` bash
openclaw backup create
openclaw backup verify <file>
```

``` bash
openclaw reset
openclaw reset --scope config
openclaw reset --scope full
```

``` bash
openclaw uninstall
openclaw uninstall --all
```

------------------------------------------------------------------------

# 常见场景

## 首次安装

``` bash
openclaw setup --wizard
openclaw configure
openclaw gateway install
openclaw gateway start
```

## Telegram

``` bash
openclaw channels add \
--channel telegram \
--token $TELEGRAM_BOT_TOKEN
```

## WhatsApp

``` bash
openclaw channels login --channel whatsapp
```

------------------------------------------------------------------------

# License

MIT
