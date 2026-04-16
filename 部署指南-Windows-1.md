# 🌸 Blossom — 完整部署指南
## Obsidian + GitHub + Netlify（Windows 版）

---

## 你需要准备的东西（都免费）
- GitHub 账号（已有）
- Obsidian（已安装）
- Git for Windows
- Netlify 账号

---

## 第一步：安装 Git for Windows

1. 打开 [git-scm.com/download/win](https://git-scm.com/download/win)
2. 下载自动开始，运行安装包
3. 一路点 **Next**，所有选项保持默认即可
4. 安装完成后，按 **Win + R** → 输入 `cmd` → 回车，打开命令提示符
5. 输入 `git --version`，看到版本号说明安装成功

---

## 第二步：设置 Git 身份（只需做一次）

在命令提示符里运行以下两行（换成你自己的信息）：

```
git config --global user.email "你的邮箱"
git config --global user.name "Tina"
```

---

## 第三步：在 GitHub 建仓库

1. 登录 [github.com](https://github.com)
2. 右上角 **+** → **New repository**
3. Repository name 填：`blossom-site`
4. 选 **Public**（必须公开，网站才能读文章）
5. 勾选 **Add a README file**
6. 点 **Create repository**

---

## 第四步：上传网站文件到 GitHub

1. 进入你的 `blossom-site` 仓库页面
2. 点 **Add file** → **Upload files**
3. 把以下文件拖进去：
   - `index.html`
   - `netlify.toml`
   - `posts` 文件夹里的示例 `.md` 文件（先手动上传一篇）
4. 点 **Commit changes** ✓

> 💡 **关于 posts 文件夹：** GitHub 网页版不能直接上传文件夹，需要先在仓库里手动建文件夹——点 **Add file** → **Create new file** → 文件名输入 `posts/示例.md` → 粘贴示例内容 → Commit。这样 `posts` 文件夹就建好了。

---

## 第五步：把仓库克隆到本地，作为 Obsidian Vault

### 5a. 获取仓库地址
仓库页面 → 绿色 **Code** 按钮 → 复制 HTTPS 链接
（格式：`https://github.com/你的用户名/blossom-site.git`）

### 5b. 克隆到本地
打开命令提示符，运行（可以换成你想放的路径）：

```
cd C:\Users\你的用户名\Documents
git clone https://github.com/你的用户名/blossom-site.git
```

Documents 里会出现 `blossom-site` 文件夹。

> 💡 **首次克隆会弹出 GitHub 登录窗口**，登录你的 GitHub 账号即可，之后不再弹出。

### 5c. 在 Obsidian 里打开这个文件夹
- Obsidian → 左下角 Vault 图标 → **Open folder as vault**
- 选择 `blossom-site` 文件夹
- 现在 Obsidian 里的 `posts` 文件夹就是你写文章的地方 ✓

---

## 第六步：安装 Obsidian Git 插件

1. Obsidian → 左下角齿轮「**设置**」
2. **第三方插件** → 关闭安全模式 → 点**浏览**
3. 搜索 `Obsidian Git` → 安装 → 启用
4. 回到设置 → 左侧找到 **Obsidian Git**，建议设置：
   - `Vault backup interval (minutes)`：`0`（手动推送）
   - `Pull updates on startup`：开启

---

## 第七步：部署到 Netlify

1. 打开 [netlify.com](https://netlify.com)，用 GitHub 账号登录
2. **Add new site** → **Import an existing project** → **GitHub**
3. 授权 Netlify 访问你的 GitHub → 选择 `blossom-site` 仓库
4. Build settings 全部保持默认
5. 点 **Deploy site**
6. 等约 1 分钟，网站上线，得到一个 `xxx.netlify.app` 的网址 ✓

---

## 第八步：在网站管理页连接 GitHub

1. 打开你的 Netlify 网站
2. 点右上角「**管理**」
3. 填入：
   - GitHub 用户名
   - 仓库名：`blossom-site`
   - 文章文件夹：`posts`
4. 点「**保存并测试连接**」→ 出现「✓ 连接成功」
5. 示例文章卡片出现在首页 ✓

---

## 第九步：绑定自己的域名

1. Netlify → **Domain management** → **Add a domain**
2. 输入你的域名 → 按提示在域名注册商处添加 DNS 记录
3. 约 10 分钟到 2 小时生效，HTTPS 自动配置好

---

## 日常发文章（设置完成后，每次只需这三步）

**① 在 Obsidian 的 `posts` 文件夹新建 `.md` 文件**

文件顶部加 frontmatter：

```
---
title: 文章标题
tag: 圣经
excerpt: 一句简短摘要，显示在卡片上
date: 2026-04-16
type: article
---

正文从这里开始，支持完整 Markdown...
```

**② 写完后推送到 GitHub**

按 **Ctrl + P** → 搜索 `Obsidian Git: Commit and push` → 回车

**③ 等约 1 分钟，刷新网站，文章出现 ✓**

---

## 发 YouTube 视频

```
---
title: 视频标题
tag: YouTube
excerpt: 视频简介
date: 2026-04-16
type: youtube
---

https://youtu.be/你的视频ID

这里可以写补充说明...
```

---

## tag 和 type 可填的值

**tag：** `圣经` `AI极简` `帕金森` `儿童自闭症` `YouTube` `生活`

**type：** `article`（文章） `youtube`（视频） `quote`（灵感短句）

---

## 常见问题

**Q: 推送时弹出登录窗口或要求输入密码？**
A: GitHub 现在不支持密码，需要用 Personal Access Token：
   GitHub → 右上角头像 → Settings → Developer settings →
   Personal access tokens → Tokens (classic) → Generate new token →
   勾选 `repo` → 生成 → 复制这串字符，推送时当密码用。

**Q: 推送后多久更新？**
A: Netlify 检测到 GitHub 变化后约 30 秒到 1 分钟自动部署。

**Q: 文章不显示？**
A: 检查：① frontmatter 格式正确，`---` 上下各一行 ② `title:` 后面有值 ③ 仓库是 Public。

**Q: 图片怎么放？**
A: 把图片放进 `posts/images/` 文件夹，文章里用 `![描述](images/文件名.jpg)` 引用，一起推送到 GitHub 即可。

**Q: 修改已发布的文章？**
A: 直接在 Obsidian 里改，再 Commit and push，网站自动更新。
