# 小票机 · 结单小票生成器

网页版结单小票机：左边填单，点「打印小票」，小票从打印机纸槽里滚出来。单文件 HTML，无需安装、无需联网（除导出 PNG 时加载 html2canvas）。

## 功能

- **点单信息**：店名（英文/中文）、下单时间、币种（£ / ¥ / $ / € / 无前缀）、小票编号
- **点单项目**：点单类型 + 副标拼音、陪陪名称、数量、金额；可「再加一项」，逐条编号 `#01 #02 …`，单条时自动隐藏删除键
- **结算**：合计（留空自动按明细汇总，手填则显示「已手动填写合计」并出现恢复自动）、实付金额（留空 = 合计）、卡内余额
- **祝福**：票面寄语、祝福人名（写进页脚「祝 ___ 在OKB俱乐部玩得开心玩得愉快」）、自定义页脚、结单章开关
- **配色**：6 个预设色相，外加色相滑杆（0–360 全色域），夜间模式只反 UI 与纸面外区域、小票始终白纸
- **出票**：打印动画 + 机身抖动、`prefers-reduced-motion` 下直接落位、按钮文案 打印小票 → 出票中… → 再打一张
- **导出**：html2canvas 双倍分辨率存 PNG（`小票-<单号>.png`）；`Ctrl/Cmd + P` 只打印票据，纸宽 80mm
- 所有输入自动存 `localStorage`，刷新不丢

## 本地打开

直接双击 `index.html` 即可（也可用 `python3 -m http.server` 起个本地服务）。

## 发布到 GitHub Pages（3 步）

前提：装好 `git`，有一个 GitHub 账号。

```bash
cd receipt-shop
git init -b main
git add index.html README.md
git commit -m "feat: 结单小票机"
git remote add origin https://github.com/<你的用户名>/receipt-shop.git
git push -u origin main
```

推送前先在 GitHub 网页端新建同名空仓库（不要勾选自动生成 README，否则要 merge）。

然后进仓库 **Settings → Pages → Source** 选 `Deploy from a branch`，分支 `main`、目录 `/ (root)`，保存。等 1–2 分钟，访问：

```
https://<你的用户名>.github.io/receipt-shop/
```

## 改成自己的店

`index.html` 里搜 `DEFAULTS`，改掉默认值（店名、点单类型、陪陪名、寄语、人名、卡内余额等）即可；换猫咪插画就替换 `assets/sticker.webp` 并重新内联成 base64（或直接把 `<img>` 的 `src` 改成相对路径引用）。
