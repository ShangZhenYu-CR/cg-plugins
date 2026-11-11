# cg-plugins · 毛豆插件库

网站里能在沙箱中运行的小页面。托管走 **GitHub Pages**：https://shangzhenyu-cr.github.io/cg-plugins/

## 目录规范（后端强制）

```
plugins/<slug>/
  index.html     必需   入口页，单文件内联 CSS/JS
  meta.json      必需   元信息
  assets/*       可选   图片/字体等（png jpg svg css js json woff2）
```

- **slug**：`^[a-z0-9][a-z0-9-]{1,40}$`，只能小写字母、数字、连字符，2–41 位，例如 `my-calculator`
- **meta.json**：

```json
{
  "name": "展示名（≤40 字）",
  "desc": "一句话说明（≤120 字）",
  "author": "发布者（服务端自动填）",
  "tags": ["工具"],
  "updatedAt": "2026-11-11（服务端自动填）"
}
```

- **体积**：index.html ≤ 300KB；单个资源 ≤ 1MB；最多 8 个资源

## 内容规则

1. 单文件、内联 CSS/JS，**不引用外部 CDN**（离线也要能开）
2. 不要试图读主站数据：跨源 + 沙箱，读不到
3. 不做自动跳转、弹窗轰炸、挖矿脚本、伪装登录页

## 三种发布方式

| 方式 | 操作 |
|---|---|
| 站内一键 | 设计稿产物面板 → **⇪ 发布到插件库** |
| 手动 git | `git add plugins/<slug> && git commit -m "plugin: <slug>" && git push` |
| 接口 | `POST /plugins/publish` {slug, name, desc, html, assets?} |

服务器用**部署密钥**（只授权本仓库）推送，不持有全范围 token。
