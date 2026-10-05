# 部署指南：把 `guanhe1001.asia` 免费上线

本落地页是纯静态文件（只有 `index.html`），**不需要任何服务器、不需要备案**，用 Cloudflare Pages 免费托管，再把域名解析过去即可。全流程 0 元。

---

## 第一步：准备文件
工作区里这个文件夹 `考研刷题落地页/` 就是要上线的网站，核心文件是 `index.html`。
- 想改文字：直接编辑 `index.html` 里的标题、功能描述、邮箱。
- 想换小程序码：把 `<div class="qr">...</div>` 里替换成你的二维码图片 `<img src="qrcode.png" width="180"/>`，并在同目录放 `qrcode.png`。

---

## 第二步：部署到 Cloudflare Pages（免费）

方式 A —— 连 GitHub 自动部署（推荐，以后改文件自动更新）：
1. 注册 GitHub 账号，新建一个仓库（如 `zhiyan-site`）。
2. 把 `考研刷题落地页/` 里的 `index.html` 上传到仓库根目录。
3. 注册/登录 [Cloudflare](https://dash.cloudflare.com)（免费）。
4. 进入 **Workers & Pages → Create → Pages → 连接 Git**，选你的仓库。
5. 构建设置：Framework preset 选 `None`；Build command 留空；Build output directory 填 `/`（根目录）。
6. 点 **Save and Deploy**，几十秒后会给一个 `xxx.pages.dev` 的临时地址，先打开看看效果。

方式 B —— 直接拖拽上传（不想用 Git 时）：
在 Cloudflare Pages 创建时选 **Direct Upload**，把整个文件夹拖进去即可。

---

## 第三步：绑定你的域名 `guanhe1001.asia`

1. 在 Cloudflare 控制台添加站点：**Websites → Add a Site → 输入 `guanhe1001.asia`**。
2. 按提示把域名的 **DNS 服务器（NS）** 改成 Cloudflare 给你的两个地址（去阿里云域名控制台 → 域名列表 → `guanhe1001.asia` → DNS 修改 / 管理，把 NS 换成 Cloudflare 的）。
   - ⚠️ 这一步是在**阿里云**改 NS，不是在 Cloudflare 加解析记录。改完 5 分钟~24 小时生效。
3. NS 生效、站点变绿后，进入该站点 → **Pages → 你的项目 → Custom domains → Set up a custom domain**，输入 `guanhe1001.asia` 和 `www.guanhe1001.asia`。
4. Cloudflare 会自动加好 CNAME 并签发**免费 SSL 证书**（加密访问 https）。
5. 等几分钟，浏览器打开 `https://guanhe1001.asia` —— 网站就活了，任何人都能访问。

---

## 第四步（可选）：免费专属邮箱

1. 站点内 → **Email → Email Routing → 开启**。
2. 添加路由：`hi@guanhe1001.asia` → 转发到你的常用邮箱。
3. 验证目标邮箱后即生效，别人发 `hi@guanhe1001.asia` 你能收到。

---

## 常见坑

- **NS 没改对**：绑定自定义域名一直“待验证”，多半是阿里云那边的 NS 没换成 Cloudflare 的，去阿里云域名控制台确认。
- **`.asia` 续费 ¥99/年**：首年便宜是钩子，定个明年到期前 1 个月的提醒，过期域名就没了、网站也挂。
- **这不是备案替代**：海外托管免备案，但若以后想在国内做小程序后端加速，仍要买国内 ECS + ICP 备案。
- **小程序后端**：当前落地页不含后端。小程序真正运行仍需服务器/云开发 + 备案，等以后有预算再做。

---

## 费用汇总
| 项目 | 费用 |
|------|------|
| 域名 `guanhe1001.asia`（首年） | ¥8（已付） |
| Cloudflare Pages 托管 | 免费 |
| SSL 证书 | 免费 |
| Email Routing | 免费 |
| **合计新增** | **¥0** |
