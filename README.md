# 订婚喜宴邀请函 · dinghun

一个纯静态、零依赖的**中式订婚喜宴电子邀请函**网站，开箱即用、可直接通过链接 / 二维码分享给亲友。项目包含两个风格不同的邀请页面、背景音乐、倒计时、飘落花瓣 / 星光特效与互动刮刮乐。

> 仓库地址：https://github.com/Bigheadsusu/dinghun
> 在线预览（GitHub Pages，部署后生效）：
> - 主页面：`https://bigheadsusu.github.io/dinghun/`
> - 备用页面：`https://bigheadsusu.github.io/dinghun/ylj.html`

---

## 功能特性

| 功能 | 说明 |
| --- | --- |
| 💌 双风格邀请页 | `index.html`（全红描金·林虹 & 叶林锦）与 `ylj.html`（米红暖调·叶林锦 & 林虹），可任选其一或并存 |
| ⏳ 吉日倒计时 | 自动计算距离订婚日的天/时/分/秒，过期后显示祝福语 |
| 🎵 背景音乐 | 点击页面任意处或音乐按钮即可播放/暂停（遵循浏览器自动播放策略） |
| 🌸 视觉特效 | 飘落花瓣、金色星光粒子、灯笼/祥云/梅花装饰 |
| 🎫 互动刮刮乐 | `ylj.html` 内置“喜相逢·幸运刮刮乐”，点击刮开随机感谢语并撒花 |
| 🗺️ 一键导航 | 内置高德地图短链，点击直达宴席地点 |
| 📱 移动端优化 | 响应式布局、适配刘海屏（`viewport-fit=cover`）、触摸交互 |
| 🔗 社交分享卡片 | 配置 Open Graph / Schema.org Meta，微信、QQ 等分享时显示封面与标题 |

---

## 目录结构

```text
dinghun/
├── index.html                  # 主邀请页（全红描金风格）
├── ylj.html                    # 备用邀请页（米红暖调 + 刮刮乐）
├── assets/                     # 统一管理的静态资源
│   ├── audio/
│   │   └── bgm.mp3             # 背景音乐
│   └── img/
│       ├── cover.jpg           # 分享封面 / 网站图标（favicon）
│       ├── og-ylj.png          # ylj.html 的分享封面图
│       └── _unused-cover.jpg   # ⚠️ 当前未被引用，可安全删除（见“待改进”）
├── .github/
│   └── workflows/
│       └── static.yml          # GitHub Pages 自动部署工作流
├── README.md
└── .gitignore
```

> 说明：两个 HTML 文件刻意保持**单文件自包含**（CSS/JS 内联），方便作为单个链接或文件直接转发给亲友，无需额外加载本地资源文件。

---

## 在线预览

本项目通过 GitHub Pages 自动部署。向 `main` 分支推送后，GitHub Actions 会自动构建并发布：

- 主页面：<https://bigheadsusu.github.io/dinghun/>
- 备用页面：<https://bigheadsusu.github.io/dinghun/ylj.html>

首次启用 Pages：仓库 **Settings → Pages → Build and deployment → Source 选择 “GitHub Actions”** 即可（工作流已就位）。

---

## 本地预览

> ⚠️ 资源（音乐、图片）在 HTML 中使用**绝对地址** `https://bigheadsusu.github.io/dinghun/...`。
> 因此在本地直接双击打开 `index.html`（`file://` 协议）时，音乐与封面图**不会加载**——它们要到部署到 GitHub Pages 后才可用。
> 本地预览推荐做法：**先部署一次到 Pages**，再用手机/浏览器打开线上地址；或临时将资源地址改为相对路径（见下方“自定义”）。

简单本地服务器（图片/音乐仍走线上绝对地址，仅用于查看布局）：

```bash
# 在项目根目录执行
python3 -m http.server 8000
# 浏览器打开 http://localhost:8000/
```

---

## 自定义修改指南

所有内容均为**纯文本/常量**，直接编辑对应 HTML 即可，无需构建工具。

### 1. 新人姓名
- `index.html`：搜索 `林虹` / `叶林锦`（位于 `.names-big` 与 `.parents-announce` 区）。
- `ylj.html`：搜索 `叶林锦` / `林虹`（位于 `.couple-names` 与 `.announcement` 区）。

