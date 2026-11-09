---
name: 科技快播封面
description: >-
  当要为科技快播/TVP 竖屏成片做 3:4 封面、九宫格风格选型、或按 Hypebeast（现行默认 B）/黄胶带中间大字胶囊（备选
  A）出可发布定稿时使用；含抖音上传用 1080×1440 JPG 导出；完整成片（视频+封面+文案）走 tvp 技能一次性交付。
---
# 科技快播封面（3:4 · 存档 2160×2880 + 抖音上传 1080×1440 JPG）

为科技快播 / TVP 成片做封面：先风格探索，再出可发布定稿。HTML + 无头 Chrome/Puppeteer 截图，不用 PIL 手绘字。

完整成片流水线（视频+封面+文案一次交）以 [tvp](sand-workflow:tvp) 为准；本技能专管封面探索、定稿与**平台上传导出**。

## 硬约束

1. **底图必须是一手实景/官片静帧**，禁止纯色空底、flat logo 冒充照片。
2. 画面文案默认 **两层**：英文 ALL-CAPS 主标 + 中文一级副标（可两行口语钩子）；不要数据卡、指标条、角标堆、底栏口号墙。
3. 主标+副标要大到手机一瞥可读；缩略图友好——EN 短语宜短、字重宜粗。**中文副标默认 160–180px**（中文圈封面硬约束；≤120px 视为不够醒目，须加大或拆行）。
4. 对比可用：轻暗角、文字区半透遮罩、描边/阴影；**不要**把照片糊成一片，也不要用厚重全幅暗角盖死实景。
5. Hypebeast 潮牌风 **不要**右侧圆形 sticker（DROP NOW / F15 FIRE 等圆章一律删除）。
6. 选型阶段 **不要**覆盖已锁正式封面，除非用户点名某一版替换。
7. **封面 B = 现行默认主推**（Justin 2026-11-02：明确「B 方案好」）：**Hypebeast 潮牌**。聊天气泡与抖音上传**优先交 B**；A 仍并行出作备选。
8. **封面 A = 备选「中间大字黄胶囊」**；禁止再用旧版梯形胶带 / 顶部 masthead 黄条 / LaoliCover 半身式排版冒充 A。
9. **抖音/短视频上传封面不得直接交 2K PNG**：必须另出平台上传包（见「平台上传导出」）；否则平台二压易糊。
10. 文案要有**爆款钩子感**（可稍绕口/反差），但事实必须真；忌干巴巴「产品名+合作」说明书标题。
11. **ZH 封面钩子前置可搜品牌+型号（Justin 2026-11-05 SEO/流量）**：有搜索量的产品名（如「腾讯混元Hy4」）须写进中文副标前半，再接能力钩子（例：`腾讯混元Hy4 / 第一次能看图还能点电脑`）。EN ALL-CAPS 可仍写短能力短语。勿只留能力线丢掉品名。

## 封面 B 定稿规格：Hypebeast 潮牌（现行默认 · 主推）

Justin 锁定优先发布风（2026-11-02）。参考实现：`/workspace/opus_video_demos/posters/templates/publish_test/cover_B_hypebeast.html`。

| 元素 | 规格 |
| --- | --- |
| 布局 | 顶部超大 EN 叠字栈 + **底部**大号中文钩子；非居中黄胶囊 |
| 英文主标 | Bebas / Anton / Impact；ALL-CAPS；首行约 **260–300px**，次行约 **220–260px**；行高 ~0.78；强黑描边/投影 |
| 英文强调块（可选） | 第三行可白底黑字色块条（约 140–180px）+ 色块投影（如 `#cc785c`）；**禁止**右侧圆章 |
| 中文副标 | Noto Sans CJK SC 粗体；约 **160–180px**（Justin 2026-11-07：中文圈缩略图要醒目；可拆 2–3 行）；靠下（约 bottom 110–150px）；白字 + 强描边；**禁止**仍用 ≤120px 脚注级小字 |
| 底图 | 一手静帧 `cover` + 略压暗/提对比；下半 scrim 更深以托住 ZH |
| 禁止 | 右侧圆形 sticker；脚注级小字；说明书式干标题 |

## 封面 A 定稿规格：中间大字黄胶囊（备选 · 仍必出）

参考实现：`/workspace/opus_video_demos/posters/templates/publish_test/cover_A_yellow_tape.html`。

| 元素 | 规格 |
| --- | --- |
| 布局 | 整块文字 **垂直+水平居中**（flex center）；非顶部 masthead |
| 黄胶带块 | `background:#ffe600`；**`border-radius: 999px`（圆角胶囊/pill）**；四周外扩 padding；轻投影；**禁止** `clip-path` 梯形胶带端 |
| 倾斜 | 胶带+英文整体约 `rotate(-1.5deg)` |
| 英文主标 | Oswald/Impact 粗体 ALL-CAPS；**约 240–264px**；行高 ~0.94；可两行；忌过密长句 |
| 英文副行 | 同字体；**约 210–220px**（约为主标 0.8–0.9×） |
| 中文副标 | Noto Sans CJK SC 粗体；**约 168px**；白字 + 强描边/阴影；可两行口语结论 |
| 间距 | 胶带块与中文副标之间约 64–80px gap |
| 底图 | 一手静帧 `cover` + 轻 scrim（中间通透、上下略压暗） |

HTML 结构要点（勿改成旧梯形胶带）：

