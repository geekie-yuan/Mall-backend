# ⚡ JWT Token 打印 - 快速指南

## ✅ 已完成

在 `AuthServiceImpl.java` 第 159 行添加了 JWT Token 打印功能。

```java
log.info("【登录成功】用户名: {}，JWT Token 已生成", request.getUsername());
// 打印生成的JWT Token（用于调试）
log.debug("【JWT Token】{}", token);
```

---

## 🚀 应用更新

```
Ctrl + F9   编译
Ctrl + F2   停止
Shift + F10 启动
```

---

## 📊 查看 Token

### 登录成功后的日志示例

```
INFO  【登录尝试】用户名: user
INFO  【认证成功】用户名: user
INFO  【登录成功】用户名: user，JWT Token 已生成
DEBUG 【JWT Token】eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiJ1c2VyIiwiaWF0IjoxNzAzMDUwODAwLCJleHAiOjE3MDMxMzcyMDB9.xYzAbC...
```

**注意**：JWT Token 现在打印在【登录成功】之后，日志顺序更合理。

---

## 💡 三种获取 Token 的方式

### 方式1️⃣：从日志复制
```
IDEA Run 窗口 → 搜索 "【JWT Token】" → 复制整个 Token
```

### 方式2️⃣：从响应体获取
```json
POST /api/v1/auth/login
响应：
{
  "code": 200,
  "message": "success",
  "data": {
    "token": "eyJhbGciOiJIUzI1NiIs...",  ← Token 在这里
    "user": {...}
  }
}
```

### 方式3️⃣：Postman 中查看
1. 发送登录请求
2. 响应中的 `data.token` 就是 JWT Token

---

## 🔍 解析 Token 内容

### 在线工具
访问 **https://jwt.io**，粘贴 Token 可以看到：

```
eyJhbGci...  .  eyJzdWIi...  .  xYzAbC...
    ↓              ↓              ↓
  Header        Payload       Signature
```

### Token 包含的信息
```json
Header:
{
  "alg": "HS256",  // 签名算法
  "typ": "JWT"     // Token 类型
}

Payload:
{
  "sub": "user",        // 用户名
  "iat": 1703050800,    // 颁发时间
  "exp": 1703137200     // 过期时间
}
```

---

## 🎯 使用 Token 测试 API

### 在 Postman 中
```
Headers:
  Authorization: Bearer eyJhbGciOiJIUzI1NiIs...
```

### 用 curl 命令
```bash
curl -H "Authorization: Bearer eyJhbGciOiJIUzI1NiIs..." \
     http://localhost:8080/api/v1/user/profile
```

---

## 📝 代码位置

**文件**：`AuthServiceImpl.java`  
**行号**：第 158-159 行  
**日志级别**：DEBUG

```java
log.info("【登录成功】用户名: {}，JWT Token 已生成", request.getUsername());
log.debug("【JWT Token】{}", token);
```

---

## ✨ 完成

✅ JWT Token 现在打印在【登录成功】之后  
✅ 日志格式更简洁：`【JWT Token】eyJhbGci...`  
✅ 便于复制整个 Token 字符串
