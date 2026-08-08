# TOEIC 托业词汇 · 分级记忆卡

一个纯前端的 TOEIC 词汇学习应用，按分数分三个等级，卡片翻转记忆，进度自动保存，手机电脑随时同步。

**无需注册、无需后端**，打开即用。

## 🚀 快速开始

### 在线使用（已部署）

🔗 **https://toeicvocabularywjw.netlify.app**

手机和电脑直接打开就能用，无需登录。手机端建议用浏览器「添加到主屏幕」，用起来更像一个 App。

### 本地打开

下载 `index.html` 和 `words.js`（放同一目录），双击 `index.html` 即可。

## ✨ 核心功能（怎么用）

### 1. 分级背词
按分数分三档，从简单到难循序渐进：
- 🌱 **600分 基础词汇**（415 词）· 🚀 **730分 进阶词汇**（705 词）· 🏆 **860分 高级词汇**（933 词）

点击顶部等级卡切换。**卡片模式**：点卡片翻面看释义；**列表模式**：快速浏览所有词。

### 2. 标记掌握，进度一目了然
- 点卡片上的「已掌握」按钮，标记这个单词记住了
- 顶部实时显示：**已掌握 / 剩余 / 完成百分比 / 进度条**
- 已掌握的词在列表里划线弱化，不用重复看

### 3. 批量掌握
想一次性标记一批单词为已掌握？点工具栏 **✅ 批量掌握**，进入选择模式——每个卡片出现复选框，**勾选任意多个**单词，点「标记已掌握」统一完成。适合「这一批我其实都会，只是没一个个点」的情况。支持「全选当前」一键勾选当前筛选下所有未掌握的词。

### 4. 导出未掌握单词（重点复习）
点工具栏 **📄 导出未掌握**，把当前级别没掌握的单词导出成 TXT（**每个单词一行**），文件名自动带级别和数量（如 `level2-未掌握-187词.txt`）。
- 可以发到微信 / 备忘录 / 打印出来，按自己节奏复习
- 手机自动调起分享，电脑直接保存文件

### 5. 搜索 & 筛选
- 顶部搜索框：按**单词或中文释义**搜索
- 筛选按钮：**全部 / 未掌握 / 已掌握**，只看想看的

### 6. 换设备不丢进度
进度自动保存在浏览器本地。跨设备同步有两种方式：

**方式一：文件备份（无需账号）**
顶部「导入导出」→ 保存备份文件 → 传到另一台设备 → 从备份恢复。

**方式二：GitHub Gist 云端同步（推荐，自动）**
顶部「同步」→ 粘贴 Token（只需 `gist` 权限）→ 手机背完点「上传」，电脑点「拉取」，两边互通。也支持「合并」保留两边进度。

> 🔐 Token 只存在你自己浏览器的 localStorage，不会上传到任何地方，也碰不到你的代码仓库。

## 📱 移动端提示

- 手机浏览器菜单 →「添加到主屏幕」，全屏体验更佳
- 导出未掌握时，手机自动调起分享，可直接发到微信或备忘录
- 部署成 https 网址后（如上面的 Netlify 链接），进度才能在手机上可靠保存

## 📁 文件说明

| 文件 | 用途 |
|---|---|
| `index.html` | 应用本体（部署用这个） |
| `words.js` | 词汇数据（2053 词，含音标、词性、释义） |
| `README.md` | 项目说明 |
| `NETLIFY.md` | 免费部署详细教程 |

## 🧰 技术栈

纯原生 HTML + CSS + JavaScript，零依赖，一个文件搞定。数据存浏览器本地，跨设备靠文件或 GitHub Gist。

## ⚖️ License

[MIT](LICENSE)

---

*纯前端小工具，给所有备考 TOEIC 的朋友。*

---

## English

# TOEIC Vocabulary · Graded Flash Cards

A pure front-end vocabulary app for the TOEIC exam, graded into three levels. Flip cards to memorize, progress saves automatically, and your phone and computer stay in sync.

**No sign-up, no backend** — open and go.

## 🚀 Quick Start

### Use it online (deployed)

🔗 **https://toeicvocabularywjw.netlify.app**

Open it on your phone or computer — no login needed. On mobile, use the browser menu → "Add to Home Screen" for a full-screen app-like experience.

### Use it locally

Download `index.html` and `words.js` (same folder), then double-click `index.html`.

## ✨ Features (how to use)

### 1. Graded vocabulary
Three levels, from easy to hard:
- 🌱 **600 Beginner** (415 words) · 🚀 **730 Intermediate** (705 words) · 🏆 **860 Advanced** (933 words)

Tap the level card to switch. **Card mode**: tap to flip and reveal the definition. **List mode**: browse all words quickly.

### 2. Mark mastered, see progress at a glance
- Tap "Mastered" on a card to mark a word as known
- Top bar shows **mastered / remaining / completion % / progress bar** live
- Mastered words are dimmed and struck through, so you skip them

### 3. One-click batch master
Want to mark a batch of words as mastered at once? Tap **✅ Batch Master** to enter selection mode — every card shows a checkbox. **Check any number of words**, then tap "Mark as mastered" to finish them all in one go. Perfect for "I actually know this batch, I just didn't tap each one." "Select All" grabs every unmastered word in the current filter.

### 4. Export unmastered words (focus review)
Tap **📄 Export Unmastered** to export the words you haven't mastered in the current level to a TXT file — **one word per line**. The filename includes the level and count (e.g. `level2-unmastered-187words.txt`).
- Send it to WeChat / Notes / print it, and review at your own pace
- On mobile it opens the system share sheet; on desktop it saves the file directly

### 5. Search & filter
- Search box: search by **word or Chinese definition**
- Filter buttons: **All / Unmastered / Mastered**

### 6. Never lose progress across devices
Progress is auto-saved in the browser. Two ways to sync:

**Option 1: File backup (no account)**
"Import/Export" → save a backup file → transfer to another device → restore.

**Option 2: GitHub Gist cloud sync (recommended, automatic)**
"Sync" → paste a Token (only needs the `gist` scope) → on phone tap "Upload" when done, on computer tap "Pull". A "Merge" button keeps mastered words from both sides.

> 🔐 Your Token lives only in your own browser's localStorage, is never uploaded anywhere, and cannot touch your code repositories.

## 📱 Mobile tips

- Browser menu → "Add to Home Screen" for a full-screen experience
- When exporting unmastered words, mobile opens the share sheet so you can send them to WeChat or Notes directly
- Deploying to an https URL (like the Netlify link above) makes progress save reliably on phones

## 📁 Files

| File | Purpose |
|---|---|
| `index.html` | The app (use this for deployment) |
| `words.js` | Vocabulary data (2,053 words with phonetics, POS, meanings) |
| `README.md` | This readme |
| `NETLIFY.md` | Free deployment guide |

## 🧰 Tech Stack

Plain HTML + CSS + JavaScript, zero dependencies, one file. Data lives in your browser; cross-device sync via file or GitHub Gist.

## ⚖️ License

[MIT](LICENSE)

---

*A small pure-frontend tool for everyone preparing for the TOEIC exam.*
