# GDT · 互动实验室

浏览器中的轻量互动实验，使用 GitHub Pages 发布。

## 在线地址

- 项目首页：<https://rushairer.github.io/GDT/>
- [88 键钢琴 · 多音高识别](https://rushairer.github.io/GDT/apps/central-c-ball/)

## 已有程序

### 88 键钢琴 · 多音高识别

路径：`apps/central-c-ball/index.html`

- 完整呈现钢琴 A0 到 C8 的 88 个琴键，包括 52 个白键和 36 个黑键；
- 88 个琴键紧密排列在同一行，页面不提供横向滚动；
- 点击“开始监听”请求麦克风权限；
- 使用 Web Audio API 获取频谱，结合多谐波证据估计多个同时出现的音符；
- 同时识别多个候选音符，并点亮对应白键或黑键；
- 显示当前主音频率、识别音符列表和同时识别数量；
- 采用相对频谱强度与局部频谱对比，降低整体音量变化对检测门槛的影响；
- 检测输入削波并给出降低音源音量或麦克风增益的提示；
- 音频仅在本机浏览器中处理，不上传录音，也不使用服务端存储；
- 需要 HTTPS 或 localhost 才能获得麦克风权限。

**识别边界：** 这是基于单路麦克风频谱的实时多音高估计，不等同于 MIDI 级别的完整复调转录。谐波重合的音程（例如某些八度、纯五度关系）、强混响、鼓点/失真音色和复杂编曲仍可能造成漏检或误检；削波已经发生时，软件无法还原被截断的波形。若要做精确和弦分析，优先使用数字音频/MIDI 输入或经过训练的复调音符识别模型。

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
