# 🎮 棍子英雄 - 抖音小游戏发布包

## 📦 文件说明

| 文件 | 说明 |
|------|------|
| `index_douyin.html` | 抖音适配版主入口 |
| `game.json` | 游戏配置文件 |
| `project.config.json` | 项目配置（需填写 AppID） |
| `抖音适配指南.md` | 详细适配文档 |

---

## 🚀 发布步骤

### 1. 注册抖音小游戏开发者

访问：https://developer.open-douyin.com/

- 完成实名认证
- 创建小游戏应用
- 获取 **AppID**

### 2. 配置项目

编辑 `project.config.json`：
```json
{
  "appid": "你的 AppID",  // ← 替换成你的
  "projectname": "stick-hero"
}
```

### 3. 下载开发者工具

- 访问：https://developer.open-douyin.com/devtool
- 下载并安装
- 登录开发者账号

### 4. 导入项目

- 打开开发者工具
- 点击"导入项目"
- 选择本文件夹
- 填写 AppID

### 5. 上传代码

- 点击"上传"按钮
- 填写版本号（如：1.0.0）
- 填写版本说明
- 等待上传完成

### 6. 提交审核

- 登录抖音小游戏后台
- 找到刚上传的版本
- 填写审核信息
- 提交审核（1-3 个工作日）

### 7. 发布上线

- 审核通过后
- 点击"发布"
- 游戏正式上线！

---

## ⚙️ 已适配功能

### ✅ 触摸控制
```javascript
// 同时支持标准触摸和抖音 SDK
canvas.ontouchstart = ...
tt.onTouchStart(...)
```

### ✅ 本地存储
```javascript
// 自动判断环境
if (typeof tt !== 'undefined') {
    tt.setStorage({...});  // 抖音
} else {
    localStorage.setItem(...);  // 浏览器
}
```

### ✅ 屏幕适配
- 自动填满屏幕
- 保持游戏比例
- 支持横竖屏

---

## 💰 变现功能（可选）

### 激励视频广告

在 `index_douyin.html` 中添加：

```javascript
// 创建广告实例
let videoAd = tt.createRewardedVideoAd({
    adUnitId: '你的广告位 ID'
});

// 播放广告（如：复活）
function showAdForRevive() {
    videoAd.show().catch(() => {
        videoAd.load().then(() => videoAd.show());
    });
    
    videoAd.onClose(res => {
        if (res && res.isEnded) {
            // 给予复活奖励
            revive();
        }
    });
}
```

### 插屏广告

游戏结束时展示：

```javascript
if (state === 'gameover') {
    tt.createInterstitialAd({
        adUnitId: '你的插屏广告 ID'
    }).show();
}
```

---

## 📊 数据接入（可选）

### 抖音游戏圈

```javascript
// 发布动态
tt.shareAppMessage({
    title: '棍子英雄 - 我得了 ' + score + ' 分！',
    imageUrl: 'cover.jpg'
});
```

### 好友排行榜

```javascript
// 获取好友分数
tt.getFriendCloudStorage({
    key: 'stickBest',
    success: (res) => {
        // 显示排行榜
    }
});
```

---

## ⚠️ 注意事项

1. **包体大小**：首包 ≤ 4MB（当前远小于此）
2. **性能要求**：保持 60fps
3. **内容审核**：不含违规内容
4. **隐私政策**：需在后台配置
5. **版号**：如需内购，必须有版号

---

## 🎯 测试清单

- [ ] PC 浏览器测试（`index.html`）
- [ ] 手机浏览器测试（GitHub Pages 链接）
- [ ] 抖音开发者工具测试
- [ ] 真机测试（扫码预览）
- [ ] 广告功能测试
- [ ] 存储功能测试
- [ ] 分享功能测试

---

**当前版本：** 1.0.0  
**更新日期：** 2026-03-12  
**状态：** ✅ 手机版完成，待适配抖音提交
