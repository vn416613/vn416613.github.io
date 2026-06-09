# AI Agent Resume Site

这是一个用于个人简历展示的 Hugo 静态站点。

## 本地运行

```powershell
D:\tools\hugo\hugo.exe server -s D:\resume-hugo --disableFastRender
```

## 本地构建

```powershell
D:\tools\hugo\hugo.exe -s D:\resume-hugo --minify
```

## 修改个人信息

主要内容集中在 `data/resume.yaml`：

- `profile`：姓名、邮箱、GitHub、求职方向
- `education`：教育经历
- `projects`：项目经历
- `skills`：技能标签

## 发布

仓库推送到 `vn416613.github.io` 后，GitHub Actions 会自动构建并部署到 GitHub Pages。
