# 蜀香小馆 · GEO 演示站

一个纯静态站点，用于 GEO（生成式引擎优化）演示与验证：4 个 HTML 页面 + `robots.txt` + `sitemap.xml`，无构建步骤、无外部依赖，任何静态托管都能直接跑。

> 站内门店「蜀香小馆」为演示用虚构内容，不指向任何真实门店。

## 页面

| 文件 | 内容 |
| --- | --- |
| `index.html` | 首页：门店介绍、招牌菜与价格、门店信息、预订须知 |
| `menu.html` | 菜单与价格、人均与点菜建议 |
| `about.html` | 品牌故事、食材来源、口味理念、客群 |
| `contact.html` | 地址、电话、营业时间、停车与到店须知 |

## 本地预览

```bash
python -m http.server 8899
# 打开 http://127.0.0.1:8899/index.html
```

## 部署到 GitHub Pages

`_deploy/deploy_github.py` 全程走 `api.github.com`（不依赖 `github.com` 的 git 推送，本机代理把 git over HTTPS 挡了）：

```bash
# 1) 把 PAT 写进临时文件（不要写进命令行）
# 2) 运行
python _deploy/deploy_github.py --repo geo-demo-site --token-file _deploy/token.txt
```

脚本会：建公开仓库 → 按页面 URL 生成 `sitemap.xml` → 上传全部文件 → 开启 Pages（`main` 分支根目录）→ 轮询构建状态 → 打印线上地址。

## 说明

- `.nojekyll` 已保留，避免 GitHub 走 Jekyll 预处理。
- 站点为纯静态演示，仓库需 **public**（免费账号的 Pages 只支持公开仓库）。
