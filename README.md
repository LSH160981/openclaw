# openclaw-

初始化与配置
命令	说明
openclaw setup	初始化配置和工作空间
openclaw configure	交互式配置向导（模型、频道、技能、网关）
openclaw onboard	完整入门向导（网关 + 工作空间 + 技能）
openclaw doctor	健康检查 + 自动修复配置问题
openclaw status	查看会话状态、频道健康、最近联系人
openclaw dashboard	打开 Control UI 控制面板
setup 选项
openclaw setup --workspace <目录>     # 指定工作空间路径
openclaw setup --wizard               # 运行配置向导
openclaw setup --non-interactive      # 非交互模式
openclaw setup --mode local|remote    # 本地或远程模式
openclaw setup --remote-url <URL>     # 远程网关地址
openclaw setup --remote-token <令牌>  # 远程网关令牌
onboard 选项
openclaw onboard --reset              # 重置后运行向导
openclaw onboard --flow quickstart    # 快速开始模式
openclaw onboard --flow advanced      # 高级模式
openclaw onboard --gateway-port 18789 # 指定网关端口
openclaw onboard --install-daemon     # 安装为系统服务
Gateway 网关服务
基本命令
命令	说明
openclaw gateway	启动 WebSocket 网关（前台运行）
openclaw gateway status	查看网关状态（默认探测 RPC）
openclaw gateway start	启动网关服务（后台）
openclaw gateway stop	停止网关服务
openclaw gateway restart	重启网关服务
openclaw gateway install	安装为系统服务
openclaw gateway uninstall	卸载系统服务
启动参数
openclaw gateway --port 18789              # 指定端口
openclaw gateway --bind lan                # 绑定地址：loopback|lan|tailnet|auto|custom
openclaw gateway --token <令牌>            # 认证令牌
openclaw gateway --auth token|password     # 认证方式
openclaw gateway --password <密码>         # 密码认证
openclaw gateway --force                   # 强制终止占用端口的进程
openclaw gateway --dev                     # 开发模式
openclaw gateway --verbose                 # 详细日志
openclaw gateway --tailscale serve|funnel  # Tailscale 暴露
日志查看
openclaw logs                  # 查看网关日志
openclaw logs --follow         # 实时跟踪日志
openclaw logs --limit 500      # 限制行数
openclaw logs --json           # JSON 格式输出
openclaw logs --plain          # 纯文本输出
RPC 调用
openclaw gateway call <方法> [--params '<JSON>']   # 调用 RPC 方法
openclaw gateway health                           # 获取健康状态
openclaw gateway probe                            # 探测网关
openclaw gateway discover                         # 发现网关
消息与会话
发送消息
# 基本发送
openclaw message send --target <目标> --message "内容"

# 指定频道
openclaw message send --channel whatsapp --target +8613800138000 --message "你好"
openclaw message send --channel telegram --target @mychat --message "Hi"
openclaw message send --channel discord --target channel:123456 --message "Hello"

# 发送媒体
openclaw message send --target +8613800138000 --message "看这个" --media /path/to/image.jpg
消息子命令
命令	说明
openclaw message send	发送消息
openclaw message poll	发送投票
openclaw message react	添加反应表情
openclaw message read	标记已读
openclaw message edit	编辑消息
openclaw message delete	删除消息
openclaw message pin	置顶消息
openclaw message search	搜索消息
openclaw message thread create	创建话题
openclaw message thread list	列出话题
会话管理
openclaw sessions                    # 列出所有会话
openclaw sessions --active 60        # 最近60分钟活跃的会话
openclaw sessions --json             # JSON 格式输出
Agent 对话
# 通过网关与 Agent 对话
openclaw agent --message "帮我总结今天的新闻"

# 指定会话
openclaw agent --message "继续" --to +8613800138000

# 本地模式
openclaw agent --message "你好" --local

# 直接发送回复
openclaw agent --message "总结" --to +8613800138000 --deliver
频道管理
基本命令
命令	说明
openclaw channels list	列出已配置的频道和账号
openclaw channels status	检查频道连接状态
openclaw channels logs	查看频道日志
openclaw channels add	添加频道账号
openclaw channels remove	移除频道账号
openclaw channels login	登录频道（扫码）
openclaw channels logout	登出频道
支持的频道
whatsapp - WhatsApp
telegram - Telegram
discord - Discord
slack - Slack
signal - Signal
imessage - iMessage
googlechat - Google Chat
msteams - Microsoft Teams
mattermost - Mattermost（插件）
添加频道示例
# Telegram Bot
openclaw channels add --channel telegram --token $TELEGRAM_BOT_TOKEN

# Discord Bot
openclaw channels add --channel discord --account work --name "Work Bot" --token $DISCORD_BOT_TOKEN

# WhatsApp（扫码登录）
openclaw channels login --channel whatsapp

