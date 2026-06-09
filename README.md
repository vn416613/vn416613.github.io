# AI Agent Resume Blog

This is a Hugo + PaperMod static portfolio site for internship applications. It highlights an AI agent runtime project, technical skills, education, and learning notes.

## Local Development

```powershell
D:\tools\hugo\hugo.exe server -s D:\resume-hugo --disableFastRender
```

## Local Build

```powershell
D:\tools\hugo\hugo.exe -s D:\resume-hugo --minify
```

## Editing Profile Content

Most profile content lives in `data/resume.yaml`:

- `profile`: name, email, GitHub, internship direction
- `education`: education experience
- `projects`: project experience
- `skills`: skill tags

Blog notes live in `content/posts/`.

## Deployment

After pushing to `vn416613.github.io`, GitHub Actions can build and deploy the site to GitHub Pages. The repository also keeps a root-level static build for branch-based Pages deployment.
