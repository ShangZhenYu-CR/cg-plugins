# cg-plugins · 毛豆插件库

这里放**能在网站里直接跑的小页面**：计算器、小工具、可视化、小游戏……

- 每个插件一个目录：`plugins/<slug>/index.html`（必需）+ `meta.json`（可选）
- 托管在 **GitHub Pages**：https://shangzhenyu-cr.github.io/cg-plugins/plugins/<slug>/
- 网站里用**沙箱 iframe** 打开，**不共享主站登录态**（不同源，读不到 cookie / token）

## 目录约定

```
plugins/
  hello/
    index.html
    meta.json
```

`meta.json`：

```json
{
  "name": "插件名字",
  "desc": "一句话说明",
  "author": "你的昵称",
  "tags": ["工具"],
  "updatedAt": "2026-11-11"
}
```

## 写一个插件的规则

1. **单文件优先**：`index.html` 里内联 CSS/JS，不依赖外部 CDN（离线也能开）
2. **不要尝试读主站数据**：跨源 + 沙箱，读不到，也不该读
3. **单插件 ≤ 2MB**，总目录 ≤ 5MB
4. 不要做：自动跳转、弹窗轰炸、挖矿脚本、伪装登录页
5. 内容要能公开看（GitHub Pages 是公开的）

## 怎么发布

- 站内：对话框里让 AI 写，点「发布到插件库」
- 或者直接提 PR / push：`npx http-server plugins` 本地预览
