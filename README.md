# shiro 个人网站

一个公开、可被搜索引擎收录的个人静态网站（HTML + CSS + JS，无需构建）。

## 目录结构

```
shiro-site/
├── index.html      首页
├── projects.html   项目
├── blog.html       博客
├── contact.html    联系
├── 404.html        404 页面
├── css/style.css   样式
├── js/main.js      脚本
├── robots.txt      搜索引擎抓取规则
├── sitemap.xml     站点地图（提交给搜索引擎用）
└── README.md
```

## 上线前必须做的事

1. **全局替换 `GITHUB_USERNAME` 为你的 GitHub 用户名**。它出现在以下文件中：
   - 每个 HTML 文件 `<head>` 里的 `canonical`、Open Graph 链接
   - `index.html` 里的 JSON-LD 结构化数据
   - `robots.txt` 和 `sitemap.xml` 里的站点地址
   - `contact.html` 里的 GitHub 链接

   最简单的办法：用编辑器（如 VS Code）对整个文件夹执行“查找替换”
   `GITHUB_USERNAME` → 你的用户名。

2. **替换占位联系方式**（`contact.html`）：
   - 邮箱 `hello@example.com` → 你的真实邮箱（页面里和底部脚本里各有一处）
   - GitHub 链接、微信号等

3. **替换占位文案**：搜索“占位”二字，换成你的真实内容。

## 部署到 GitHub Pages（免费二级域名）

### 方式 A：用户站点（推荐，网址最干净）

1. 在 GitHub 新建仓库，仓库名必须是 `<你的用户名>.github.io`
   （把 `<你的用户名>` 换成你自己的，必须完全一致，否则不生效）。
2. 仓库设为 Public（公开）。
3. 把本文件夹 `shiro-site` 里的所有文件上传到该仓库根目录。
4. 等 1~2 分钟，访问 `https://<你的用户名>.github.io/` 即可看到网站。

### 方式 B：项目站点

1. 新建任意仓库（如 `shiro-site`），设为 Public。
2. 上传文件后，进入仓库 → Settings → Pages → Source 选
   `Deploy from a branch`，分支选 `main`，目录选 `/ (root)`，保存。
3. 网站地址会是 `https://<你的用户名>.github.io/shiro-site/`。

### 用命令行推送（二选一）

```bash
cd shiro-site
git init
git add .
git commit -m "init: personal website"
git branch -M main
git remote add origin https://github.com/<你的用户名>/<你的用户名>.github.io.git
git push -u origin main
```

## 让搜索引擎收录（关键步骤）

1. **Google Search Console**（https://search.google.com/search-console）
   - 添加网站属性 → 选“网址前缀” → 输入 `https://<你的用户名>.github.io/`
   - 验证所有权（HTML 标签 / 上传文件 / DNS 均可）
   - 在“站点地图”里提交 `sitemap.xml`
   - 在“网址检查”里输入首页地址，点“请求编入索引”

2. **Bing Webmaster**（https://www.bing.com/webmasters）
   - 可直接导入你的 Google Search Console 站点，提交 sitemap。

3. 收录不是实时的，通常需要几天到几周，耐心等待；持续更新内容会加快收录。

## 之后迁移到大陆服务器（备案完成后）

1. 域名备案完成后，把这套文件上传到阿里云/腾讯云服务器（或对象存储 OSS/COS 托管静态站）。
2. 把每个页面里的 `https://GITHUB_USERNAME.github.io` 全部替换成你的正式域名，并更新 `robots.txt`、`sitemap.xml`。
3. 在百度搜索资源平台（https://ziyuan.baidu.com）提交站点与 sitemap，让百度收录。
