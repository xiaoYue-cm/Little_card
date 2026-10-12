# Little_card

一堆自包含的小卡片。每张卡片是一个单独的 HTML 文件，不依赖框架、不依赖构建，用 iframe 就能嵌进任何页面。

## 怎么用

```html
<iframe src="https://xiaoyue-cm.github.io/Little_card/card.html?card=music"
        width="400" height="120"
        style="border:0" loading="lazy"></iframe>
```

把 `card` 换成下表里的 id，其余参数原样转给卡片自己。

> **要先开 GitHub Pages**：仓库 Settings → Pages → Source 选 `main` / `root`，等一分钟拿到地址。
> 不打开的话，`raw.githubusercontent.com` 返回的是 `text/plain`，iframe 里只会显示源码。

## 卡片

| id | 名字 | 建议尺寸 | 说明 |
|---|---|---|---|
| `music` | 音乐播放卡片 | 400 × 120 | 默认只有一张唱片；悬停时正方形从唱片背后长出来，点击从右侧抽出一条播放面板，再点唱片收回 |
| `heatmap` | GitHub 贡献热力图 | 680 × 340 | 年 / 月两种视图切换；窗口窄了整体等比缩小，不重排格子 |

## 参数

**所有卡片通用**

| 参数 | 说明 |
|---|---|
| `card` | 要哪张卡片（必填） |
| `u` | 整卡缩放的基准单位，1 = 默认大小。不给的话按 iframe 宽度自动缩，最多 1 |
| `bg` | `transparent`：去掉 demo 底色。卡片检测到自己被 iframe 套着时会自动开 |

**`music` 独有**

| 参数 | 示例 | 说明 |
|---|---|---|
| `src` | `https://example.com/a.mp3` | 要放的音频直链。**不给就没有声音**，只走假进度演示动画 |
| `title` / `artist` | `title=Foo` | 覆盖面板里的曲名和艺人 |

**`heatmap`**

| 参数 | 示例 | 说明 |
|---|---|---|
| `user` | `user=octocat` | 显示谁的贡献，默认 `xiaoYue-cm` |

尺寸跟着 iframe 的宽度走（自带等比缩放），所以宽度给够就行。数据源两个都带 CORS，
静态页可以直接请求：贡献日历走 `github-contributions-api.jogruber.de/v4/<user>?y=<年>`，
用户资料走 `api.github.com/users/<user>`；连不上网会退回演示数据并在卡片上标注。

一个已知取舍：布局固定 53 列 = 371 格，遇到「闰年且 1 月 1 日是周日」的年份（2012、下一次 2040）
需要 54 列，会少掉 12 月 31 日那一格。

## 音频

仓库里不放任何音频文件，一是版权（示例那首是商业唱片），二是体积。想有声音就自己传直链：

```html
<iframe src="…/card.html?card=music&src=https://example.com/song.mp3" …></iframe>
```

跨域音频能直接播（`<audio>` 不需要 CORS），但对方的服务器要允许热链。

## 从 github-heatmap-card 搬过来的部分

`heatmap` 这张卡片原来单独放在 [xiaoYue-cm/github-heatmap-card](https://github.com/xiaoYue-cm/github-heatmap-card)，
内容和这里的是同一份（文件哈希一致），那个仓库已经弃用、准备删掉了（建了几天，没人用过，
所以没有外部页面依赖它的旧地址）。地址对应：

| 旧地址（已弃用） | 新地址 |
|---|---|
| `https://xiaoyue-cm.github.io/github-heatmap-card/` | `https://xiaoyue-cm.github.io/Little_card/card.html?card=heatmap` |

顺带一个改进：原来要换账号得去改 `index.html` 里的 `GITHUB_USER` 常量，现在直接传 `?user=` 就行。

## 加一张新卡片

1. 把单文件卡片丢进 `cards/`，比如 `cards/clock.html`；
2. 在 `cards.js` 里加一条：

```js
{ id:'clock', name:'时钟卡片', file:'cards/clock.html', size:[300,140],
  desc:'一句话说明它长什么样', params:[ ['u','0.8','整卡缩放'] ] }
```

3. 想让它在 iframe 里自动去掉 demo 底色，卡片 CSS 里加一条：

```css
html.lc-embed body{background:none}
```

卡片里再跑这段（`cards/` 下现成的两张可以直接抄文件末尾那段 script）：

```js
var q = new URLSearchParams(location.search);
if (window.self !== window.top || q.get('bg') === 'transparent') {
  document.documentElement.classList.add('lc-embed');
}
```

`index.html`（画廊）和 `card.html`（iframe 入口）都读 `cards.js`，所以列表只维护这一处。

## 文件

```
index.html      画廊：卡片预览 + 参数表 + 一键复制 iframe 代码
card.html       iframe 入口：?card=<id> 挑卡片，其余参数转给卡片
cards.js        卡片注册表（唯一的列表）
cards/*.html    每张卡片，各自自包含
```

## License

MIT
