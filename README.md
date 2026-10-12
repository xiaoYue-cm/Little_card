# Little_card

几张独立的小卡片。每张就是一个单独的 HTML 文件，不依赖框架，也不用打包，塞进 iframe 就能跑。

## 用法

```html
<iframe src="https://xiaoyue-cm.github.io/Little_card/card.html?card=music"
        width="400" height="120" style="border:0" loading="lazy"></iframe>
```

把 `card` 换成下面表里的 id 就换一张卡，其余参数原样传给卡片。

> 先把 GitHub Pages 打开（Settings → Pages，Source 选 `main` / `root`）。不然 iframe 里只会显示源码。

## 卡片

| id | 名字 | 尺寸 | 长什么样 |
|---|---|---|---|
| `music` | 音乐播放 | 400 × 120 | 平时只有一张唱片，点一下展开，右边抽出一块播放面板 |
| `heatmap` | 贡献热力图 | 680 × 340 | 年 / 月两种视图。窗口变窄就整张缩小，格子不动 |

## 参数

| 参数 | 说明 |
|---|---|
| `card` | 选哪张卡，必填 |
| `u` | 缩放基准，1 是默认大小，不填就按宽度自动缩 |
| `bg` | `transparent` 去掉 demo 底色，放在 iframe 里时自动打开 |
| `src` / `title` / `artist` | music 专用：音频直链、曲名、艺人。不给 `src` 就没声音 |
| `user` | heatmap 专用：看谁的贡献，默认 `xiaoYue-cm` |

## 文件

```
index.html      画廊：预览、参数表、一键复制 iframe
card.html       iframe 入口：?card=<id> 选卡
cards.js        卡片注册表
cards/*.html    每张卡片
```

## 加一张新卡

卡片放进 `cards/`，再到 `cards.js` 加一条注册项。
