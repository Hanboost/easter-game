# GitHub Pages 部署指南（保姆级教程）

## 总共 4 步，预计 5 分钟

---

## 第 1 步：注册 GitHub 账号（已有账号跳过）

1. 打开 https://github.com/signup
2. 填写邮箱、密码、用户名（用户名会出现在游戏链接里，建议用 `hanboost` 或品牌相关的名字）
3. 完成验证，点 Create account

---

## 第 2 步：创建仓库并上传文件

1. 登录 GitHub 后，点击右上角 **+** 号 → **New repository**

2. 填写仓库信息：
   - Repository name: **easter-game**
   - Description: Hanboost Easter Hunt Game（可选）
   - 选择 **Public**（必须选 Public，GitHub Pages 免费版只支持公开仓库）
   - **不要**勾选 Add a README
   - 点击 **Create repository**

3. 在新建的空仓库页面，点击 **uploading an existing file**（蓝色链接）

4. 把解压后的 `easter-game` 文件夹里的**所有文件**拖进上传区域：
   - `index.html`（主游戏文件）
   - `README.md`
   - `assets/` 文件夹（里面有占位图片）
   - `shopify-iframe-code.html`
   
   注意：是把文件夹**里面的内容**拖进去，不是把文件夹本身拖进去

5. 页面底部 Commit changes 区域，直接点 **Commit changes** 绿色按钮

---

## 第 3 步：开启 GitHub Pages

1. 在仓库页面，点击顶部的 **Settings**（齿轮图标）

2. 左侧菜单找到 **Pages**，点击进入

3. 在 "Build and deployment" 区域：
   - Source 选择：**Deploy from a branch**
   - Branch 选择：**main**，文件夹选 **/ (root)**
   - 点击 **Save**

4. 等待 1-2 分钟，页面顶部会出现绿色提示：
   **"Your site is live at https://你的用户名.github.io/easter-game/"**

5. 点击这个链接，确认游戏能正常打开和运行

---

## 第 4 步：嵌入 Shopify

1. 复制你的 GitHub Pages 链接，格式为：
   ```
   https://你的用户名.github.io/easter-game/
   ```

2. 登录 Shopify 后台

3. 方式 A —— 新建页面：
   - **Online Store → Pages → Add page**
   - 标题：Easter Hunt Game
   - 编辑器切换到 **HTML 模式**（点 `<>` 按钮）
   - 粘贴以下代码（把链接替换成你的）：

   ```html
   <div style="max-width:640px;margin:30px auto;">
     <iframe 
       src="https://你的用户名.github.io/easter-game/"
       width="100%" height="435" frameborder="0" scrolling="no" 
       allow="autoplay"
       style="display:block;border:none;border-radius:16px;box-shadow:0 8px 32px rgba(0,0,0,0.12);"
       title="Hanboost Easter Hunt Game">
     </iframe>
   </div>
   <script>
   (function(){var f=document.querySelector('iframe[title="Hanboost Easter Hunt Game"]');if(!f)return;function r(){f.style.height=Math.round(f.offsetWidth*380/560)+'px'}r();window.addEventListener('resize',r)})();
   </script>
   ```

4. 方式 B —— Custom Liquid 区块：
   - **Themes → Customize** → 选择活动页面
   - 添加 **Custom Liquid** 区块
   - 粘贴上面同样的代码

5. 保存，完成！

---

## 以后设计师怎么更新图片

1. 设计师画好新的背景图（按 README.md 里的尺寸规格）
2. 打开 GitHub 仓库页面 → 进入 `assets` 文件夹
3. 点击 **Add file → Upload files**
4. 拖入新图片（**文件名必须和占位图一模一样**，比如 `level1-bg.png`）
5. GitHub 会自动覆盖旧文件
6. 点 **Commit changes**
7. 等 1-2 分钟，GitHub Pages 会自动更新，Shopify 页面也会自动显示新图片

**不需要改任何代码，不需要重新嵌入，替换图片就完事了。**

---

## 常见问题

**Q: 上传后 GitHub Pages 链接打不开？**
A: 等 2-3 分钟，首次部署需要时间。如果超过 5 分钟还打不开，检查 Settings → Pages 是否正确设置了 branch 为 main。

**Q: Shopify 里 iframe 显示空白？**
A: 先单独打开 GitHub Pages 链接确认游戏正常，再检查 iframe 的 src 链接是否正确（注意 https 和末尾的 /）。

**Q: 游戏在 Shopify 里被截断/显示不全？**
A: 确保粘贴了底部的 `<script>` 自适应代码，它会根据宽度自动调整 iframe 高度。

**Q: 设计师替换图片后没有生效？**
A: GitHub Pages 有 CDN 缓存，通常 2-5 分钟更新。可以在浏览器强制刷新（Ctrl+Shift+R）或等待缓存过期。

**Q: 仓库可以设为 Private 吗？**  
A: GitHub 免费账号的 Pages 只支持 Public 仓库。如果需要 Private，需要升级到 GitHub Pro（$4/月）。游戏代码是前端的，公开也不影响安全性。
