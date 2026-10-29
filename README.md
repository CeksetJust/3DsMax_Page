# 3dsmax 学习日志 · 网页

纯静态站点，双击 `index.html` 就能在浏览器里打开，不需要装任何环境。

## 页面结构

```
3dsmax-log/
├── index.html          首页：顶部展示图片 + 标题「3dsmax学习日志」+ 卡片「建模」
├── modeling.html       建模页：卡片「沙发」
├── sofa.html           沙发页：练习目标 / 步骤 / 截图 / 踩坑记录 / 小结
├── bookshelf.html      书柜页：练习目标 / 步骤 / 结果截图
├── phone.html          手机页：练习目标 / 步骤 / 结果截图
├── computer.html       电脑页：练习目标 / 步骤 / 结果截图
└── assets/
    ├── css/style.css   全站样式（改 :root 里的 --accent 就能整体换主色）
    └── img/
        ├── hero-sofa.png  首页展示图原图（2550×1378，从 D:\画画 复制过来的）
        └── hero-sofa.jpg  首页实际引用的压缩版（1920×1038，约 280KB）
```

页面跳转关系：

```
index.html --卡片「建模」--> modeling.html
                                  ├─ 沙发 --> sofa.html
                                  ├─ 书柜 --> bookshelf.html
                                  ├─ 手机 --> phone.html
                                  └─ 电脑 --> computer.html
```

## 常见修改

- **换首页展示图**：把新图片放进 `assets/img/`，然后改 `index.html` 里 `hero__banner` 那张 `<img>` 的 `src`；
  建议用 1920px 宽左右的 jpg，几 MB 的图会让首屏加载变慢。
- **首页顶部图片 / 导航栏**：首页 `<body>` 带 `page-home` 类，导航栏透明叠在展示图片上方，图片左右与上方都通栏。
  图片高度上限在 `.hero__banner img` 的 `max-height`，图片顶部那层淡白蒙版是 `.page-home .hero__banner::after`（换成暗图时把它的透明度调高一点，导航才看得清）。
  另外 `index.html` 末尾有一小段脚本：把导航实际高度写进 `--header-h`（避免图片顶部露出空隙），并在页面滚动后给导航加上 `.is-solid` 换成白底。
- **改标题**：首页标题是 `index.html` 里的 `<title>` 和 `<h1 class="hero__title">`，两处一起改。
- **加新卡片**：复制 `<a class="card">` 整块，改 `card__index`、`card__title`、`card__desc` 和 `href`，
  再照着 `sofa.html` 复制一份新页面即可；`.card--todo` 是虚线占位卡片的样式。
- **换配色**：`assets/css/style.css` 顶部 `:root` 里调 `--accent`（主色）和 `--bg`（背景色）。
- **页脚年份**：三个页面底部的 `© 2026` 按需修改。

> 注意：`singularity-wiki/` 是另一个独立站点（奇点异客工作室百科），和本站互不影响。
