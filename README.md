# Little_card

几张自己的小卡片喵。每张就是一个单独的 HTML 文件哦~

## 用法

```html
<iframe src="https://xiaoyue-cm.github.io/Little_card/card.html?card=music"
        width="400" height="120" style="border:0" loading="lazy"></iframe>
```

把 `card` 换成下面表里的 id 就换一张卡喵，其余参数原样传给卡片喵~

> 先把 Pages 打开喵，不然 iframe 里只会显示源码喵。

## 卡片

| id | 名字 | 尺寸 | 长什么样 |
|---|---|---|---|
| `music` | 音乐播放 | 400 × 120 | 平时只有一张唱片，点一下展开，右边抽出一块播放面板喵 |
| `heatmap` | 贡献热力图 | 680 × 340 | 年 / 月两种视图，窗口变窄就整张缩小，格子没写惹qwq |

## 参数

| 参数 | 说明 |
|---|---|
| `card` | 选择参数喵 |
| `u` | 默认大小是1，不填就按宽度自动缩喵 |
| `bg` | `transparent` 去掉 demo 底色，放在 iframe 里时自动打开哦~ |
| `src` / `title` / `artist` | 音频直链，用音乐卡片又不传SRC等着听空气喵(不传听棍木呢你) |
| `user` | 用来看贡献，不传默认原作者喵 |

## 文件

```
index.html      画廊：预览、参数表、一键复制 iframe
card.html       iframe 入口：?card=<id> 选卡
cards.js        卡片注册表
cards/*.html    每张卡片
```

## 加一张新卡

卡片放进 `cards/` 喵，再到 `cards.js` 加一条注册项喵。
