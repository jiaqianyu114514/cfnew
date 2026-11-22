# cfnew

Cloudflare Worker 跑 cfnew，免费，不用 VPS。

来源：上游 byJoey/cfnew 精简内核 2026.10.17.2，`_worker.js` 37,806 字节。

## 部署后要做的事（Cloudflare 控制台）

1. Worker 设置 → 变量和机密，加文本变量 `u`，值是你自己的 UUID。
2. 需要在线保存配置时，创建一个 Workers KV 命名空间，在绑定里加 `C`。
3. 兼容日期已设为 `2026-01-20`，改了变量或绑定后要重新部署。

打开 Worker 首页显示 `hello` 是正常的。管理和订阅走独立面板 cfnew-panel，填自己的 Worker 域名和同一个 UUID。

## 自动部署

推到 `main` 分支会自动部署。GitHub 仓库 Settings → Secrets and variables → Actions 里要加：

- `CLOUDFLARE_API_TOKEN`：Cloudflare API Token，需要 Workers 编辑权限
- `CLOUDFLARE_ACCOUNT_ID`：Cloudflare 账号 ID

不要把 UUID、Token 写进代码或这个仓库里。
