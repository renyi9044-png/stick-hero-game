# 🎮 棍子英雄 - GitHub Pages 部署指南

## 部署步骤

### 1. 创建 GitHub 仓库

1. 打开 https://github.com/new
2. 仓库名：`stick-hero-game`
3. 设为 **Public**
4. 点击 **Create repository**

### 2. 上传游戏文件

**方法 A：网页上传（推荐）**
1. 进入刚创建的仓库
2. 点击 **uploading an existing file**
3. 把 `index.html` 拖进去
4. 点击 **Commit changes**

**方法 B：使用 Git 命令**
```bash
cd C:\Users\Admin\.openclaw\workspace\games\douyin\stick-hero
git init
git add index.html
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/renyi9044-png/stick-hero-game.git
git push -u origin main
```

### 3. 启用 GitHub Pages

1. 进入仓库 **Settings**
2. 左侧菜单点击 **Pages**
3. **Source** 选择 `Deploy from a branch`
4. **Branch** 选择 `main`，文件夹选 `/ (root)`
5. 点击 **Save**

### 4. 访问游戏

等待 1-2 分钟后，游戏将在以下地址可用：

```
https://renyi9044-png.github.io/stick-hero-game/
```

---

## ✅ 优点

- **永久有效** - 只要仓库存在，链接就有效
- **无需密码** - 直接访问
- **全球可访问** - 任何网络都能打开
- **免费** - GitHub Pages 完全免费
- **HTTPS** - 安全链接

---

## 📱 手机访问

手机浏览器直接打开：
```
https://renyi9044-png.github.io/stick-hero-game/
```

---

## 🔄 更新游戏

修改 `index.html` 后，重新推送：

```bash
git add index.html
git commit -m "Update game"
git push
```

等待 1-2 分钟，更新自动生效！

---

**这是最稳定的部署方式！** 强烈推荐！🎮
