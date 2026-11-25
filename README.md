# GMING OK 接案網站

純靜態網站（一個 `public/index.html`），部署在 Cloudflare 免費方案，跟嘉作一樣用 GitHub 自動部署。

## 檔案在哪裡改

| 要改什麼 | 檔案 |
| --- | --- |
| 所有文字、案例、方案、聯絡方式 | `public/index.html` |
| 網站名稱（Cloudflare 上的專案名） | `wrangler.jsonc` 的 `name` |

改完 push 到 `main`，Cloudflare 會自動重新部署，約 1 分鐘後上線。

## 第一次連接 Cloudflare（只做一次）

1. 登入 Cloudflare 後台 → **Workers & Pages** → **Create** → **Import a repository**。
2. 連接 GitHub，選 `gmingok` 這個 repo。
3. 設定：
   - Project name：`gmingok`
   - Build command：留空
   - Deploy command：`npx wrangler deploy`
4. 按 **Deploy**。完成後會得到 `gmingok.<你的帳號>.workers.dev` 網址，網站就上線了。

## 之後買網域、綁網域

1. 買網域：Cloudflare 後台 **Domain Registration → Register Domains**，買好會自動在你的帳號裡。
   （在別家買的話：Cloudflare 先 **Add a domain**，再到原註冊商把 nameserver 改成 Cloudflare 給的兩組。）
2. 綁網域：**Workers & Pages → gmingok → Settings → Domains & Routes → Add → Custom domain**，填 `你的網域.com`，再加一次 `www.你的網域.com`。
3. 讓 www 轉到主網域：**Rules → Redirect Rules**，`www.你的網域.com/*` 301 轉到 `https://你的網域.com/${1}`。

## 選用（免費）

- **Web Analytics**：看流量。Workers & Pages → gmingok → Metrics，或 Analytics & Logs → Web Analytics。
- **Email Routing**：讓 `hello@你的網域.com` 轉寄到你的 Gmail。

## 本機預覽

直接用瀏覽器打開 `public/index.html` 就能看。
