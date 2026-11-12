# 崩解世界 · 权能修复者

单文件 HTML 浏览器游戏，源代码位于 [game/index.html](game/index.html)。

## 在线试玩

- [Render 试玩版](https://worldcollapse-powerrestorer-demo.onrender.com/)
- [GitHub Pages 试玩版](https://jc007cyber.github.io/Games-WorldCollapse-PowerRestorer/)

## GitHub → Render 自动部署

Render 服务当前通过公开 Git URL 创建。Render 对公开 Git URL 服务不提供原生 Git Push 自动部署，因此本仓库使用 GitHub Actions + Render Deploy Hook 触发部署。

工作流：`.github/workflows/render-deploy.yml`

- 监听 `main` 分支的 `game/**` 文件变化。
- 可通过 GitHub Actions 的 `workflow_dispatch` 手动触发。
- 对已配置的 Render Deploy Hook 发送 POST 请求。
- 不把 Deploy Hook URL 写入仓库；必须存放在 GitHub Actions Repository Secrets。

需要在 GitHub 仓库 Settings → Secrets and variables → Actions → New repository secret 中配置：

| Secret 名称 | 对应 Render 站点 |
|---|---|
| `RENDER_DEPLOY_HOOK_DEMO` | 原版试玩站 |
| `RENDER_DEPLOY_HOOK_PLAY` | 备用试玩站 |
| `RENDER_DEPLOY_HOOK_MIRROR` | 镜像试玩站 |

每个 Hook URL 在对应 Render 服务 Dashboard → Settings → Deploy Hook 中创建并复制。不要把 Hook URL 发到聊天或提交到 GitHub 文件。

当前工作流已提交，但在至少配置一个 Secret 前，GitHub Actions 会明确报错；未配置的站点会显示 warning 并跳过。配置三个 Secret 后，一次游戏代码推送会触发三个站点部署。

[原版 Render 服务](https://dashboard.render.com/static/srv-dbq4s18u01pc739sdqcg)
[备用 Render 服务](https://dashboard.render.com/static/srv-dbqhgd56e07s73f7mr20)
[镜像 Render 服务](https://dashboard.render.com/static/srv-dbqhgdt6e07s73f7mthg)

Render Blueprint `worldcollapse-autodeploy` 的 `autoSync` 仍然开启，但它用于同步 Blueprint 配置，不替代上面的游戏代码部署工作流。

## 备用部署配置

- [render.yaml](render.yaml)：Render Blueprint 静态站点配置。
- [.github/workflows/deploy-pages.yml](.github/workflows/deploy-pages.yml)：GitHub Pages 自动部署流程。

## 注意

不同域名的浏览器本地存档独立；从 GitHub Pages 切换到 Render 不会自动迁移已有进度。中国大陆网络访问性取决于域名及运营商，应使用目标网络实测。
