# Clash Verge — Ingrid Theme

![banner](wallpaper/wallpaper.jpg)

> *灵感来源于《Street Fighter 6》中 Ingrid 的水晶幻境——她每一次瞬移都留下半透明的光晕，像凝固的玻璃碎片。这套 Clash Verge 主题把这种感觉搬到了代理面板上：每一张卡片都是一片"水晶"，底下透出您的壁纸。*

---

## 🇨🇳 简体中文简介

**Clash Verge 毛玻璃主题 · Ingrid 版**

> 灵感来自《街头霸王 6》的 **Ingrid（英格丽德）**——每一次瞬移都留下半透明白色光晕，像凝固的水晶碎片。本主题把这种感觉搬到了 Clash Verge 的代理面板上：每一张卡片都是一片"水晶"，底下透出您的壁纸。

### 这是什么？

一份**纯 CSS 注入**的毛玻璃主题，专为 [Clash Verge](https://github.com/clash-verge-rev/clash-verge-rev) 设计。不修改任何源代码，不依赖任何外部资源——您只需要把一份 CSS 粘贴进"主题设置 → CSS 注入"，整套界面瞬间换皮。

### 为什么做这个？

默认的 Clash Verge 主题是 MUI 默认色 + 灰底卡片，代理列表一眼望上去密密麻麻像表格。希望让它变成这样：

- 卡片像一片**浮在壁纸上的薄玻璃**，能透出您精心挑的壁纸
- 节点名不会因为"压暗的次级文字"而看不清
- 顶部标题栏也是壁纸的一部分，**整个窗口真正"无缝一体"**
- 想换壁纸/换配色/调整磨砂浓度，**改一行 CSS 变量**就行

### 适合谁？

- 喜欢自定义界面、但不想折腾编译/打包 Clash Verge 源码的人
- 想让代理面板跟自己的壁纸协调一致的视觉控
- 觉得官方主题文字偏暗、节点名辨识度不够的人
- 喜欢街霸6、想用 Ingrid 的水晶质感做点什么的粉丝

### ✨ 主要特性

- 全屏**毛玻璃**效果（卡片、弹窗、菜单、悬浮层）
- **壁纸铺满整个窗口**——包括顶部标题栏
- **微调透明度**：壁纸隐约可见，文字不会糊掉
- **节点名强制提亮**：Selector 旁边的小字不再暗淡
- 单一 `theme.css` 文件，**纯 CSS 注入**，无依赖、无 JS
- 顶部 CSS 变量一行就能换壁纸、改配色、调整磨砂程度

### 🚀 一句话安装

1. **设置 → 界面设置 → 把第一项「优先使用系统标题栏」关掉**（这一步让壁纸能覆盖顶栏）
2. **设置 → 主题设置 → CSS 注入 → 把 `theme.css` 整份粘贴进去 → 保存**

详细教程往下翻（英文版教程往下滚；如需完整中文文档请切换到 [`README.zh-CN.md`](./README.zh-CN.md)）。

---

A frosted-glass CSS theme for [Clash Verge](https://github.com/clash-verge-rev/clash-verge-rev) inspired by **Ingrid** from *Street Fighter 6*. Every panel is a frozen shard of light, the wallpaper peeks through underneath, and the proxy list reads like a battlefield of crystalline teleports.

---

## 📸 Previews

### Proxies page

![Proxies preview](docs/preview-proxies.png)

### Settings overview

![Overview preview](docs/preview-overview.png)

---

## ✨ Features

- **Frosted glass** on every card, dialog, and popover
- **Wallpaper bleeds across the entire window**, including the top title bar
- **Micro-tuned opacity**: you can still glimpse the wallpaper, but text never drowns
- **Force-bright secondary text** so node names next to "Selector" stay crisp
- **Easy re-skin** via CSS variables — change the wallpaper, accent colour, or panel density in one line
- Zero JavaScript, zero dependencies — pure CSS injection

---

## 🚀 Installation

### 1. Open the custom title bar (required for full-screen wallpaper)

By default Clash Verge uses the **system title bar**, which sits *above* the webview and cannot be styled by CSS. To let the wallpaper cover the entire window (including the very top edge), you must disable it.

Open **Settings → Interface** and turn the **first toggle** off:

> **优先使用系统标题栏** → **OFF**

![Interface settings — disable system title bar](docs/interface-settings.png)

*(the exact menu label depends on your Clash Verge language; on the English build it's something like "Use system title bar". Once it is OFF, the title bar becomes part of the webview and our CSS can paint it transparent.)*

### 2. Paste the CSS

Open **Settings → Theme settings**, find the **CSS injection** field, click the pencil icon, and paste the **entire** contents of [`theme.css`](./theme.css). Save.

The theme takes effect immediately — no restart needed.

For reference, here is what the **Theme settings** dialog looks like in our setup:

![Theme settings dialog](docs/theme-settings.png)

---

## 🖼 Using your own wallpaper

The bundled wallpaper lives in `wallpaper/wallpaper.jpg`. To use your own:

1. Replace `wallpaper/wallpaper.jpg` with your image (keep the same filename, or update the path below)
2. Or change the path in `theme.css`:

```css
--cv-wallpaper: url("http://asset.localhost/$(pwd)/wallpaper/wallpaper.jpg");
```

Common path formats:

| OS | Example |
| --- | --- |
| Windows | `url("http://asset.localhost/C%3A%5CUsers%5CPublic%5CPictures%5Cmy-image.jpg")` |
| Linux | `url("file:///home/you/Pictures/my-image.jpg")` |
| macOS | `url("file:///Users/you/Pictures/my-image.jpg")` |

Tip: in Clash Verge's Custom CSS field, `$(pwd)` resolves to the directory of the CSS file, so you can ship the theme + wallpaper together.

The CSS already ships with a two-layer fallback chain:

```css
--cv-wallpaper:
  url("http://asset.localhost/$(pwd)/wallpaper/wallpaper.jpg"),                                  /* local bundle */
  url("https://fastly.jsdelivr.net/gh/TTNAN/clash-verge-ingrid-theme@main/wallpaper/wallpaper.jpg"); /* CDN mirror */
```

If the bundled wallpaper file is missing, the jsDelivr mirror kicks in automatically — no blank theme.

---

## 🎨 Customisation cheat-sheet

All visual tweaks are CSS variables at the top of `theme.css`.

### Wallpaper
```css
--cv-wallpaper: url("...");  /* your image */
--cv-wp-filter: none;          /* e.g. blur(4px) brightness(0.85) */
--cv-scrim:    rgba(6, 8, 14, 0.10);  /* dark overlay on top of wallpaper */
```

### Glass density

| Variable | Default | Effect |
| --- | --- | --- |
| `--cv-panel` | `rgba(255,255,255,0.06)` | Card backgrounds |
| `--cv-subpanel` | `rgba(255,255,255,0.08)` | Inner lists |
| `--cv-row-bg` | `rgba(255,255,255,0.06)` | Proxy row strip |
| `--cv-chip-bg` | `rgba(255,255,255,0.14)` | Small tags |
| `--cv-input-bg` | `rgba(0,0,0,0.40)` | Input fields |
| `--cv-overlay-bg` | `rgba(18,20,28,0.86)` | Dialogs / menus |
| `--cv-tooltip-bg` | `rgba(13,15,22,0.96)` | Tooltips |
| `--cv-sticky-bg` | `rgba(10,12,18,0.65)` | Sticky bars |

> Increase the last number in each `rgba(...)` to make the surface **more opaque** (less wallpaper visible). Decrease it for a more ghostly look.

### Accent colour
```css
--cv-accent:  #5ab0f8;   /* primary highlight (selected, borders, underlines) */
--cv-success: #3fd3a8;   /* "connected" green */
--cv-error:   #ff6b80;   /* "failed" red */
```

### Geometry
```css
--cv-radius:  16px;  /* card corner radius */
--cv-gap:      5px;   /* spacing between rows */
--cv-row-pad:  12px;  /* vertical padding inside proxy cards */
--cv-border:   rgba(255,255,255,0.37);
```

---

## 🧠 How it works (in one paragraph)

`body::before` paints the wallpaper as a fixed background with `z-index: -2`. `body::after` adds a translucent dark scrim on top. Every MUI panel / card / list item is then forced to `background: transparent`, so the wallpaper shines through. A thin white border + soft shadow is layered on top to give the illusion of frosted glass without ever needing `backdrop-filter` (which is unreliable inside Tauri webviews).

The bottom of `theme.css` contains two surgical patches:

1. A **wide-net titlebar selector** that turns the custom (non-system) title bar fully transparent so the wallpaper flows edge-to-edge. This is why step **1** of the install instructions asks you to disable the system title bar — without that, the title bar lives outside the webview and CSS cannot reach it.
2. A **MUI Typography force-bright** rule that keeps the small node-name text next to "Selector" readable, without painting the whole card white on hover.

---

## 📁 File layout

```
clash-verge-ingrid-theme/
├── README.md
├── LICENSE
├── theme.css                # ← drop this into Clash Verge
├── wallpaper/
│   └── wallpaper.jpg        # bundled background
└── docs/
    ├── preview-proxies.png   # what the Proxies page looks like
    ├── preview-overview.png  # what the Settings page looks like
    ├── theme-settings.png    # reference: where to paste the CSS
    └── interface-settings.png  # reference: turn off system title bar
```

---

## 📜 License

MIT — see [`LICENSE`](./LICENSE).

The bundled `wallpaper/wallpaper.jpg` is included for personal use only; please replace it before redistributing if you don't hold the rights to the image.

---

## 🙏 Credits

- Inspired by **Ingrid** from *Street Fighter 6* by Capcom
- Built for [Clash Verge](https://github.com/clash-verge-rev/clash-verge-rev) / [Clash Verge Rev](https://github.com/clash-verge-rev/clash-verge-rev)
- MIT, do whatever you want