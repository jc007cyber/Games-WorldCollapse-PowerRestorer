# 崩解世界 · 权能修复者

单文件 HTML 浏览器游戏，源代码位于 [game/index.html](game/index.html)。

## 在线试玩

- [Render 试玩版](https://worldcollapse-powerrestorer-demo.onrender.com/)
- [GitHub Pages 试玩版](https://jc007cyber.github.io/Games-WorldCollapse-PowerRestorer/)

## GitHub → Render 自动部署

Render 服务 `worldcollapse-powerrestorer-demo` 已关联本仓库的 `main` 分支，开启 `Auto Deploy: yes`，触发条件为 `commit`。

原版试玩站还由 Render Blueprint `worldcollapse-autodeploy` 托管，已启用 `autoSync`：GitHub `main` 更新后会尝试同步配置及自动构建。实际以 Render Deploys 记录为准。

1. 修改 `game/index.html` 并提交到 `main`。
2. Render 自动拉取最新提交。
3. 执行 `mkdir -p site && cp game/index.html site/index.html`。
4. 将 `site` 目录作为静态站点发布；网站 URL 不变。

[查看 Render 服务](https://dashboard.render.com/static/srv-dbq4s18u01pc739sdqcg)

## 备用部署配置

- [render.yaml](render.yaml)：Render Blueprint 静态站点配置。
- [.github/workflows/deploy-pages.yml](.github/workflows/deploy-pages.yml)：GitHub Pages 自动部署流程。

## 注意

不同域名的浏览器本地存档独立；从 GitHub Pages 切换到 Render 不会自动迁移已有进度。中国大陆网络访问性取决于域名及运营商，应使用目标网络实测。
