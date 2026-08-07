# Netlify 部署指南（TOEIC 托业词汇）

把本应用免费部署到 Netlify，获得一个 `https://xxx.netlify.app` 网址，手机电脑都能访问，且进度同步功能（localStorage）在 https 下才能可靠工作。

**全程免费，不需要信用卡。**

---

## 目录

1. [Netlify 是什么 / 免费吗](#1-netlify-是什么--免费吗)
2. [方式 A：Netlify Drop 手动部署（最快，不用注册）](#2-方式-anetlify-drop-手动部署最快不用注册)
3. [方式 B：连接 GitHub 自动部署（推荐，长期省心）](#3-方式-b连接-github-自动部署推荐长期省心)
4. [更新网站（两种情况）](#4-更新网站两种情况)
5. [自定义域名（可选）](#5-自定义域名可选)
6. [常见问题](#6-常见问题)

---

## 1. Netlify 是什么 / 免费吗

- **Netlify** 是一个静态网站托管平台，你上传 HTML/JS/CSS，它帮你托管并配好 HTTPS。
- **免费档（Free/Starter）**：**不需要信用卡**，免费提供无限站点、每月 100GB 带宽、自动 HTTPS。个人小应用完全够用。
- 你在官网看到的"付费套餐"页面是可选升级，**不是必须**。
- 用 **Google 账号**即可登录注册（这就是你之前遇到的"要登录"——那是登录 Netlify 后台管理你的站点，**不是访问者要登录**。部署完的 `.netlify.app` 网址对游客完全开放）。

---

## 2. 方式 A：Netlify Drop 手动部署（最快，不用注册）

> 适合：第一次试水、快速拿到一个网址。

**步骤：**

1. 打开浏览器访问 **https://app.netlify.com/drop**（不需要先注册）
2. 把本项目文件夹里的 **`index.html` 和 `words.js` 两个文件一起** 拖进页面中央的虚线框
3. 松开鼠标，等几秒，Netlify 会自动生成一个随机网址，形如：
   ```
   https://abcdef0123.netlify.app
   ```
4. 点开网址即可使用

> ⚠️ **必须两个文件一起拖**：`index.html` 引用了 `words.js`，缺一个页面就加载不出词汇。
>
> 💡 未登录时生成的站点是"临时"的；建议顺手用 Google 账号登录一下，站点才会绑定到你的账号、长期保留。

---

## 3. 方式 B：连接 GitHub 自动部署（推荐，长期省心）

> 适合：代码已在 GitHub，以后改代码 `git push` 一下，网站**自动更新**，不用再手动拖文件。

**前提**：代码已推送到 GitHub 仓库（本项目即 `JLXYwjw/toeicvocabulary`）。

**步骤：**

1. 登录 https://app.netlify.com （用 Google）
2. 点页面右上角 **Add new site**（或首页的 **Import an existing project**）
3. 选择 **Import from Git** → **GitHub**
4. 浏览器会弹出 GitHub 授权页 → **Authorize Netlify**（授权 Netlify 读取你的仓库）
   - 若没看到你的仓库，检查 GitHub 的 "Authorized OAuth Apps" 里是否已授权
5. 在仓库列表里选中 `toeicvocabulary`（或你的仓库名）
6. 进入部署配置页，**保持默认**即可：
   - Branch: `main`
   - Build command: 留空（本项目无构建）
   - Publish directory: 留空（直接发布仓库根目录）
7. 点 **Deploy site**
8. 等一两分钟，部署完成，获得 `https://xxx.netlify.app`

**以后更新：**

本地改完代码后执行：

```bash
git add .
git commit -m "改了啥"
git push
```

Netlify 检测到 `main` 分支有更新，会自动重新部署，**无需任何手动操作**。

---

## 4. 更新网站（两种情况）

### 情况 1：用的是 Netlify Drop（手动部署）

1. 登录 https://app.netlify.com → **Sites** → 点进你的站点
2. 进入 **Deploys** 页签
3. 找到 **"Drag and drop your site output folder here"** 区域
4. 把**最新**的 `index.html` + `words.js` 拖进去 → 覆盖部署
5. 部署完成后刷新网址（手机用浏览器刷新，必要时清缓存）

### 情况 2：用的是 GitHub 自动部署

直接 `git push`，Netlify 自动更新（见第 3 节）。

---

## 5. 自定义域名（可选）

免费档支持绑定自己的域名（需已购买）：

1. **Sites** → 进入站点 → **Domain settings** → **Add a domain**
2. 按提示添加你的域名
3. 到你的域名服务商后台，添加一条 CNAME 记录指向 `xxx.netlify.app`（或按 Netlify 提示配置 DNS）
4. 等 DNS 生效（一般几分钟到几小时），即可用你自己的域名访问

> 不买域名也能正常用 `.netlify.app` 免费网址，本步骤可选。

---

## 6. 常见问题

**Q1：为什么打开网址要登录？**
不用。`.netlify.app` 网址对游客完全开放。需要登录的只有 Netlify **后台管理**（那是你自己的账号），以及**你主动在 GitHub 同步里填的 token**。

**Q2：手机上进度保存不了？**
检查网址是不是 `https://` 开头（Netlify 默认就是）。localStorage 只有在 https（或 localhost）下才可靠。若在 `http://` 的局域网地址测试，属正常现象。

**Q3：`words.js` 加载失败 / 页面空白？**
多半是部署时只传了 `index.html` 没传 `words.js`，或两者不在同一目录。重新把两个文件一起拖 / 一起 push。

**Q4：如何取消/删除部署的站点？**
后台 **Sites** → 站点 → **Site configuration** → **Danger Zone** → **Delete site**。

**Q5：免费档会被收费吗？**
不会。免费档一直免费，无需信用卡。只有主动升级到付费套餐才收费。

---

*如有其它问题，可在 [Netlify 官方文档](https://docs.netlify.com) 查询。*
