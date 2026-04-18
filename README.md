# Blossom like crocus

文艺个人博客系统，纯静态，无需服务器。

## 特点

- 🌸 番红花紫配色，文艺简洁
- 📱 响应式设计，移动端完美
- 🏷️ 标签云、归档、分页
- 🚀 三种发布方式：一键推送 / 下载 JSON / 复制粘贴
- 🔒 Token 仅本地存储，安全隐私

## 快速开始

1. Fork 本仓库
2. 修改 `admin.html` 中的 `CONFIG.owner` 和 `CONFIG.repo`
3. 开启 GitHub Pages（Settings → Pages → Source: main）
4. 访问 `https://你的用户名.github.io/blossom-blog`

## 写文章

打开 `admin.html`，三种方式：

| 方式 | 步骤 |
|-----|------|
| **一键推送** | 配置 Token → 填写文章 → 点击"推送到 GitHub" |
| **下载上传** | 填写文章 → 点击"下载 JSON" → 上传到 `posts/` 文件夹 |
| **复制粘贴** | 填写文章 → 点击"复制 JSON" → 在 GitHub 新建文件粘贴 |

## 自定义域名

1. 修改 `CNAME` 文件为你的域名
2. 域名解析 CNAME 到 `你的用户名.github.io`
3. GitHub Pages 设置里添加自定义域名

## 文件说明

- `index.html` - 博客首页（自动加载 posts/ 下所有文章）
- `admin.html` - 管理后台（本地打开，写文章用）
- `posts/` - 文章文件夹（JSON 格式）
