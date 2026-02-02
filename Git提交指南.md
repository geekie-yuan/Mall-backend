# Git 提交指南 - 登录日志优化

## 🎯 本次修改内容

增强了登录功能的日志记录，包括：
1. 添加异常处理和详细的日志记录
2. 区分账号不存在和密码错误的情况
3. 添加 JWT Token 的调试日志输出
4. 优化日志格式，使用【】标识便于搜索

---

## 📝 标准的 Git Commit Message

### 方式1：简洁版（推荐）

```bash
git add .
git commit -m "feat: 增强登录日志记录功能

- 添加登录过程的详细日志（尝试、成功、失败）
- 区分账号不存在和密码错误的日志输出
- 添加 JWT Token 的 DEBUG 级别日志
- 使用【】标识符优化日志格式便于搜索
- 修复密码错误时误显示账号不存在的问题"
```

### 方式2：详细版（更规范）

```bash
git add .
git commit -m "feat(auth): 增强登录功能的日志记录和异常处理

✨ 新增功能：
- 添加【登录尝试】【认证成功】【登录成功】日志
- 添加【JWT Token】调试日志，便于开发调试
- 使用【】标识符标记关键日志，便于搜索过滤

🐛 修复问题：
- 修复 BadCredentialsException 判断逻辑错误
- 修复密码错误时误显示为账号不存在的问题

♻️ 代码重构：
- 在异常处理中查询数据库区分账号和密码错误
- 优化日志输出格式和层次结构

📝 修改文件：
- AuthServiceImpl.java: login() 方法异常处理和日志记录

影响范围：登录功能
测试状态：已手动测试三种情况（账号不存在、密码错误、登录成功）"
```

---

## 🌟 Git Commit Message 标准格式

### 基本结构

```
<type>(<scope>): <subject>

<body>

<footer>
```

### Type 类型（必填）

| 类型 | 说明 | 示例 |
|------|------|------|
| `feat` | 新功能 | feat: 添加用户登录功能 |
| `fix` | Bug 修复 | fix: 修复登录时密码验证错误 |
| `docs` | 文档修改 | docs: 更新 API 文档 |
| `style` | 代码格式调整 | style: 格式化代码缩进 |
| `refactor` | 重构代码 | refactor: 重构登录逻辑 |
| `perf` | 性能优化 | perf: 优化数据库查询 |
| `test` | 测试相关 | test: 添加登录单元测试 |
| `chore` | 构建/工具链 | chore: 更新依赖版本 |

### Scope 范围（可选）

- `auth` - 认证相关
- `user` - 用户相关
- `product` - 商品相关
- `order` - 订单相关
- `cart` - 购物车相关

### Subject 主题（必填）

- 简短描述（50 字符以内）
- 动词开头，第一人称现在时
- 首字母小写
- 结尾不加句号

---

## 💡 本次修改的推荐 Commit Message

### 推荐方案1：单次提交

```bash
git add src/main/java/site/geekie/shop/shoppingmall/service/impl/AuthServiceImpl.java
git commit -m "feat(auth): 增强登录日志记录和异常处理

- 添加登录流程的详细日志输出（登录尝试、认证成功、登录成功）
- 区分账号不存在和密码错误两种失败情况的日志
- 添加 JWT Token 的 DEBUG 日志便于调试
- 使用【】标识符优化日志格式便于搜索和过滤
- 修复密码错误时误显示为账号不存在的逻辑问题

修改文件：AuthServiceImpl.java
影响功能：用户登录
测试情况：已验证三种场景（账号不存在、密码错误、成功登录）"
```

### 推荐方案2：分多次提交（更清晰）

