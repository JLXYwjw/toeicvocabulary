# TOEIC 托业词汇 · 分级记忆卡

一个纯前端的 TOEIC 词汇学习应用，按分数分三个等级，支持卡片翻转记忆、进度统计、本地保存、文件备份与云端同步。

**无需后端、无需数据库**，就是一个 HTML + 一个 JS，打开即用。

## ✨ 功能

- **三级词汇**：600分基础 / 730分进阶 / 860分高级，共 2053 个 TOEIC 核心词汇
- **两种学习模式**
  - 卡片模式：点击翻转查看释义
  - 列表模式：词条列表快速浏览
- **标记已掌握**：一键标记，已掌握的词在列表里划线弱化
- **进度统计**：当前等级掌握数、剩余数、完成百分比、进度条
- **搜索与筛选**：按单词 / 中文释义搜索，按「全部 / 未掌握 / 已掌握」筛选
- **进度自动保存**：localStorage + Cookie 双通道，本地 HTML 打开也能保存
- **文件备份 / 恢复**：进度导出成 JSON 文件，换设备可手动恢复
- **云端同步**：通过 GitHub Gist 在手机与电脑之间同步进度

## 📁 文件结构

```
├── index.html          # 应用入口（部署时用这个）
├── words.js            # 词汇数据（2053 词，三个等级）
├── README.md           # 项目说明（中英双语）
├── NETLIFY.md          # Netlify 部署详细指南
└── .gitignore          # 忽略个人备份文件
```

> `托业词汇分级记忆卡（修复版）.html` 是开发版源文件，内容与 `index.html` 一致，日常使用/部署请用 `index.html`。

## 🚀 快速开始

### 在线体验（已部署）

本项目的官方在线版本部署在 Netlify：

🔗 **https://toeicvocabularywjw.netlify.app**

手机和电脑都能直接访问，无需登录。

### 本地打开

直接双击 `index.html` 即可使用（`words.js` 必须与它同目录）。

### 局域网预览（手机测试）

在项目目录启动一个静态服务器，手机连同一 WiFi 访问：

```bash
python -m http.server 8000
```

手机浏览器打开 `http://<电脑局域网IP>:8000/`

### 免费部署（推荐）

任意静态托管平台均可，把 `index.html` 和 `words.js` 两个文件一起上传：

- **Netlify Drop**：打开 `netlify.com/drop`，把两个文件拖进去，即可获得 `https://xxx.netlify.app` 网址
- **GitHub Pages**：推到仓库后开启 Pages

> 📖 **Netlify 详细部署教程**：见 [NETLIFY.md](NETLIFY.md)（免费与否、Drop 手动部署、连接 GitHub 自动部署、更新网站、自定义域名、常见问题）

部署成 https 网址后，localStorage 才能在手机上可靠保存进度。

## 🔄 进度保存与同步

进度数据（已掌握的单词）默认保存在浏览器的 localStorage + Cookie 中，按设备、按浏览器隔离。跨设备同步有两种方式：

### 方式一：文件备份（手动，无需账号）

顶部「导入导出」→「保存为备份文件」→ 得到一份 JSON，可通过微信 / 备忘录传到另一台设备 → 另一台设备「从备份文件恢复」。

### 方式二：GitHub Gist 云端同步（自动，推荐）

利用 GitHub Gist 作为云端存储，手机与电脑连接同一个 Gist 即可互通。

**首次配置（每台设备各做一次）：**

1. GitHub → Settings → Developer settings → Personal access tokens → Tokens (classic) → Generate new token (classic)
   - 权限**只勾 `gist`**，有效期建议 90 天
2. 打开网页 → 顶部「同步」→ 粘贴 Token
3. 第一台设备点「☁️ 上传进度」，会自动创建私有 Gist 并回填网址
4. 另一台设备填同一个 Token → 点「⬇️ 拉取进度」

**日常使用：**

- 手机背完 → 手机「上传进度」
- 电脑 → 电脑「拉取进度」

也提供「合并」按钮：保留两边已掌握的单词，合并结果回传云端。

> **安全说明**：Token 只存本机浏览器 localStorage，不会上传到任何地方。`gist` 权限只能读写你的 Gist，无法访问代码仓库。到期后在 GitHub 重新生成替换即可。

## 🧰 技术栈

