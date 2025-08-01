# Titan Node 自动机器人

一个用于自动连接 Titan Network 扩展程序以赚取积分的 Python 机器人，支持多账户和代理功能。

## 功能特点

- 🚀 支持多账户同时运行
- 🚀 支持单账户多ip
- 🌐 支持代理服务器
- ⏰ 实时时间戳显示
- 📊 自动积分更新显示
- 🔄 自动重连机制
- 📝 详细的日志记录

## 安装要求

- Python 3.7+
- 必需的 Python 包：
  ```bash
  pip install aiohttp asyncio uuid pytz
  ```

## 注册账户

1. 访问注册地址：[https://edge.titannet.info/signup?inviteCode=JBK7C5U4](https://edge.titannet.info/signup?inviteCode=JBK7C5U4)
2. 完成账户注册
3. 登录到您的账户

## 获取 Token

### 方法一：通过浏览器开发者工具

1. 在 Chrome 浏览器中登录您的 Titan Network 账户
2. 按 `F12` 打开开发者工具
3. 点击 `应用` (Application) 标签
4. 在左侧菜单中找到 `本地存储空间` (Local Storage)
5. 点击您的网站域名
6. 找到 `login-info` 项目
7. 复制其中 JSON 数据里的 `refresh_token` 值

### 示例
```json
{
  "access_token": "...",
  "refresh_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
  "user_id": "..."
}
```

复制 `refresh_token` 的完整值（通常是一个很长的字符串）。

## 配置文件

### 1. 创建 token.txt 文件
在config目录创建 `token.txt` 文件，每行放一个 refresh_token：

```
eyJhb....
eyJhbG...
```

### 2. 创建 proxies.txt 文件（可选）
如果您想使用代理，在config目录创建 `proxy.txt` 文件，每行一个代理：

```
http://username:password@proxy1.example.com:8080
http://username:password@proxy2.example.com:8080
socks5://username:password@proxy3.example.com:1080
```

## 使用方法

### 基本使用
懒得写

## 日志输出示例

```
[14:30:25] 找到 2 个令牌.
[14:30:25] 找到 2 个代理.
[14:30:25] 令牌 1 将使用代理: http://proxy1.example.com:8080
[14:30:25] 令牌 2 将使用代理: http://proxy2.example.com:8080
[14:30:35][账户1][代理] 使用代理: http://proxy1.example.com:8080
[14:30:35][账户1][步骤] 使用设备ID: 12345678-1234-1234-1234-123456789abc
[14:30:35][账户1][加载] 正在尝试刷新访问令牌...
[14:30:36][账户1][信息] 令牌刷新状态: 200
[14:30:36][账户1][成功] 访问令牌刷新成功!
[14:30:36][账户1][信息] 用户ID: d1vn6336a33c73a825r0
[14:30:37][账户1][加载] 正在注册节点...
[14:30:38][账户1][成功] 节点注册成功.
[14:30:38][账户1][信息] 初始积分: {"today_points": 0, "total_points": 1250}
[14:30:38][账户1][加载] 正在连接到WebSocket...
[14:30:39][账户1][成功] WebSocket连接已建立. 等待任务...
[14:31:15][账户1][积分] 积分更新 - 今日: 5, 总计: 1255
```

## 文件结构

```
TitanNode/
├── bot              # 主程序文件
├── config/token.txt           # 存放 refresh_token（必需）
├── config/proxies.txt         # 存放代理列表（可选）
└── README.md           # 说明文档
```

## 注意事项

1. **Token 安全**：请妥善保管您的 refresh_token，不要泄露给他人
2. **代理配置**：如果使用代理，确保代理服务器稳定可用
3. **网络连接**：程序需要稳定的网络连接来维持 WebSocket 连接
4. **多账户**：每个账户会自动分配一个唯一的设备ID
5. **重连机制**：程序会自动处理连接断开并尝试重连

## 故障排除

### 常见问题

1. **Token 无效**
   - 检查 token.txt 文件格式是否正确
   - 确认 refresh_token 是否已过期
   - 重新获取 refresh_token

2. **代理连接失败**
   - 检查代理服务器是否可用
   - 验证代理格式是否正确
   - 尝试不使用代理运行

3. **WebSocket 连接失败**
   - 检查网络连接
   - 确认防火墙设置
   - 尝试更换网络环境

## 许可证

本项目仅供学习和研究使用，请遵守相关服务条款。

## 免责声明

使用本工具的风险由用户自行承担。开发者不对任何损失或问题负责。
