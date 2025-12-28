# Claude Relay Service 部署指南

让团队成员共享 Claude Code 订阅。

## 部署方式选择

| 方式 | 适用场景 | 国内访问 | 稳定性 | 成本 |
|------|----------|----------|--------|------|
| [VPS 部署](#vps-部署推荐) | 国内用户为主 | ✅ 无需翻墙 | ⭐⭐⭐⭐⭐ | ~60元/月 |
| [Zeabur 部署](#zeabur-部署) | 快速体验 | ⚠️ 可能不稳定 | ⭐⭐⭐ | ~$8/月 |
| [Docker 镜像](#docker-镜像部署) | 自有服务器 | 取决于服务器 | ⭐⭐⭐⭐ | - |

---

## VPS 部署（推荐）

使用 **香港 VPS + 美国代理** 方案，国内用户无需翻墙即可访问。

### 架构

```
国内用户 ──→ 香港VPS ──→ 美国代理 ──→ Anthropic API
(不用翻墙)   (主服务)    (代理出口)
```

### 一键部署

#### 1. 部署代理服务器（美国/日本 VPS）

```bash
curl -fsSL https://raw.githubusercontent.com/JessyTsui/ai-coding-kit/master/deploy/claude-relay-service/scripts/install-proxy.sh | sudo bash
```

#### 2. 部署主服务（香港 VPS）

```bash
curl -fsSL https://raw.githubusercontent.com/JessyTsui/ai-coding-kit/master/deploy/claude-relay-service/scripts/install-relay-service.sh | sudo bash
```

**详细文档**: [VPS-DEPLOY.md](./VPS-DEPLOY.md)

---

## Zeabur 部署

适合快速体验，但国内访问可能不稳定。

### 步骤

1. 访问 [Zeabur](https://zeabur.com) → **Create Project** → 选择 **Hong Kong**
2. **Add Service** → **Prebuilt Image** → 输入 `weishaw/claude-relay-service:latest`
3. **Add Service** → **Marketplace** → 选择 **Redis**
4. 配置环境变量：

| 变量名 | 值 |
|--------|-----|
| `JWT_SECRET` | [生成](https://generate-secret.vercel.app/32) |
| `ENCRYPTION_KEY` | [生成](https://generate-secret.vercel.app/32) |
| `REDIS_HOST` | `${REDIS_HOST}` |
| `REDIS_PORT` | `${REDIS_PORT}` |
| `REDIS_PASSWORD` | `${REDIS_PASSWORD}` |

5. **Networking** → **Domain** → 获取域名

---

## Docker 镜像部署

适合自有服务器。

```bash
docker run -d \
  --name claude-relay \
  -p 3000:3000 \
  -e JWT_SECRET=your-secret-key \
  -e ENCRYPTION_KEY=your-32-char-key \
  -e REDIS_HOST=your-redis-host \
  -e REDIS_PORT=6379 \
  -e REDIS_PASSWORD=your-redis-pass \
  weishaw/claude-relay-service:latest
```

---

## 部署后配置

### 1. 访问管理界面

```
http://你的服务器IP:3000/admin-next/
```

### 2. 获取管理员密码

```bash
docker exec claude-relay-service cat /app/data/init.json
```

### 3. 添加 Claude 账户

1. 登录管理界面
2. Claude 账户 → 添加账户
3. 选择 **Access Token** 方式（推荐）
4. **重要**：配置代理信息

### 4. 创建 API Key

API Keys → 创建 → 记录 Key（格式：`cr_xxx`）

---

## 用户使用

```bash
# Linux/macOS
export ANTHROPIC_BASE_URL="http://你的服务器/api/"
export ANTHROPIC_AUTH_TOKEN="cr_你的api_key"

# 使用 Claude Code
claude
```

---

## 相关链接

- [Claude Relay Service 源码](https://github.com/Wei-Shaw/claude-relay-service)
- [Docker Hub 镜像](https://hub.docker.com/r/weishaw/claude-relay-service)
