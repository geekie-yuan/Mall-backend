# ⚡ Git 提交快速参考

## 🎯 本次修改推荐的 Git 命令

### 最推荐（规范且清晰）

```bash
git add src/main/java/site/geekie/shop/shoppingmall/service/impl/AuthServiceImpl.java

git commit -m "feat(auth): 增强登录日志记录和异常处理

- 添加【登录尝试】【认证成功】【登录成功】【登录失败】日志
- 区分账号不存在和密码错误两种失败情况
- 添加 JWT Token 的 DEBUG 级别调试日志
- 使用【】标识符优化日志格式便于搜索
- 修复密码错误时误显示为账号不存在的逻辑问题"

git push origin main
```

---

## 📝 Commit Message 格式

### 标准格式

```
<type>(<scope>): <subject>

<body>
```

### 类型（type）

| 类型 | 说明 | 示例 |
|------|------|------|
| `feat` | 新功能 | feat(auth): 添加登录日志 |
| `fix` | Bug 修复 | fix(auth): 修复密码验证 |
| `docs` | 文档 | docs: 更新 README |
| `refactor` | 重构 | refactor(auth): 重构登录 |
| `perf` | 性能优化 | perf: 优化查询 |
| `test` | 测试 | test: 添加单元测试 |
| `chore` | 构建/工具 | chore: 更新依赖 |

### 作用域（scope）

- `auth` - 认证相关
- `user` - 用户相关
- `product` - 商品
- `order` - 订单
- `cart` - 购物车

---

## 🚀 完整操作流程

```bash
# 1. 查看修改
git status
git diff

# 2. 添加文件
git add src/main/java/site/geekie/shop/shoppingmall/service/impl/AuthServiceImpl.java

# 3. 提交
git commit -m "feat(auth): 增强登录日志记录和异常处理

- 添加详细的登录流程日志
- 区分账号不存在和密码错误
- 添加 JWT Token 调试日志
- 修复逻辑判断问题"

# 4. 推送
git push origin main
```

---

## 💡 其他常用命令

```bash
# 查看提交历史
git log --oneline

# 修改最近一次提交
git commit --amend

# 撤销 add
git reset HEAD <file>

# 撤销修改
git checkout -- <file>
```

---

## ✅ Commit Message 规范

### 好的示例 ✓

```
feat(auth): 添加登录日志记录
fix(auth): 修复密码验证错误
docs: 更新 API 文档
```

### 不好的示例 ✗

```
更新
修改代码
fix bug
改了点东西
```

---

## 🎯 本次修改的关键点

```
类型：feat（新功能）+ fix（修复）
范围：auth（认证）
主题：增强登录日志记录和异常处理

主要修改：
1. 添加日志 → feat
2. 修复判断逻辑 → fix
3. 添加调试功能 → feat
```

建议合并为一个 commit，类型使用 `feat`，在 body 中说明包含 bug 修复。
