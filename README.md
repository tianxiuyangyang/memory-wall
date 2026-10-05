# 回忆墙墙 · MEMORY WALL

一个单页的高级感小网站：主界面只有「回忆墙墙」四个字，轻触后触发金色碎光特效，两张照片从光里浮出，组成一面"墙"。

## 打开方式

直接双击 `index.html` 即可（无需服务器、无需构建、无外部依赖）。
若想用本地服务器：在目录里执行 `python -m http.server 8000`，然后访问 `http://localhost:8000/`。

## 交互

| 操作 | 效果 |
| --- | --- |
| 点击 / 轻触屏幕（或按 Enter、空格） | 闪光 + 金色碎光四散，四字化光，照片从景深中浮出 |
| 鼠标移动 | 主界面微视差；回忆墙里相框跟着光标轻微 3D 倾斜，相纸上有反光 |
| 点击相框 | 打开大图（Esc 或点背景关闭） |
| 「重新封存」 | 光尘归拢，照片退回深处，回到「回忆墙墙」 |
| 右上角「音效」 | 开关合成音效（Web Audio 实时合成，无音频文件） |

## 文件结构

```
index.html          页面结构
css/style.css       全部样式（配色、相框、动效）
js/app.js           粒子系统、开启/收回编排、音效、大图查看
assets/memory-1.jpg 第一张回忆
assets/memory-2.jpg 第二张回忆
```

## 换成自己的照片

1. 把图片放进 `assets/`，建议宽高比约 20:9 或更宽（会自动裁切填满相框）。
2. 改 `index.html` 里两个 `<figure class="frame-wrap">` 的 `data-src`、`<img src>`、`data-cap` 和下方 `<figcaption>` 里的编号与标题。

## 可以调的地方

- 主标题：`index.html` 中的 `<h1 class="title">`，每个字一个 `<span class="ch" style="--i:n">`，`--i` 决定描金扫光的错位节奏。
- 主题色 / 字号：`css/style.css` 顶部的 `:root` 变量（`--gold`、`--gold-2`、`--ink`）。
- 照片冷暖：`.frame-mat img` 的 `filter`。
- 已适配手机（相框自动竖排、双指缩放正常）与"减少动态效果"系统偏好。
