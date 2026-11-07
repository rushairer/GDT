# GDT · 互动实验室

浏览器中的轻量互动实验，使用 GitHub Pages 发布。

## 在线地址

- 项目首页：<https://rushairer.github.io/GDT/>
- [88 键钢琴 · 音高识别](https://rushairer.github.io/GDT/apps/central-c-ball/)

## 已有程序

### 88 键钢琴 · 音高识别

路径：`apps/central-c-ball/index.html`

- 完整呈现钢琴 A0 到 C8 的 88 个琴键，包括 52 个白键和 36 个黑键；
- 88 个琴键紧密排列在同一行，白键之间无布局间隙，黑键按真实半音位置叠放；
- 页面不提供横向滚动，所有琴键在当前屏幕宽度内同时显示；
- 点击“开始监听”请求麦克风权限；
- 使用浏览器 Web Audio API 和 YIN 类差分算法估计音高；
- 识别到音符时点亮对应白键或黑键；
- 显示当前频率、音符和相对最近标准音的音分误差；
- 音频仅在本机浏览器中处理，不上传录音，也不使用服务端存储；
- 需要 HTTPS 或 localhost 才能获得麦克风权限。

页面可在桌面和移动端现代浏览器中使用。手机屏幕宽度有限，88 键会等比例压缩显示；识别结果受麦克风、环境噪声和乐器音色影响。当前为单音音高识别，不支持和弦的多音分离。

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
