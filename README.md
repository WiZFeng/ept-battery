# 电池信息页 — GitHub Pages 部署说明

本目录是可直接上传到 GitHub Pages 的静态站点（与客户示例 `lukang-luffy.github.io` 同一种做法）。
用微信扫一扫可直接打开，无安全提示页。

## 目录内容

| 文件 | 说明 |
|---|---|
| `index.html` | 型号列表页（仓库首页），扫码/访问根地址时显示 |
| `di100-aa-7.2v.html` | 本型号信息页（Ni-MH AA 1000mAh 7.2V），**二维码指向这个文件** |

## 部署步骤（全程浏览器操作，不用装 Git）

1. **注册 GitHub 账号** — 打开 https://github.com 注册（需邮箱验证）。
2. **新建仓库** — 右上角 `+` → `New repository`
   - Repository name 填 `ept-battery`
   - 勾选 `Public`（免费账号的 Pages 必须公开）
   - 勾选 `Add a README file`，点 `Create repository`
3. **上传页面** — 进入仓库 → `Add file` → `Upload files`
   - 把 `index.html` 和 `di100-aa-7.2v.html` 两个文件拖进去
   - 底部点 `Commit changes`
4. **开启 Pages** — 仓库 `Settings` → 左侧 `Pages`
   - Source 选 `Deploy from a branch`
   - Branch 选 `main`、目录选 `/ (root)`，点 `Save`
5. **等待生效** — 约 1～2 分钟后刷新该页面，顶部会出现网址，形如
   `https://<你的用户名>.github.io/ept-battery/`
6. **验证** — 手机浏览器打开
   `https://<你的用户名>.github.io/ept-battery/di100-aa-7.2v.html`
   再用微信扫一扫测试二维码。

> 想要更短的网址：把仓库名改成 `<你的用户名>.github.io`（例：`ept-pe.github.io`），
> 则链接变为 `https://ept-pe.github.io/di100-aa-7.2v.html`。一个账号只能有一个这样的仓库。

## 生成二维码

把上一步得到的网址替换进去（在 WorkBuddy 工作区执行）：

```bash
python tools/make_qr.py --url "https://<用户名>.github.io/ept-battery/di100-aa-7.2v.html" \
    --out qr/qr-di100-aa-7.2v.png --box 16 --ec H
```

生成的是 784px、纠错等级 H、600dpi 的 PNG，可直接插入标签模板印刷。
加 `--caption "EPT  Ni-MH AA 1000mAh 7.2V"` 可在二维码下方加一行型号文字。

## 新增型号（批量管理）

1. 复制 `di100-aa-7.2v.html`，改名为新型号，例如 `di200-aaa-3.6v.html`
2. 打开该文件，修改页面中的型号、容量、电压、DoC 信息
3. 上传到仓库（`Add file → Upload files`），仓库内容更新后网站**约 1 分钟内自动刷新**
4. `index.html` 中复制一张卡片，改链接与文字
5. 用新型号的网址生成新二维码，印到对应型号的标签上

## 重要提醒

- **网址印上标签后不能再改**。页面内容可以随时更新（改 HTML 重新上传即可），网址不变，二维码不用重印。
- `github.io` 在微信/企业微信中属于可信域名，扫码直接打开；但**国内网络访问 GitHub 偶尔较慢**，
  若正式量产标签面向欧盟客户（主要扫码方在欧洲），此方案完全够用。
- 若日后要用公司自有域名（如 `www.ept-battery.com/battery/...`），把最终网址给到 WorkBuddy 重新生成二维码即可；
  公司域名建议先完成 ICP 备案，且首次使用微信可能有安全提示。
