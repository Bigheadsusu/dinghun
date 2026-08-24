# 结婚喜宴邀请函 · dinghun

纯静态 **中式风格 · 红色喜庆** 婚礼电子邀请函（单页 HTML），无需构建、无需后端，适合直接通过微信 / QQ / 二维码分享给亲友。

> 仓库地址：https://github.com/Bigheadsusu/dinghun
> 在线预览：`https://bigheadsusu.github.io/dinghun/ylj.html`

---

## 功能特性

| 功能 | 说明 |
| --- | --- |
| 📜 单页滚动 | 封面 → 中式插画画廊 → 婚宴信息卡，一页浏览，无翻页依赖 |
| 👫 新人信息 | 封面醒目展示 **魏永森 & 叶湄敏**，含「吾家有喜」祝福语 |
| 📅 婚期时间 | 2026 年 10 月 1 日（农历八月廿一）星期四 12:00 午宴 |
| 📍 宴席地点 | 永泰县长庆镇人民政府东 50 米 永泰县（附地图导航链接） |
| 🖼 中式插画 | 9 张红金中式插画网格展示，点击可放大查看 |
| 🎵 背景音乐 | 点击右上角音乐按钮播放 / 暂停（自动播放被拦截时，首次点击恢复） |
| 📱 响应式 | 移动端 2 列、桌面端 3 列画廊，均正常显示 |
| 🔗 微信分享 | 完整 Open Graph / itemprop Meta，分享卡片显示标题、封面与摘要 |
| 🚫 零外部依赖 | 无 CDN、无第三方库，全部 CSS / JS 内联，图片全本地加载 |

---

## 目录结构

```text
dinghun/
├── ylj.html                    # 唯一页面（自包含 CSS/JS + 微信 Meta）
├── show/                       # 图片素材（全部为小写扩展名，保证 GitHub Pages 可加载）
│   ├── cover.jpg               # 封面合影相框图
│   ├── mobile_01.jpg ~ mobile_09.jpg   # 9 张中式插画
│   ├── mobile_end.jpg          # 婚宴信息卡背景图
│   ├── remark_01.png ~ remark_06.png   # 插画上的文字装饰贴图
│   └── musicon.png / musicoff.png      # 音乐开关图标
├── assets/
│   ├── audio/bgm.mp3           # 背景音乐
│   └── img/og-ylj.png          # 分享封面 / favicon
├── .github/workflows/static.yml# GitHub Pages 自动部署
├── README.md
└── .gitignore
```

> 仅保留 `ylj.html` 一个 HTML 文件；无 CDN 依赖，图片使用相对路径（`show/*.jpg`）。

---

## 在线预览

通过 GitHub Pages 自动部署：

- 邀请函页面：<https://bigheadsusu.github.io/dinghun/ylj.html>

向 `main` 分支推送后，GitHub Actions 会自动发布。

---

## 本地预览

```bash
cd dinghun
python3 -m http.server 8000
# 浏览器打开 http://localhost:8000/ylj.html
```

建议使用 Chrome / Edge 的“手机模拟器”模式查看，效果最佳。

---

## 自定义修改指南

### 1. 修改新人信息
编辑 `ylj.html`，搜索并替换 `魏永森` / `叶湄敏`（含 `<title>`、Meta、封面与落款）。

### 2. 修改日期 / 时间
搜索 `2026.10.01`、`农历八月廿一`、`10月1日`、`12:00 午宴`、`星期四` 并同步替换。

### 3. 修改宴席地点
搜索 `永泰县长庆镇人民政府东50米` 与 `永泰县`；地图导航链接在 `.nav-btn` 的 `href` 中。

### 4. 替换图片
- 封面合影：`show/cover.jpg`
- 场景插画：`show/mobile_01.jpg` ~ `mobile_09.jpg`（画廊顺序与 `remark_*.png` 装饰对应）
- 信息卡背景：`show/mobile_end.jpg`
- 分享封面 / favicon：`assets/img/og-ylj.png`

> ⚠️ 注意：GitHub Pages 服务器区分文件名大小写，新增图片请使用**小写扩展名**（如 `.jpg` / `.png`）。

### 5. 替换背景音乐
替换 `assets/audio/bgm.mp3`（保持文件名，或同步修改 `<audio>` 的 `src`）。

### 6. 微信分享卡片
已内置 `og:title / og:description / og:image / og:url` 与 `itemprop` Meta；如需自定义分享图片，替换 `assets/img/og-ylj.png` 并同步更新 `og:image` 的完整线上地址。

---

## 部署

```bash
git add -A
git commit -m "重构 ylj 邀请函：单页中式红金风格，修复图片大小写加载问题"
git push origin main
```

部署状态可在仓库 **Actions** 标签页查看。

---

## 图片加载问题修复说明

原页面引用 `show/mobile_01.jpg` 等小写路径，但仓库内文件实际为 `mobile_01.JPG`（大写）。本地 Windows 文件系统不区分大小写可正常显示，而 GitHub Pages（Linux）严格区分，导致**仅 `cover.jpg` 一张能加载，其余全部 404**。本次已将所有图片统一重命名为小写扩展名，并在 HTML 中验证所有引用与实际文件大小写完全一致。

---

## 模板来源与声明

- 场景插画素材来自 GitHub 开源项目 [`leo-yi/reliy`](https://github.com/leo-yi/reliy)（中式婚礼 H5 模板），已重排为单页布局。
- 模板图片仅供示例，如需商用请确保拥有相应图片版权。

---

## 许可证

未指定许可证。如需开源分享，建议在仓库添加 `LICENSE`（例如 MIT）。
