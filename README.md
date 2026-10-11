# awnighthunt 的博客

Hugo + PaperMod 搭建的静态博客，部署到 GitHub Pages。
支持：**多标签**、**站内全文搜索**、**自动发布**。

## 项目结构

```
awnighthunt-blog/
├─ hugo.toml              # 站点配置（标题、导航、标签、搜索）
├─ content/
│  ├─ posts/              # 你写文章的地方（Markdown 文件）
│  └─ search.md           # 搜索页
├─ themes/PaperMod/       # 主题（已内置，无需额外下载）
└─ .github/workflows/deploy.yml   # 推送后自动构建发布
```

---

## 一、Windows 端安装（只需做一次）

### 1. 安装 Git
- 到 https://git-scm.com/downloads 下载安装，一路默认即可。

### 2. 安装 Hugo
- 到 https://github.com/gohugoio/hugo/releases 下载
  **hugo_extended_0.151.2_windows-amd64.zip**（Extended 版，很重要）。
- 解压后把 `hugo.exe` 放到一个固定文件夹（例如 `C:\hugo\`），并把该文件夹加进系统环境变量 `Path`。
- 打开命令行（Win+R → 输入 `cmd`）输入 `hugo version`，能显示版本号即安装成功。

---

## 二、发布到 GitHub（做一次）

1. 把本文件夹 `awnighthunt-blog` 放到电脑上（例如 `C:\blog\awnighthunt-blog`）。
2. 在 GitHub 网页上新建一个**公开**仓库，仓库名填 **`awnighthunt.github.io`**（务必这样命名，才能让博客显示在 awnighthunt.github.io 根地址）。
3. 在电脑上打开命令行，进入项目目录并推送：
   ```
   cd C:\blog\awnighthunt-blog
   git init
   git add .
   git commit -m "init blog"
   git branch -M main
   git remote add origin https://github.com/awnighthunt/awnighthunt.github.io.git
   git push -u origin main
   ```
4. 在 GitHub 仓库页面：**Settings → Pages → Source 选 "GitHub Actions"**。
5. 等待 Actions 跑完（仓库顶部 Actions 标签可看进度），然后访问：
   **https://awnighthunt.github.io/** 即可看到博客上线。

---

## 三、以后日常写文章

1. 新建一篇：在 `content/posts/` 里新建一个 `.md` 文件（可复制现有文章当模板）。
2. 文件开头写：
   ```
   ---
   title: "文章标题"
   date: 2026-10-11
   tags: ["标签1", "标签2"]     # 想打几个就打几个
   ---
   ```
3. 正文用 Markdown 写。
4. 想本地预览：命令行运行 `hugo server`，浏览器打开 http://localhost:1313
5. 发布：把改动推送上去即可：
   ```
   git add .
   git commit -m "新文章"
   git push
   ```
   GitHub Actions 会自动构建发布。

## 四、私密内容怎么办

- 不想公开的文章：不要把它 push 上去即可，保留在本地（也可用 Obsidian 等本地工具管理）。
- 草稿：把文件开头的 `draft: false` 改成 `draft: true`，本地预览能看到，但不会发布到线上。