### 2. 订婚日期与时间
- 页面展示文字：搜索 `2026年05月01日`、`2026.5.1`、`12:00`、`17:00`、`农历三月十五`、`星期五`。
- **倒计时目标（关键）**：`index.html` 脚本中的
  ```js
  const targetDate = new Date(2026, 4, 1, 12, 0, 0); // 月份从 0 开始：4 = 5 月
  ```
  > ⚠️ **务必让这里的年份/月份/时间与页面文字一致**，否则倒计时会提前或延后显示“吉日已至”。

### 3. 宴席地点与导航
- 地点文字：搜索 `柳浪望江楼`、`野猪湾村庄`、`G1523...`。
- 高德导航短链：搜索 `surl.amap.com`，替换为自己的高德地图分享短链（两页各一个）。

### 4. 背景音乐
- 替换 `assets/audio/bgm.mp3`（保持文件名，或同步修改 HTML 中 `<audio>` / `<source>` 的 `src`）。
- 建议使用无版权/已获授权的喜庆纯音乐。

### 5. 分享封面图
- 替换 `assets/img/cover.jpg`（两页共用，同时作为 favicon）与 `assets/img/og-ylj.png`（`ylj.html` 专用）。
- 改完记得同步修改两页 `<meta property="og:image">` 与 `<link rel="icon">` 指向的文件名（若改名）。

### 6. 配色风格
- 两页配色均为 CSS 变量化的纯色值，集中在 `<style>` 顶部与各区块注释处，按需调整即可。

---

## 部署

已内置 GitHub Pages 工作流（`.github/workflows/static.yml`），推送即部署：

```bash
git add -A
git commit -m "优化邀请函：修复倒计时年份、整理资源、完善文档"
git push origin main
```

部署状态可在仓库 **Actions** 标签页查看；发布地址即上方“在线预览”中的 GitHub Pages 链接。

---

## 已知问题与待改进

以下为本次优化中**已修复**与**仍需人工确认**的清单：

### ✅ 本次已修复
1. **倒计时年份错误（严重）**：`index.html` 倒计时原目标为 `2025-05-01`，与页面显示的 `2026年05月01日` 不符，导致倒计时提前一年显示“吉日已至”。已修正为 `2026`。
2. **死代码**：`index.html` 中 `setWeekdayText()` 引用了并不存在的 `weekdayShow` 元素，且月份写错（写成 6 月），属无效代码，已删除。
3. **音乐按钮逻辑缺陷（ylj.html）**：`updateMusicButton()` 用 `innerHTML` 重写按钮，导致内部 `musicText` 文本节点被孤立、后续更新失效。已重构为只更新文本与图标 class。
4. **资源命名与结构混乱**：原 `1.mp3` / `cover(1).jpg` / `1(1).png` / `cover.jpg` 命名含下载冗余后缀且混在根目录；已归入 `assets/` 并规范化命名。
5. **缺失基础 Meta**：两页均补充了 `description`、`theme-color`、favicon，并将 `lang` 统一为 `zh-CN`。

### ⚠️ 仍需人工确认 / 建议改进
1. **两页开席时间不一致（最重要）**：`index.html` 显示 **12:00**，`ylj.html` 显示 **17:00**。请确认实际开席时间，并将两页统一；倒计时脚本 `targetDate` 的小时也要同步。
2. **未使用资源 `assets/img/_unused-cover.jpg`**：原始 `cover.jpg` 在项目中无任何引用，可安全删除（如需保留作备份请移出 `assets`）。
3. **`user-scalable=no` 与全局 `user-select: none`**：为移动端沉浸体验关闭了缩放与文本选择，对无障碍（如视力障碍用户）不友好。如非必要可去掉 `user-scalable=no`。
4. **`ylj.html` 依赖外部 CDN（Font Awesome）**：图标来自 `cdnjs`，离线或 CDN 故障时图标会丢失。可考虑替换为 Emoji（如 `index.html` 的做法）或自托管图标字体。
5. **“刮刮乐”实为点击揭晓**：`ylj.html` 的刮刮乐是“点击即揭开”，并非真正的画布涂抹刮卡。若需真实刮卡手感，可用 `<canvas>` 实现涂抹擦除。
6. **农历日期为手写常量**：`农历三月十五` 为人工填写，未做农历换算。若日期变更，需自行核对农历。
7. **缺少测试与 CI 校验**：目前工作流仅做静态部署，可后续加入 HTML 校验（如 `htmlhint` / `w3c` 检查）提升质量。

---

## 许可证

未指定许可证。如需开源分享，建议在仓库添加 `LICENSE`（例如 MIT）并据此使用。
