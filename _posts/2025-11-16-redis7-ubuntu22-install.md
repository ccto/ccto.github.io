---
layout: post
title: "在 Ubuntu 22.04 上安装 Redis 7"
category: Redis
---

## 1. 更新系统
首先，更新系统包列表，确保所有系统包都是最新的：

```bash
sudo apt update && sudo apt upgrade -y
````

## 2. 添加 Redis 官方 PPA 仓库

### 2.1. 安装 `software-properties-common` 工具

Redis 7 版本可能不在 Ubuntu 官方仓库中，因此我们需要添加 Redis 官方的 PPA（Personal Package Archive）。首先，安装 `software-properties-common` 工具：

```bash
sudo apt install software-properties-common -y
```

### 2.2. 添加 Redis PPA 仓库

接着，添加 Redis 官方的仓库：

```bash
sudo add-apt-repository ppa:redislabs/redis
```

然后，更新包列表：

```bash
sudo apt update
```

## 3. 安装 Redis 7

现在，使用以下命令安装 Redis 7：

```bash
sudo apt install redis-server -y
```

## 4. 配置 Redis 允许远程连接（可选）

默认情况下，Redis 只允许从本地访问。若要允许远程连接，需修改配置文件。

### 4.1. 修改 Redis 配置文件

使用 `nano` 或其他文本编辑器打开 Redis 配置文件：

```bash
sudo nano /etc/redis/redis.conf
```

找到并修改以下两项：

* 修改 `bind` 配置，允许所有 IP 连接：

  ```bash
  bind 0.0.0.0 ::0
  ```

* 禁用 `protected-mode`，允许外部连接：

  ```bash
  protected-mode no
  ```

### 4.2. 设置 Redis 密码（可选）

为了安全性，建议设置密码。找到 `requirepass` 配置项并设置密码：

```bash
requirepass yourpassword
```

### 4.3. 重启 Redis 服务

配置更改后，重启 Redis 服务使其生效：

```bash
sudo systemctl restart redis-server
```

## 5. 设置 Redis 开机自启（可选）

如果你希望 Redis 在系统启动时自动启动，可以使用以下命令：

```bash
sudo systemctl enable redis-server
```

## 6. 验证 Redis 安装

### 6.1. 检查 Redis 服务状态

使用 `systemctl` 检查 Redis 服务是否正在运行：

```bash
sudo systemctl status redis-server
```

如果 Redis 正在运行，输出会显示如下：

```
Active: active (running) since Mon 2025-11-15 22:30:21 UTC; 1h 3min ago
```

### 6.2. 连接到 Redis

使用 `redis-cli` 客户端连接 Redis：

```bash
redis-cli
```

如果你设置了密码，可以通过以下命令进行验证：

```bash
redis-cli -a yourpassword
```

### 6.3. 测试连接

在 `redis-cli` 中，输入 `ping` 命令。如果 Redis 正常运行，你应该收到 `PONG` 响应：

```bash
ping
```

---

## 7. 卸载 Redis（可选）

如果你需要卸载 Redis，可以使用以下命令：

```bash
sudo apt purge redis-server -y
```

然后删除 Redis 配置文件和数据：

```bash
sudo rm -rf /etc/redis
sudo rm -rf /var/lib/redis
```

---

## 总结

* 通过 PPA 仓库安装 Redis 7。
* 配置 Redis 允许远程连接并设置密码（如果需要）。
* 使用 `redis-cli` 测试连接。
* 配置 Redis 开机自动启动（可选）。

如果你遇到任何问题或有其他问题，随时告诉我！