# 多账号
openclaw channels add --channel telegram --account alerts --name "Alerts Bot" --token $TOKEN
频道状态检查
openclaw channels status            # 基本状态
openclaw channels status --probe    # 深度检查
openclaw channels list --json       # JSON 输出
模型配置
查看与设置
命令	说明
openclaw models list	列出可用模型
openclaw models status	查看模型配置和认证状态
openclaw models set <模型ID>	设置默认主模型
openclaw models set-image <模型ID>	设置图像模型
openclaw models scan	扫描并推荐最佳模型
模型别名
openclaw models aliases list                 # 列出别名
openclaw models aliases add <别名> <模型ID>  # 添加别名
openclaw models aliases remove <别名>        # 删除别名
回退模型
openclaw models fallbacks list               # 列出回退模型
openclaw models fallbacks add <模型ID>       # 添加回退模型
openclaw models fallbacks remove <模型ID>    # 删除回退模型
openclaw models fallbacks clear              # 清空回退列表
认证管理
openclaw models auth add                     # 交互式添加认证
openclaw models auth setup-token             # 使用 setup-token（Anthropic）
openclaw models auth paste-token             # 粘贴令牌
查看使用量
openclaw status --usage                      # 显示模型提供商用量/配额
openclaw models status --probe               # 实时探测模型状态
定时任务
任务管理
命令	说明
openclaw cron status	查看调度器状态
openclaw cron list	列出所有定时任务
openclaw cron add	添加定时任务
openclaw cron edit <ID>	编辑任务
openclaw cron rm <ID>	删除任务
openclaw cron enable <ID>	启用任务
openclaw cron disable <ID>	禁用任务
openclaw cron run <ID>	立即执行任务
openclaw cron runs --id <ID>	查看执行历史
添加任务示例
# 每小时提醒
openclaw cron add --name "每小时提醒" --every 1h --system-event "该休息一下了"

# 指定时间执行
openclaw cron add --name "早间提醒" --at "2026-03-10T09:00:00" --system-event "早安！新的一天开始了"

# Cron 表达式
openclaw cron add --name "工作日早间" --cron "0 9 * * 1-5" --system-event "开始工作"

# 发送消息任务
openclaw cron add --name "日报提醒" --cron "0 18 * * *" --message "记得写日报"
记忆系统
命令
命令	说明
openclaw memory status	查看记忆索引状态
openclaw memory index	重建记忆索引
openclaw memory search "<查询>"	语义搜索记忆
示例
# 搜索记忆
openclaw memory search "上次讨论的项目"

# 重建索引
openclaw memory index

# 查看状态
openclaw memory status --json
记忆文件结构
~/.openclaw/workspace/
├── MEMORY.md          # 长期记忆（手动维护）
├── memory/
│   ├── 2026-03-10.md  # 每日记录
│   └── 2026-03-09.md
└── HEARTBEAT.md       # 心跳任务
配置管理
基本命令
命令	说明
openclaw config	启动配置向导（无子命令时）
openclaw config get <路径>	获取配置值
openclaw config set <路径> <值>	设置配置值
openclaw config unset <路径>	删除配置值
openclaw config file	显示配置文件路径
openclaw config validate	验证配置
示例
# 获取配置
openclaw config get agents.defaults.model.primary
openclaw config get gateway.port
openclaw config get channels.telegram.accounts.default.token

# 设置配置
openclaw config set agents.defaults.model.primary "claude-3-opus"
openclaw config set gateway.port 18789

# 删除配置
openclaw config unset agents.defaults.thinking

# 验证配置
openclaw config validate
配置路径示例
agents.defaults.model.primary       # 主模型
agents.defaults.thinking            # 思考模式
agents.defaults.timeoutSeconds      # 超时时间
gateway.port                        # 网关端口
gateway.auth.token                  # 网关令牌
channels.telegram.enabled           # Telegram 启用状态
技能系统
命令
命令	说明
openclaw skills list	列出可用技能
openclaw skills info <名称>	查看技能详情
openclaw skills check	检查技能依赖状态
示例
# 列出技能
openclaw skills list

# 只显示就绪的技能
openclaw skills list --eligible

# 查看详情
openclaw skills info weather