```html
<div class="center">
  <div class="text-block">
    <div class="headline-wrap"> <!-- rotate(-1.5deg) -->
      <div class="tape"></div>  <!-- border-radius:999px; inset 外扩 -->
      <div class="headline">LINE1<span class="l2">LINE2</span></div>
    </div>
    <div class="sub">中文口语结论</div>
  </div>
</div>
```

`.tape` 必须：`border-radius: 999px; clip-path: none;`。

## 平台上传导出（抖音等 · Justin 2026-10-30）

主页九宫格与信息流会对封面二次压缩。**大 PNG / 过高分辨率更容易被暴力二压发糊。**

### 双轨产物（定稿必交）

| 用途 | 规格 | 路径约定 |
| --- | --- | --- |
| **存档 / 选题库母版** | **2160×2880** PNG（3:4） | `posters/publish_test/cover_B_hypebeast_3_4.png`（及 A） |
| **抖音等直接上传** | **1080×1440**（3:4）**JPG**，sRGB，质量 **约 85–92**（默认 **90**），`subsampling=0`（4:4:4，利文字），体积目标约 **0.3–1.2MB** | `posters/douyin_upload/cover_B_<slug>_1080x1440_q90.jpg`（及 A） |

可选：另出 `1080×1920` JPG（9:16）仅当用户点名或某端强制竖全幅；**抖音主页卡片默认优先 3:4 的 1080×1440**。

### 导出硬规则

1. 从已定稿的 2160×2880 母版 **LANCZOS 缩到 1080×1440** 再存 JPG；不要用低于 1080 短边的图硬放大。
2. **禁止**把 2.5MB+ 的 PNG 直接当上传文件交给用户发抖音。
3. 色彩：**sRGB / RGB**；不要 P3/CMYK。
4. 交付时在聊天气泡**优先附 B 的 JPG**，再附 A；PNG 母版路径可写在正文，默认不强调当上传文件。
5. 提醒用户：**不要经微信/QQ 转发后再传**（会被先压一次）；用原文件或网盘直传。
6. 文案侧：缩略图友好——EN 短语宜短、字重宜粗；过密英文在九宫格里更容易糊。

### 一键导出示例（母版 → 上传包）

```python
from PIL import Image
im = Image.open("posters/publish_test/cover_B_hypebeast_3_4.png").convert("RGB")
im.resize((1080, 1440), Image.Resampling.LANCZOS).save(
    "posters/douyin_upload/cover_B_<slug>_1080x1440_q90.jpg",
    "JPEG", quality=90, optimize=True, subsampling=0,
)
```

## 流程

### A. 探索（用户说「九宫格 / 换风格 / 大师级」）
1. 用项目一手静帧裁成 3:4 底图。
2. 一次出 **9 种明显不同** 的流派（勿与上一批重复），每张独立 HTML → Puppeteer/CDP 截 **2160×2880** PNG。
3. 拼 `grid_9.png` + 手机预览 `grid_9_preview.jpg`（角标 1–9）。
4. 聊天气泡交九宫格 + 中文风格表，等用户点号。
5. 九宫格里至少保留 **1 格「Hypebeast」**（现行默认）+ **1 格「中间大字黄胶囊」** 备选对照。

### B. 发布测试定稿（用户选定风格 / 默认双封面）
科技快播默认并行出两套；**主推 B**：

| 代号 | 风格 | 要点 |
| --- | --- | --- |
| **B** | **Hypebeast 潮牌**（现行默认 · 主推） | 超大叠字、白底色块点缀；**无右侧圆章**；ZH 底部大字爆款钩子；聊天气泡与抖音优先交此张 |
| **A** | **中间大字黄胶囊**（备选 · 仍必出） | 居中胶囊黄胶带（`border-radius:999px`）+ 大号 EN + 略小 ZH；字号见上表 |

输出到项目：
- 母版：`posters/publish_test/cover_B_hypebeast_3_4.png`、`cover_A_yellow_tape_3_4.png`
- **上传包（必交）**：`posters/douyin_upload/cover_B_<slug>_1080x1440_q90.jpg`、`cover_A_<slug>_1080x1440_q90.jpg`

用户确认后，再写入正式双封面槽，并保留 backup；正式槽写入后同样刷新对应 JPG 上传包。

### C. 渲染技术
- 模板：HTML + 本地可商用字体（Bebas / Anton / Oswald / Noto Sans CJK）。
- 截图：优先 Puppeteer → Chrome CDP（`google-chrome --screenshot` 可能挂起）。
- 视口固定 `2160×2880`，`deviceScaleFactor: 1`；上传包再缩 JPG。

## 文案占位（按选题替换）
- EN：两行短爆款短语，如 `NOT SLIDES` / `REAL KOF`（宜短不宜密）；可与中文分流
- ZH：优先 `品牌+型号 + 能力钩子`（可搜名时，Justin 2026-11-05），如 `腾讯混元Hy4 / 第一次能看图还能点电脑`；无强品名时再用纯口语钩子，如 `不是PPT交差，是真拳皇上线了`

## 交付
- 探索：九宫格总览 + 1–9 说明
- 定稿：聊天气泡**优先附 B 的 1080×1440 JPG**，再附 A；正文注明母版 PNG 路径与「抖音请用 JPG、勿转发微信再传」；标明 **B=Hypebeast 主推**、A=黄胶囊备选
