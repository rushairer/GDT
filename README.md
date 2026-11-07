# GDT · 互动实验室

浏览器中的轻量互动实验，使用 GitHub Pages 发布。

## 在线地址

- 项目首页：<https://rushairer.github.io/GDT/>
- [中央 C · 音高感应球](https://rushairer.github.io/GDT/apps/central-c-ball/)

> 首次启用时，请在仓库 **Settings → Pages → Build and deployment → Source** 选择 **GitHub Actions**。随后 GitHub Actions 中的 `Deploy GitHub Pages` 工作流将负责自动发布。

## 已有程序

### 中央 C · 音高感应球

路径：`apps/central-c-ball/index.html`

- 点击“开始监听”请求麦克风权限；
- 使用浏览器 Web Audio API 采集声音，并通过 YIN 类差分算法估计音高；
- 识别中央 C（C4，约 261.63 Hz）时小球放大；音高离开目标后恢复；
- 显示当前频率、音符和相对 C4 的音分误差；
- 无第三方 JS 依赖、无录音上传、无服务端存储；
- 需要 HTTPS 或 localhost 才能获得麦克风权限。

页面可在桌面或移动端的现代浏览器中使用。识别结果受麦克风、环境噪声和乐器音色影响，并非专业调音仪。

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
