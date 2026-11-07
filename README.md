# GDT · 互动实验室

浏览器中的轻量互动实验，使用 GitHub Pages 发布。

## 在线地址

- 项目首页：<https://rushairer.github.io/GDT/>
- [88 键钢琴 · 乐谱与演奏挑战](https://rushairer.github.io/GDT/apps/central-c-ball/)

## 88 键钢琴 · 乐谱与演奏挑战

路径：`apps/central-c-ball/index.html`

### 实时识别

- 完整显示钢琴 A0 到 C8 的 88 个琴键，包括 52 个白键和 36 个黑键；
- 使用 Web Audio API 获取频谱，结合多谐波证据估计多个同时出现的音符；
- 同时识别多个候选音符，并点亮对应白键或黑键；
- 显示当前主音频率、识别音符列表和同时识别数量；
- 检测输入削波并给出降低音源音量或麦克风增益的提示。

### 乐曲创作与导入

- 导入 MuseScore 4 的 `.mscz` 压缩乐谱和 `.mscx` XML 乐谱；
- 同时支持导入 MusicXML（`.musicxml` / `.xml`）及 GDT 乐曲 JSON；
- 解析音符、和弦、休止符、基础时值、拍号和速度；
- 在 88 键键盘上点选音符，多选琴键可组成和弦；
- 设置 BPM、拍号和音符时值，添加音符或休止符；
- 使用 Web Audio 合成音色试听乐曲；
- 自动保存最近编辑内容到当前浏览器，并可下载 `.gdtmusic.json`；
- 导出 MusicXML，可在 MuseScore 4 中继续打开和编辑。

### 演奏挑战

- 乐谱中的每个音符变成对应琴键位置的下落条形；
- 条形到达琴键时，通过麦克风检测演奏音高；
- 匹配成功后，对应条形消失；未及时匹配会计为未命中；
- 和弦会同时产生多个下落条形，分别判断每个音符；
- 显示命中数、未命中数和准确率。

### 数据与识别边界

- 乐谱文件在浏览器本机解析；麦克风音频仅在本机处理，不上传录音；
- 麦克风需要 HTTPS 或 localhost 权限；
- MSCZ 导入聚焦音高与节奏数据，不完整还原谱面排版、歌词、复杂装饰记号、连音线、反复跳转等高级记谱信息；
- 当前挑战采用单路麦克风频谱多音高估计，不等同于 MIDI 级别的复调转录。谐波重合的音程、强混响、鼓点/失真音色和复杂编曲仍可能造成漏检或误检；
- 精确的复杂和弦挑战建议使用 MIDI 或数字音频接口输入。

## 开发和部署

代码位于 `main`，Pages 工作流在 `.github/workflows/pages.yml`。提交到 `main` 后会触发静态站点部署，无需构建命令。

本地调试：

```bash
python3 -m http.server 8000
```

打开 <http://localhost:8000/apps/central-c-ball/>。

## 目录

```text
/
├── index.html
├── apps/
│   └── central-c-ball/
│       └── index.html
├── .github/
│   └── workflows/
│       └── pages.yml
└── README.md
```
