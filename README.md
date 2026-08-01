# fisherdata.top — 李浩渊个人简历站

AI Agent 应用开发工程师个人简历网站，单页静态站。

## 技术栈

- [Astro](https://astro.build) 静态站点
- 纯 CSS 设计系统（暖白 × 墨绿），无外部字体依赖，国内访问友好
- 部署：Cloudflare Pages + 自有域名 fisherdata.top

## 本地开发

```sh
npm install
npm run dev      # 开发预览 http://localhost:4321
npm run build    # 构建到 dist/
npm run preview  # 预览构建产物
```

## 目录结构

```
src/
  components/   # 页面模块组件（Header/Hero/Projects/Experience/OpenSource/Skills/Contact）
  pages/        # index.astro 单页入口
  styles/       # global.css 设计系统（配色变量、排版、通用组件）
public/
  resume.pdf    # 简历 PDF（由 resume-src.html 通过 Edge headless 导出）
resume-src.html # 简历 PDF 的 HTML 源文件
```

## 更新简历内容

改简历 = 改 `src/components/` 下对应模块的组件文件（内容是数据化的数组，改文字即可）→ `npm run build` → push。

更新简历 PDF：修改 `resume-src.html`，用 Edge headless 重新导出：

```sh
"C:\Program Files (x86)\Microsoft\Edge\Application\msedge.exe" \
  --headless --disable-gpu --print-to-pdf="public/resume.pdf" \
  --no-pdf-header-footer "file:///D:/personal/fisherdata/resume-src.html"
```

## 部署

推送到 GitHub 仓库 → Cloudflare Pages 连接该仓库（构建命令 `npm run build`，输出目录 `dist`）→ 绑定 fisherdata.top。