# 检查依赖
openclaw skills check --verbose
安装技能
# 使用 clawhub 搜索和安装技能
npx clawhub
安全与诊断
安全审计
openclaw security audit              # 基本审计
openclaw security audit --deep       # 深度审计（包括网关探测）
openclaw security audit --fix        # 自动修复安全问题
健康检查
openclaw health                      # 获取网关健康状态
openclaw health --json               # JSON 输出
openclaw doctor                      # 快速诊断
openclaw doctor --deep               # 深度诊断
openclaw doctor --yes                # 自动接受默认修复
密钥管理
openclaw secrets reload              # 重新加载密钥引用
openclaw secrets audit               # 审计密钥安全
浏览器控制
管理命令
命令	说明
openclaw browser status	浏览器状态
openclaw browser start	启动浏览器
openclaw browser stop	停止浏览器
openclaw browser tabs	列出标签页
openclaw browser open <URL>	打开网页
openclaw browser close [ID]	关闭标签页
openclaw browser profiles	列出配置文件
检查命令
命令	说明
openclaw browser screenshot	截图
openclaw browser snapshot	获取页面结构（ARIA/AI 格式）
操作命令
命令	说明
openclaw browser navigate <URL>	导航到 URL
openclaw browser click <ref>	点击元素
openclaw browser type <ref> <文本>	输入文本
openclaw browser press <键>	按键
openclaw browser hover <ref>	悬停
openclaw browser drag <start> <end>	拖拽
openclaw browser select <ref> <值>	选择
openclaw browser upload <文件>	上传文件
openclaw browser fill --fields '<JSON>'	填充表单
openclaw browser wait --time <ms>	等待
openclaw browser evaluate --fn '<代码>'	执行 JavaScript
示例
# 打开网页
openclaw browser open https://example.com

# 截图
openclaw browser screenshot --full-page

# 获取页面结构
openclaw browser snapshot --format aria

# 点击元素
openclaw browser click e123

# 输入文本
openclaw browser type e456 "Hello World" --submit
节点管理
设备配对
openclaw devices list                # 列出已配对设备
openclaw devices approve <请求ID>    # 批准配对请求
openclaw devices reject <请求ID>     # 拒绝配对请求
openclaw devices remove <设备ID>     # 移除设备
节点操作
openclaw nodes status                # 节点状态
openclaw nodes list                  # 列出节点
openclaw nodes describe --node <ID>  # 节点详情

# 远程执行命令
openclaw nodes run --node <ID> ls -la

# 发送通知
openclaw nodes notify --node <ID> --title "提醒" --body "内容"

# 获取位置
openclaw nodes location get --node <ID>
相机操作
openclaw nodes camera list --node <ID>
openclaw nodes camera snap --node <ID> --facing front
openclaw nodes camera clip --node <ID> --duration 10s
屏幕录制
openclaw nodes screen record --node <ID> --duration 30s --fps 30
Canvas 操作
openclaw nodes canvas snapshot --node <ID>
openclaw nodes canvas present --node <ID> --target https://example.com
openclaw nodes canvas hide --node <ID>
更新与维护
更新
openclaw update                      # 更新 OpenClaw
openclaw update --check              # 检查更新
备份
openclaw backup create               # 创建备份
openclaw backup verify <文件>        # 验证备份
重置
openclaw reset                       # 重置配置（保留 CLI）
openclaw reset --scope config        # 只重置配置
openclaw reset --scope config+creds+sessions  # 重置配置+凭证+会话
openclaw reset --scope full          # 完全重置
卸载
openclaw uninstall                   # 卸载网关服务和数据
openclaw uninstall --all             # 完全卸载
全局参数
参数	说明
--dev	开发模式（状态隔离到 ~/.openclaw-dev）
--profile <名称>	使用命名配置文件
--no-color	禁用彩色输出
--log-level <级别>	日志级别：silent
-V, --version	显示版本号
-h, --help	显示帮助
输出格式
参数	说明
--json	JSON 格式输出
--plain	纯文本输出
常用场景示例
场景1：首次安装
# 安装后初始化
openclaw setup --wizard

# 配置模型
openclaw configure

# 安装为服务
openclaw gateway install

# 启动服务
openclaw gateway start
场景2：连接 Telegram
# 添加 Telegram Bot
openclaw channels add --channel telegram --token $TELEGRAM_BOT_TOKEN

# 检查状态
openclaw channels status --probe

# 发送测试消息
openclaw message send --channel telegram --target @mychat --message "测试"
场景3：连接 WhatsApp
# 登录 WhatsApp
openclaw channels login --channel whatsapp

# 扫描二维码后检查状态
openclaw channels status

# 发送消息
openclaw message send --target +8613800138000 --message "你好"
场景4：设置定时提醒
# 每天早上9点提醒
openclaw cron add --name "早间提醒" --cron "0 9 * * *" --system-event "早安！新的一天开始了"

# 工作日下班提醒
openclaw cron add --name "下班提醒" --cron "0 18 * * 1-5" --system-event "该下班了，记得写日报"

# 查看任务
openclaw cron list
场景5：切换模型
# 查看可用模型
openclaw models list

# 设置默认模型
openclaw models set claude-3-opus

# 验证
openclaw models status
场景6：远程节点控制
# 查看已配对节点
openclaw nodes list

# 远程执行命令
openclaw nodes run --node my-mac -- open -a "Safari"

# 获取位置
openclaw nodes location get --node my-iphone
场景7：浏览器自动化
# 启动浏览器
openclaw browser start

# 打开网页
openclaw browser open https://github.com

# 获取页面结构
openclaw browser snapshot --format aria

# 截图
openclaw browser screenshot --full-page

# 关闭
openclaw browser stop
