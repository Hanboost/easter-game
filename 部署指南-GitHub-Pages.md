# =====================================================
#  Hanboost Easter Game — GitHub Pages 部署操作指南
# =====================================================
#
#  总共 4 步，大约 10 分钟搞定
#
# =====================================================


## 第一步：注册 GitHub 账号（如已有可跳过）

1. 打开 https://github.com/signup
2. 输入邮箱、密码、用户名，完成注册
3. 验证邮箱


## 第二步：创建仓库并上传文件

1. 登录 GitHub 后，点击右上角 **+** → **New repository**
2. 填写：
   - Repository name：`easter-game`
   - Description：`Hanboost Easter Hunt Game`
   - 选择 **Public**（必须是 Public 才能用 GitHub Pages 免费托管）
   - ✅ 勾选 **Add a README file**
3. 点击 **Create repository**
4. 进入仓库页面后，点击 **Add file** → **Upload files**
5. 把解压后的以下文件/文件夹**全部拖进去**：
   ```
   index.html        ← 拖这个文件
   assets/            ← 拖整个文件夹（里面有占位图）
   ```
6. 底部 Commit message 填：`Upload Easter game files`
7. 点击 **Commit changes**


## 第三步：开启 GitHub Pages

1. 在仓库页面，点击顶部的 **Settings**（齿轮图标）
2. 左侧菜单找到 **Pages**
3. 在 **Source** 下拉框中选择：
   - Branch: **main**
   - Folder: **/ (root)**
4. 点击 **Save**
5. 等待 1-2 分钟，页面顶部会出现绿色提示：
   ```
   Your site is live at https://你的用户名.github.io/easter-game/
   ```
6. 点击链接验证游戏是否正常运行


## 第四步：嵌入到 Shopify

1. 复制你的 GitHub Pages 链接（格式：`https://你的用户名.github.io/easter-game/`）
2. 进入 Shopify 后台 → **Online Store** → **Pages** → **Add page**
3. 页面标题填 `Easter Hunt Game`
4. 编辑器切换到 **HTML 模式**（点 `<>` 按钮）
5. 粘贴以下代码（把链接换成你自己的）：

```html
<div style="max-width:640px;margin:0 auto;padding:20px 0;">
  <iframe
    src="https://你的用户名.github.io/easter-game/"
    width="100%"
    height="435"
    frameborder="0"
    scrolling="no"
    allow="autoplay"
    style="display:block;border:none;border-radius:16px;box-shadow:0 8px 32px rgba(0,0,0,0.12);"
    title="Hanboost Easter Hunt Game">
  </iframe>
</div>
<script>
(function(){
  var f=document.querySelector('iframe[title="Hanboost Easter Hunt Game"]');
  if(!f)return;
  function r(){f.style.height=Math.round(f.offsetWidth*380/560)+'px'}
  r();window.addEventListener('resize',r);
})();
</script>
```

6. 保存页面
7. 访问你的页面确认游戏正常显示


## 以后设计师更新图片怎么操作

1. 设计师按照 README.md 里的规格做好新的 PNG 图片
2. 登录 GitHub → 进入 easter-game 仓库
3. 进入 `assets/` 文件夹
4. 点击要替换的文件（例如 `level1-bg.png`）
5. 点击右上角铅笔旁边的 **...** → **Delete file** → Commit
6. 然后 **Add file** → **Upload files** → 上传同名新文件 → Commit
7. 等 1-2 分钟 GitHub Pages 自动更新，刷新页面即可看到新图

**无需修改任何代码，无需通知开发者，设计师自己就能操作。**


## 常见问题

**Q: GitHub Pages 要多久才能生效？**
A: 通常 1-2 分钟，最慢不超过 10 分钟。

**Q: 更新文件后页面没变化？**
A: 浏览器缓存。按 Ctrl+Shift+R（Mac: Cmd+Shift+R）强制刷新。

**Q: 流量有限制吗？**
A: GitHub Pages 免费版每月 100GB 带宽，对于活动页面绰绰有余。

**Q: 可以绑定自定义域名吗？**
A: 可以。Settings → Pages → Custom domain，填入你的域名并配置 DNS。
   例如可以设置成 `game.hanboost.com`。

**Q: Shopify 主题会影响游戏样式吗？**
A: 不会。因为用的是 iframe，游戏在独立沙盒中运行，完全隔离。