- 原生 HTML + CSS + JavaScript（无构建、无依赖）
- [Tailwind CSS](https://cdn.tailwindcss.com)（CDN）
- [GitHub Gist API](https://docs.github.com/rest/gists)（同步）

## 📄 词汇数据

词汇按三个 TOEIC 分数段分级，每条包含单词、音标、词性、中文释义、示例。数据结构见 `words.js`。

## ⚖️ License

[MIT](LICENSE)（请按需补充）

---

*纯前端小工具，给自己和所有备考 TOEIC 的朋友。*

---

## English

# TOEIC Vocabulary · Graded Flash Cards

A pure front-end vocabulary learning app for the TOEIC exam, graded into three levels by target score. Features flip-card memorization, progress tracking, local saving, file backup, and cloud sync.

**No backend, no database** — just one HTML file and one JS file. Open and go.

## ✨ Features

- **Three graded levels**: 600 / 730 / 860 target score, 2,053 core TOEIC words in total
- **Two study modes**
  - Card mode: click to flip and reveal the definition
  - List mode: browse words as a quick list
- **Mark as mastered**: one-click toggle; mastered words are dimmed and struck through
- **Progress stats**: mastered count, remaining, completion %, progress bar
- **Search & filter**: search by word or Chinese definition; filter by All / Not mastered / Mastered
- **Auto-save progress**: dual-channel via localStorage + Cookie, works even when opening the local HTML file
- **File backup / restore**: export progress to a JSON file, manually restore on another device
- **Cloud sync**: sync progress between phone and computer via GitHub Gist

## 📁 File Structure

```
├── index.html          # App entry (use this for deployment)
├── words.js            # Vocabulary data (2,053 words, three levels)
├── README.md           # Project readme (Chinese & English)
├── NETLIFY.md          # Detailed Netlify deployment guide
└── .gitignore          # Excludes personal backup files
```

## 🚀 Quick Start

### Try it online (deployed)

The official live version of this project is hosted on Netlify:

🔗 **https://toeicvocabularywjw.netlify.app**

Accessible from both phone and computer, no login required.

### Open locally

Double-click `index.html` to use it (`words.js` must be in the same directory).

### Preview on your LAN (test on your phone)

Start a static server in the project folder, then open it from a phone on the same Wi-Fi:

```bash
python -m http.server 8000
```

Open `http://<your-computer-LAN-IP>:8000/` in the phone browser.

### Free deployment (recommended)

Any static hosting platform works — upload `index.html` and `words.js` together:

- **Netlify Drop**: go to `netlify.com/drop`, drag the two files in, get a `https://xxx.netlify.app` URL
- **GitHub Pages**: push to a repo and enable Pages

> 📖 **Detailed Netlify deployment guide**: see [NETLIFY.md](NETLIFY.md) (is it free, Drop manual deploy, connect GitHub for auto-deploy, updating the site, custom domains, FAQ)

Once deployed to an https URL, localStorage saves progress reliably on phones.

## 🔄 Progress Saving & Sync

Progress (mastered words) is stored in the browser's localStorage + Cookie by default, isolated per device and browser. Two ways to sync across devices:

### Option 1: File backup (manual, no account needed)

Top menu "Import/Export" → "Save as backup file" → get a JSON, transfer it via WeChat / Notes / etc. to another device → "Restore from backup file" there.

### Option 2: GitHub Gist cloud sync (automatic, recommended)

Use a GitHub Gist as cloud storage — your phone and computer connect to the same Gist to stay in sync.

**First-time setup (once per device):**

1. GitHub → Settings → Developer settings → Personal access tokens → Tokens (classic) → Generate new token (classic)
   - Only check the **`gist`** scope, validity suggested 90 days
2. Open the web app → top menu "Sync" → paste the Token
3. On the first device click "☁️ Upload", which auto-creates a private Gist and fills in the URL
4. On the other device paste the same Token → click "⬇️ Pull"

**Daily use:**

- Done studying on phone → phone "Upload"
- On computer → computer "Pull"

A "Merge" button is also available: keeps mastered words from both sides and pushes the merged result back to the cloud.

> **Security note**: The Token is stored only in the local browser's localStorage and is never uploaded anywhere. The `gist` scope can only read/write your Gists — it cannot access your code repositories. When it expires, generate a new one on GitHub and replace it.

## 🧰 Tech Stack

- Plain HTML + CSS + JavaScript (no build step, no dependencies)
- [Tailwind CSS](https://cdn.tailwindcss.com) (CDN)
- [GitHub Gist API](https://docs.github.com/rest/gists) (sync)

## 📄 Vocabulary Data

Words are graded by three TOEIC score bands. Each entry includes the word, phonetic, part of speech, Chinese definition, and an example. See `words.js` for the data structure.

## ⚖️ License

[MIT](LICENSE)

---

*A small pure-frontend tool, for myself and everyone preparing for the TOEIC exam.*
