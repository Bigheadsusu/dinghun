# 结婚喜宴邀请函 · dinghun

纯静态 **中式婚礼 H5 电子邀请函**，基于开源模板 `leo-yi/reliy` 二次修改，适合直接通过微信 / QQ / 二维码分享给亲友。

> 仓库地址：https://github.com/Bigheadsusu/dinghun
> 在线预览：`https://bigheadsusu.github.io/dinghun/ylj.html`

---

## 功能特性

| 功能 | 说明 |
| --- | --- |
| 💌 中式 H5 翻页 | 10 屏竖向滑动 + 3D 翻页动画，含故宫红墙、中式屋檐、山水插画等喜庆画面 |
| 👫 新人信息 | 封面与结尾页醒目展示 **魏永森 & 叶湄敏** |
| 📅 婚期时间 | 2026 年 10 月 1 日（农历八月廿一）星期四 12:00 午宴 |
| 📍 宴席地点 | 永泰县长庆镇人民政府东 50 米 永泰县 |
| 🎵 背景音乐 | 点击右上角音乐图标可播放 / 暂停 |
| 🌸 氛围动效 | 页面切换动画、装饰性光圈闪烁、飘落感场景 |
| 📱 移动端优化 | 竖屏全屏适配，支持触摸上滑翻页 |
| 🔗 社交分享 | 配置 Open Graph Meta，分享时显示封面与标题 |

---

## 目录结构

```text
dinghun/
├── ylj.html                    # 邀请函主页面（多屏 Swiper H5）
├── css/
│   ├── animate.min.css         # animate.css 动画库
│   └── index.css               # 页面主样式
├── js/
│   └── jquery-3.2.1.min.js     # 模板依赖
├── images/
│   └── upArrow.png             # 上滑提示箭头
├── show/                       # 模板插画与装饰素材
│   ├── cover.jpg               # 封面底图
│   ├── mobile_01.jpg ~ mobile_09.jpg   # 9 张场景插画
│   ├── mobile_end.jpg          # 结尾页底图
│   ├── remark_01.png ~ remark_06.png   # 文字装饰贴图
│   └── musicon.png / musicoff.png      # 音乐开关图标
├── assets/
│   ├── audio/bgm.mp3           # 背景音乐
│   └── img/og-ylj.png          # 分享封面 / favicon
├── .github/workflows/static.yml# GitHub Pages 自动部署
├── README.md
└── .gitignore
```

> 模板 Swiper 4.5.0 与 swiper.animate 通过 **CDN** 加载，无需 npm 构建。

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
编辑 `ylj.html`，搜索并替换：
- `魏永森 & 叶湄敏`
- 新郎 / 新娘文案

### 2. 修改日期/时间
- 婚期：搜索 `2026.10.01`、`农历八月廿一`、`10月1日`、`12:00 午宴`
- 星期：当前为 **星期四**，如需修改请同步替换

### 3. 修改宴席地点
搜索 `永泰县长庆镇人民政府东50米` 与 `永泰县`。

### 4. 替换图片
- 封面 / 结尾背景：替换 `show/cover.jpg`、`show/mobile_end.jpg`
- 场景插画：替换 `show/mobile_01.jpg` ~ `mobile_09.jpg`
- 分享封面 / favicon：替换 `assets/img/og-ylj.png`

### 5. 替换背景音乐
替换 `assets/audio/bgm.mp3`（保持文件名，或同步修改 `ylj.html` 中 `<audio>` 的 `src`）。

---

## 部署

```bash
git add -A
git commit -m "重构 ylj 邀请函：采用中式翻页 H5 模板，更新新人信息"
git push origin main
```

部署状态可在仓库 **Actions** 标签页查看。

---

## 模板来源与声明

- 翻页 H5 模板来自 GitHub 开源项目 [`leo-yi/reliy`](https://github.org/leo-yi/reliy)，基于其结构修改了新人信息、日期地点、结尾页，并移除了依赖后端的 RSVP 表单。
- 模板图片仅供示例，如需商用请确保拥有相应图片版权。

---

## 许可证

未指定许可证。如需开源分享，建议在仓库添加 `LICENSE`（例如 MIT）。
