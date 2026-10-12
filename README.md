# Little_card 

喵~ 这里是一窝自包含的小卡片喵。每张卡就是一个 HTML 文件，不吃框架、不用构建，塞进 iframe 里就能住下啦喵！

## 怎么用喵？

```html
<iframe src="https://xiaoyue-cm.github.io/Little_card/card.html?card=music"
        width="400" height="120" style="border:0" loading="lazy"></iframe>
```

把 `card` 换成下面表里的 id 就换卡喵，剩下的参数原封不动丢给卡片自己喵~

> 要先把 GitHub Pages 打开喵（Settings → Pages，Source 选 `main` / `root`），
> 不然 iframe 里只会伸出一堆源码，喵呜——

## 都有哪些卡喵？

| id | 名字 | 尺寸 | 小家伙长啥样喵 |
|---|---|---|---|
| `music` | 音乐播放 | 400 × 120 | 平时就一张唱片趴着，戳一下展开，再点右边抽出一块播放面板，喵~ |
| `heatmap` | 贡献热力图 | 680 × 340 | 年 / 月随便切，窗口一窄就整只缩起来，格子不乱跑喵 |

## 参数喵

| 参数 | 说明 |
|---|---|
| `card` | 想撸哪张卡（必填喵） |
| `u` | 缩放基准，1 = 默认大小，不填就按宽度自己缩喵 |
| `bg` | `transparent` 去掉 demo 底色，被 iframe 套住时会自己开喵 |
| `src` / `title` / `artist` | music 专用：音频直链、曲名、艺人（不给 `src` 就没声音，只喵喵不出声） |
| `user` | heatmap 专用：看谁的贡献，默认 `xiaoYue-cm` 喵 |

## 文件喵

```
index.html      画廊：预览 + 参数表 + 一键复制 iframe
card.html       iframe 入口：?card=<id> 选卡
cards.js        卡片注册表
cards/*.html    每张卡片
```

## 想再养一张卡喵？

把卡丢进 `cards/`，再去 `cards.js` 加一条注册项就搞定啦喵~

## License

MIT 喵~
