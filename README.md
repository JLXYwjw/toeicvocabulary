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

### 3. 英美发音 🔊
单词旁有两个小喇叭：🔵 **美式发音** / 🟣 **英式发音**，点一下即播放。音标也同时标注**英美两套**（如 `schedule` 英 `[ˈʃedjuːl]` / 美 `[ˈskedʒuːl]`），发音与音标均来自权威词典。

**发音技术方案：**

| 项目 | 说明 |
|---|---|
| 发音源 | **有道词典真人发音**（`dict.youdao.com/dictvoice`），非机器 TTS 合成 |
| 英式音频 | `dictvoice?audio=单词&type=1`（真人录制） |
| 美式音频 | `dictvoice?audio=单词&type=2`（真人录制） |
| 数据存储 | 每个词条含 `us`（美式 URL）和 `uk`（英式 URL）两个字段，随 `words.js` 一起加载 |
| 播放逻辑 | 优先用词条里已存的音频 URL；个别缺失时用有道 TTS 即时合成兜底 |
| 音标来源 | 有道词典权威 IPA（英/美两套），全部 1802 个单字已核对替换 |
| 网络要求 | 国内可正常访问（Google TTS 在国内被墙，已弃用） |

> 音标和发音均以**英美真实发音**为准，适合边听边记。

### 4. 批量掌握
想一次性标记一批单词为已掌握？点工具栏 **✅ 批量掌握**，进入选择模式——每个卡片出现复选框，**勾选任意多个**单词，点「标记已掌握」统一完成。适合「这一批我其实都会，只是没一个个点」的情况。支持「全选当前」一键勾选当前筛选下所有未掌握的词。

### 5. 导出未掌握单词（重点复习）
点工具栏 **📄 导出未掌握**，把当前级别没掌握的单词导出成 TXT（**每个单词一行**），文件名自动带级别和数量（如 `level2-未掌握-187词.txt`）。
- 可以发到微信 / 备忘录 / 打印出来，按自己节奏复习
- 手机自动调起分享，电脑直接保存文件

### 6. 搜索 & 筛选
- 顶部搜索框：按**单词或中文释义**搜索
- 筛选按钮：**全部 / 未掌握 / 已掌握**，只看想看的

### 7. 换设备不丢进度
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
| `words.js` | 词汇数据（2053 词，含标准音标、词性、释义、英美发音） |
| `README.md` | 项目说明 |
| `NETLIFY.md` | 免费部署详细教程 |

## 📖 词汇数据说明

词汇来自 TOEIC 备考书 **《出る単特急 金のフレーズ》/《銀のフレーズ》**（TEX 加藤 著），按分数分三档，每条包含：

| 字段 | 说明 |
|---|---|
| `word` | 单词 |
| `phonetic` | 标准 IPA 音标（英式，`uk` 字段另存美式） |
| `pos` | 词性（如 名/動/形，多词性用 `/` 分隔） |
| `meaning` | 中文释义 |
| `example` | 学习笔记（**日文原文**） |
| `us` / `uk` | 美式 / 英式发音 URL |

**关于日文笔记（example）：**

- 约 **1447 个词条**的 `example` 字段是**原书的日文学习笔记**，**保留日文原文**，未翻译成中文
- 内容包括：派生词、同义词、用法提示、考点说明、例句等（如 `◎addition`、`★必出`、`×almost employees`）
- 因为原文是日文，**不懂日语的同学**直接看 example 可能不理解，可结合 `meaning`（中文释义）一起看，或用网页翻译工具辅助
- 这是刻意保留的——日文笔记信息密度高，且是原作者的考试经验总结

> 如需将日文笔记翻译成中文，或希望去掉日文只留中文/英文，可以后续按需处理。

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

### 3. US / UK pronunciation 🔊
Each word has two speaker buttons: 🔵 **US** / 🟣 **UK** — tap to hear it spoken. Phonetics show **both US and UK forms** (e.g. `schedule` UK `[ˈʃedjuːl]` / US `[ˈskedʒuːl]`), sourced from an authoritative dictionary.

**How pronunciation works:**

| Item | Details |
|---|---|
| Audio source | **Youdao dictionary real recordings** (`dict.youdao.com/dictvoice`), not machine TTS |
| UK audio | `dictvoice?audio=word&type=1` (real recording) |
| US audio | `dictvoice?audio=word&type=2` (real recording) |
| Data storage | Each entry has `us` (US URL) and `uk` (UK URL) fields, loaded with `words.js` |
| Playback | Uses the entry's stored URL first; falls back to Youdao TTS synthesis for any missing ones |
| Phonetic source | Authoritative Youdao IPA (both US & UK), all 1,802 single words verified |
| Network | Works in mainland China (Google TTS is blocked there, so it was dropped) |

> Pronunciation and phonetics follow real US/UK audio — great for listening while you study.

### 4. One-click batch master
Want to mark a batch of words as mastered at once? Tap **✅ Batch Master** to enter selection mode — every card shows a checkbox. **Check any number of words**, then tap "Mark as mastered" to finish them all in one go. Perfect for "I actually know this batch, I just didn't tap each one." "Select All" grabs every unmastered word in the current filter.

### 5. Export unmastered words (focus review)
Tap **📄 Export Unmastered** to export the words you haven't mastered in the current level to a TXT file — **one word per line**. The filename includes the level and count (e.g. `level2-unmastered-187words.txt`).
- Send it to WeChat / Notes / print it, and review at your own pace
- On mobile it opens the system share sheet; on desktop it saves the file directly

### 6. Search & filter
- Search box: search by **word or Chinese definition**
- Filter buttons: **All / Unmastered / Mastered**

### 7. Never lose progress across devices
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
| `words.js` | Vocabulary data (2,053 words with standard IPA, POS, meanings, US/UK audio) |
| `README.md` | This readme |
| `NETLIFY.md` | Free deployment guide |

## 📖 Vocabulary Data

Words come from the TOEIC prep books **《出る単特急 金のフレーズ》/《銀のフレーズ》** (by TEX Kato), graded into three score levels. Each entry has:

| Field | Meaning |
|---|---|
| `word` | The word |
| `phonetic` | Standard IPA (UK; US stored in the `uk`/`us` fields) |
| `pos` | Part of speech (名/動/形, multi-POS separated by `/`) |
| `meaning` | Chinese definition |
| `example` | Study notes (**Japanese original**) |
| `us` / `uk` | US / UK pronunciation audio URLs |

**About the Japanese notes (`example`):**

- About **1,447 entries** have `example` notes written in **the original Japanese**, kept untranslated on purpose
- They contain derived words, synonyms, usage tips, exam points, and example sentences (e.g. `◎addition`, `★must-know`, `×almost employees`)
- If you don't read Japanese, they can be puzzling — use the `meaning` (Chinese) alongside, or a web page translator
- This is intentional: the Japanese notes are dense and carry the author's exam experience

> If you'd like the Japanese notes translated to Chinese, or stripped to keep only Chinese/English, that can be done on request.

## 🧰 Tech Stack

Plain HTML + CSS + JavaScript, zero dependencies, one file. Data lives in your browser; cross-device sync via file or GitHub Gist.

## ⚖️ License

[MIT](LICENSE)

---

*A small pure-frontend tool for everyone preparing for the TOEIC exam.*