```bash
# 第1次提交：添加日志记录
git add src/main/java/site/geekie/shop/shoppingmall/service/impl/AuthServiceImpl.java
git commit -m "feat(auth): 添加登录过程的详细日志记录

- 添加【登录尝试】【认证成功】【登录成功】日志
- 添加【登录失败】日志并包含失败原因
- 使用【】标识符便于日志搜索"

# 第2次提交：修复 bug
git add src/main/java/site/geekie/shop/shoppingmall/service/impl/AuthServiceImpl.java
git commit -m "fix(auth): 修复密码错误时误显示账号不存在的问题

- 在异常处理中查询数据库确认用户是否存在
- 正确区分账号不存在和密码错误两种情况"

# 第3次提交：添加调试功能
git add src/main/java/site/geekie/shop/shoppingmall/service/impl/AuthServiceImpl.java
git commit -m "feat(auth): 添加 JWT Token 的调试日志输出

- 在【登录成功】后添加 DEBUG 级别的 Token 日志
- 便于开发调试和问题排查"
```

---

## 🚀 完整的 Git 操作流程

### Step 1：查看修改状态

```bash
git status
```

### Step 2：查看具体修改内容

```bash
git diff src/main/java/site/geekie/shop/shoppingmall/service/impl/AuthServiceImpl.java
```

### Step 3：添加到暂存区

```bash
# 添加特定文件
git add src/main/java/site/geekie/shop/shoppingmall/service/impl/AuthServiceImpl.java

# 或添加所有修改
git add .
```

### Step 4：提交修改

```bash
git commit -m "feat(auth): 增强登录日志记录和异常处理

- 添加登录流程的详细日志输出
- 区分账号不存在和密码错误的日志
- 添加 JWT Token 的 DEBUG 日志
- 修复密码错误时误显示账号不存在的问题"
```

### Step 5：推送到远程仓库

```bash
git push origin main
# 或
git push origin master
```

---

## 📋 Commit Message 最佳实践

### ✅ 好的示例

```bash
# 清晰明了
feat(auth): 添加用户登录日志记录

# 详细说明
fix(auth): 修复密码验证错误
- 修复 BadCredentialsException 判断逻辑
- 通过查询数据库区分账号和密码错误

# 包含影响范围
refactor(auth): 重构登录异常处理逻辑
影响文件：AuthServiceImpl.java
影响功能：用户登录
```

### ❌ 不好的示例

```bash
# 太简单
git commit -m "修改"

# 太笼统
git commit -m "更新代码"

# 中英文混用不规范
git commit -m "fix bug修复登录"

# 没有说明影响
git commit -m "改了点东西"
```

---

## 🎯 本次推荐使用的命令

基于你的修改内容，推荐使用以下命令：

```bash
# 1. 查看修改
git status
git diff

# 2. 添加修改的文件
git add src/main/java/site/geekie/shop/shoppingmall/service/impl/AuthServiceImpl.java

# 3. 提交修改
git commit -m "feat(auth): 增强登录日志记录和异常处理

- 添加【登录尝试】【认证成功】【登录成功】【登录失败】日志
- 区分账号不存在和密码错误两种失败情况
- 添加 JWT Token 的 DEBUG 级别调试日志
- 使用【】标识符优化日志格式便于搜索
- 修复密码错误时误显示为账号不存在的逻辑问题

修改文件：AuthServiceImpl.java
影响功能：用户登录认证
测试状态：已验证（账号不存在、密码错误、登录成功三种场景）"

# 4. 推送到远程
git push origin main
```

---

## 📚 更多 Git 规范参考

### Conventional Commits 规范

参考：https://www.conventionalcommits.org/

基本格式：
```
<类型>[可选的作用域]: <描述>

[可选的正文]

[可选的脚注]
```

### Angular 规范

参考：https://github.com/angular/angular/blob/main/CONTRIBUTING.md

类型定义：
- `build`: 构建系统或外部依赖的更改
- `ci`: CI 配置文件和脚本的更改
- `docs`: 文档修改
- `feat`: 新功能
- `fix`: Bug 修复
- `perf`: 性能优化
- `refactor`: 代码重构
- `style`: 代码格式调整
- `test`: 测试相关

---

## ✨ 快速命令

```bash
# 一键提交（简化版）
git add . && git commit -m "feat(auth): 增强登录日志记录和异常处理" && git push

# 查看提交历史
git log --oneline

# 查看最近一次提交
git show

# 修改最近一次提交信息
git commit --amend -m "新的提交信息"
```
