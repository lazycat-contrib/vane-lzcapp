# Vane - LazyCat App

[Vane](https://github.com/ItzCrazyKns/Vane)（隐私优先的 AI 问答引擎，内置 SearXNG）的懒猫微服（LazyCat）打包。

## 模式

- **镜像模式（mirror）**：`docker.io/itzcrazykns1337/vane` 镜像经 `docker.1ms.run` 加速器拉取，`require_digest_match: true` 校验镜像内容与上游一致。
- **自动跟随上游**：每日检查上游 semver tag（`channel: stable`），发现新版本自动更新版本号与镜像、构建 LPK、发布商店。
- **喵喵商店发布**：仅私有商店（MiaoMiao private store），不发布官方商店。

## 说明

- 镜像内含 Vane + SearXNG（单体 full 版），无需额外搜索引擎容器
- 数据卷 `/lzcapp/var/vane:/home/vane/data`（上传文件与配置）
- AI Provider（Ollama / OpenAI / Claude / Groq 等）在首次打开的设置页配置
- 上游镜像发布滞后较久（v1.12.2 @ 2026-04），自动跟随以 Docker Hub tag 为准

## 结构

| 文件 | 说明 |
| --- | --- |
| `package.yml` | 包元数据（`community.lazycat.app.vane`） |
| `lzc-manifest.yml` | 服务与路由配置 |
| `lzc-build.yml` | 构建配置 |
| `icon.png` | 图标（上游 icon） |
| `.github/lazycat-action.yml` | [lazycat-github-action](https://github.com/ca-x/lazycat-github-action) 配置 |
| `.github/workflows/lazycat.yml` | 构建 + 发布工作流 |

## 所需 Secrets

| Secret | 说明 |
| --- | --- |
| `APPSTORE_URL` / `APPSTORE_TOKEN` | 喵喵商店 API 地址与发布令牌 |
| `APP_ID` | 可选 |
| `PRIVATE_STORE_GROUP_CODES` | 可选，私有分组码 |

## 许可

MIT（上游）
