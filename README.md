# ept-battery — 电池产品信息页（EU 2023/1542）

电池标签二维码指向的在线信息页，内容依据 **Regulation (EU) 2023/1542**（Article 6 / Article 13 / Annex I / Annex VI 及 EU 符合性声明要求）。

## 在线地址

| 型号 | 页面 |
|---|---|
| 型号列表 | https://wizfeng.github.io/ept-battery/ |
| DI100 Ni-MH AA 1000mAh 7.2V | https://wizfeng.github.io/ept-battery/di100-aa-7.2v.html |
| 14500 Li-ion 800mAh 7.4V (2S1P) | https://wizfeng.github.io/ept-battery/14500-800mah-7.4v.html |
| 0620 Ni-MH AAA 600mAh 3.6V (3S) | https://wizfeng.github.io/ept-battery/0620-aaa600mah-3.6v.html |
| DI300 Ni-MH AA 1000mAh 7.2V | https://wizfeng.github.io/ept-battery/di300-aa-7.2v.html |

## 维护规则

- **网址一旦印上标签不得更改**；页面内容可随时更新（重新上传同名 HTML，约 1 分钟生效，二维码无需重印）。
- 新增型号：复制任一型号 HTML → 修改内容 → 以 `型号-容量-电压.html` 命名上传 → 在 `index.html` 增加一张卡片。
- 页面为纯静态、手机优先布局，不依赖任何外部 CDN 资源。
