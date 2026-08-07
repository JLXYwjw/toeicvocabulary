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
├── README.md           # 本文件
└── .gitignore          # 忽略个人备份文件
```

> `托业词汇分级记忆卡（修复版）.html` 是开发版源文件，内容与 `index.html` 一致，日常使用/部署请用 `index.html`。

## 🚀 快速开始

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
