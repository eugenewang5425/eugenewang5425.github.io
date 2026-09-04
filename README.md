# eugenewang5425.github.io

个人主页 / Personal site of **Eugene Wang** — 从 GIS/遥感深度学习走向机器人/具身智能。

🌐 线上站点: <https://eugenewang5425.github.io>

## 技术栈 / Stack

- 纯 HTML + CSS + 少量原生 JS（零框架、零依赖）
- 双主题（`prefers-color-scheme`）、响应式（≤640px 移动端菜单）、无障碍基础（aria / focus-visible / reduced-motion）
- 单文件页面：`index.html`（结构 + 内联脚本）与 `style.css`（设计令牌 + 版式）
- GitHub Pages 部署（main 分支直发，CDN 缓存约 1 分钟生效）

## 设计参考 / Design refs

版式与 UI 参数参考 **bchiang7**（Brittany Chiang）现役站：分区纵向节奏、字阶、单主色 + 中性色阶、轻阴影、mono 标签；配色与观感融合本站"空间智能"主题（#4f8cff 主色）。

## 页面结构 / Sections

Hero（头像/标语/技能芯片/CTA）→ 01 About → 02 Research（MSSACT-Net 指标）→ 03 Projects（5 个公开仓库卡片）→ 04 Now/Next（阶段路线）→ 05 Contact → Footer。

## 交互 / Interactions

- 导航：吸顶胶囊菜单，滚动位置高亮（阅读线 ~30% 视口 + **方向迟滞 12px** 防边界抖动）
- 末端处理：距底部 ≤120px 视为"已到底"（激活最后一节 Contact），上行保持至 >240px——抵消真实触控板 ±15px 动量震荡与页面高度漂移
- 点击优先：点击导航即高亮目标分区（即使页面长度不足以把该节顶到导航正下），手动滚动后交还位置规则
- 滚动：100% 浏览器原生（`scroll-behavior: smooth` + `scroll-padding-top: 76px` + 锚点），无任何自定义滚动动画
- 诊断入口：URL 加 `#diag` 可开启逐帧滚动轨迹录制（导出按钮），用于环境差异排查

## 已知问题与解决记录 / Known issue & resolution

**问题**：Windows Chrome（经典滚动条）在特定页面缩放（50%/80%/90%/100%）下滚动到底时，页面出现轻微横向溢出 → 触发**水平滚动条出现/消失循环**；经典滚动条占用 ~15px 视口高度，导致 `maxY`（scrollHeight − clientHeight）反复 ±15px 漂移，页面底部被"顶起"，末端高亮（阅读线/距底阈值）随之抖动，行程恰为滚动条厚度。

**为什么常规站点没有**：绝大多数页面具备横向防溢出护栏（`overflow-x: clip/hidden` 或全局 `max-width:100%` + `min-width:0`），且不存在"距底阈值敏感"的滚动监测；本站桌面导航为无换行胶囊组，在窄于其最小宽度但尚未进入 640px 移动断点的视口/缩放下可能成为溢出源。

**规避与修复（进行时）**：① 交互层已改为全部原生滚动 + 方向迟滞/末端宽区，与滚动条漂移解耦；② 根治项（待应用）：根容器 `overflow-x: clip` + 导航 `min-width:0`/允许换行护栏，从源头消除横向溢出；见 Issue #1 全链路溯源。

**版本溯源（本仓库 `git log`）**：80a74f5（导航重做，引入宽屏胶囊导航）→ 7876c19 / d5f53a6 / 75c34c7（自定义滚动动画多轮尝试）→ cb20e4f / 791cc1e / 1bac19d / c29e5a4（scroll-spy 位置算法与末端迟滞迭代）→ 7c769fa（回归原生滚动）→ 6337548（加装 #diag 诊断）→ c29e5a4（现 HEAD，120px 末端区）。

## 本地开发 / Local

```powershell
Set-Location "D:\项目\分析githuber\.homepage-repo"
python -m http.server 8000   # 打开 http://127.0.0.1:8000
```

## License

代码：MIT（站点内容与个人素材属作者所有）。
