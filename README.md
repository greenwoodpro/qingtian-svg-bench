# 晴天 · 50 张大模型 SVG 海报横评

> 同一句提示词，50 次生成，8 个平台、19 个模型、4 档思考强度。
> 全部由模型自己手写 SVG —— 不调用图片生成，不使用任何现成素材。

**在线浏览 → [greenwoodpro.github.io/qingtian-svg-bench](https://greenwoodpro.github.io/qingtian-svg-bench/)**

> 站点托管在 **GitHub Pages**（`github.io` 域名）。国内网络下 github.io 常有 DNS 污染或间歇性阻断，打不开时挂代理，或直接浏览仓库里的 `images/` 全尺寸原图。

---

## 测试方法

给每个模型的是同一句话：

> 帮我用 SVG 画一张周杰伦晴天的 MV 海报或封面，内容完整精细、富有创意，像真实的照片一样，但注意不要使用图片或已有素材，全靠自己用 SVG 绘制。

没有任何参考图、没有风格示例、没有第二轮修正。模型输出的 `.svg` 原样收下，用 Edge 无头浏览器按原始 viewBox 渲染成 PNG（2× 缩放，全尺寸保留），不做任何后期调整。

| 项目 | 数量 |
| --- | --- |
| 作品 | 50 件（51 份文件，其中 1 份为重复导出） |
| 平台 | 8 个 |
| 模型 | 19 个 |
| 厂商 | 10 家 |
| SVG 源码 | 24 份，共 19.2 MB |

---

## 先说结论

50 张里真正能当海报用的，不超过十张。

### 最好的三张

1. **`v0 · GPT (astra) · xhigh`** — 空教室的长焦透视、窗格投下的阴影、琴箱上的高光，是全场最接近实拍的一张。有意思的是它不是手绘路径：模型自己写了 Three.js，把程序化几何场景投影成矢量路径。技术上绕了一层，结果却是最"真"的。
2. **`claude.ai · Sonnet 5.5 · high`** — 唯一一张真正把"概念"做出来的：雾玻璃上用手指划出「晴天」二字，字缝里透出蓝天。这比堆元素难得多。
3. **`商汤 · SenseNova · high`** — 室内静物：吉他盒、黑胶、窗光。50 张里唯一一张跳出"校园海报模板"的。

**最会做平面构成**：`wb · GLM-5.3-Flash`（方楼 + 窗影 + 巨大「晴天」）、`chaiku 5.5 max`（逆光剪影 + 极简字）
**最有电影感**：`trae · GLM-5.3-Flash xhigh`（雨幕里劈下的光柱）、`DeepSeek 官方 API`（落日长路上的单人背影）
**调性最克制**：`GPT-6.1 (sol)` 三张，低饱和、少元素、有作者感

### 通病

- **同质化极重。** 九成作品挤在同一个安全区：校门 / 教室 / 操场 / 秋千 / 单车 / 黄伞 / 小黄花，加上居中两字「晴天」。第一眼都像，翻十张就腻了。
- **丁达尔光柱、天空渐变、向日葵** 已经成了标配滤镜，遮住了本来该有的构图差异。
- **人物一律背影或剪影。** 都知道正面画脸会崩，于是集体回避——这是模型对自己能力边界的诚实，也是想象力的偷懒。
- **底部小字排版普遍失控**，糊成一团，凑近看是装饰性乱码。
- **设计层级差距很大**：`muse`、`wb-glm5.3flash`、`chaiku` 明显是"先想到再画"；其余多数是"先画场景再塞字"。

### 关于思考强度

**更高的强度不等于更好的作品。** `glm5.3` 的 high 是一张有冲击力的暖橙逆光，max 反而灰白低对比、字和图都发虚。强度更像是"想得更多"，而不是"画得更好"——强度越高，元素堆叠失控的风险越大。

全场唯一在强度上换来明显质感的，是 `GPT (astra)` 一组：三张都不是一笔一笔手绘，而是模型自己写 Three.js 把程序化几何场景投影成矢量路径；xhigh 把机位拉远、饱和度压低，是三张里最完整的一张。

### 关于平台

- **v0.app** 成品度最高：尺寸统一、排版完整、有电影片头字幕的质感。
- **opencode / Trae Code** 更"代码味"：构图朴素、留白多，但几何结构干净。
- **商汤平台上跑 GLM / DeepSeek**，风格差异主要来自模型本身，平台包装的影响不明显。
- **DeepSeek 官方 API 接 Claude Code** 这一跑成本最高（300K 上下文，约 1.8 元），画面也最"长"，完整保留了大面积天空与地平线。

---

## 怎么逛

`index.html` 是一个纯静态画廊，打开就能用：

- **搜索**：按 `/` 聚焦搜索框，可搜模型、厂商、平台、强度、备注关键词（如 `opus`、`glm`、`窗`、`v0`）
- **筛选**：平台 / 厂商 / 思考强度 三组标签可多选叠加
- **排序**：按平台·模型、模型名、思考强度、像素体量
- **大图**：点任意作品 → 查看原图、元数据、`下载 PNG`、`查看 SVG 源码`；键盘 `← →` 翻页，`Esc` 关闭
- **分享**：筛选状态写进 URL hash，复制链接即可还原同一个视图
- **深浅色**：右上角太阳 / 月亮图标切换，选择记在本地；也可用 `?theme=dark` 直接指定

---

## 命名规则

文件名本身就是元数据：`平台前缀 + 模型 + 思考强度`。

| 前缀 / 目录 | 含义 | 说明 |
| --- | --- | --- |
| （无前缀） | `v0.app` | Vercel v0 平台 |
| `c` | `claude.ai` | Anthropic 官方网页版，如 `csonnet5.5` |
| `trae` | `Trae Code` | Trae 编辑器内置 |
| `wb` | `WorkBuddy` | WorkBuddy 客户端 |
| `oc` | `opencode` | opencode CLI |
| `model` | `魔搭 ModelScope` | 阿里魔搭社区 |
| `sens` / `sen` | `商汤 SenseNova` | 商汤平台（跑自研及其它模型） |
| `dsv4.1_official` | `DeepSeek 官方 API` | 接入 Claude Code，300K 上下文 |

**模型代号**：`astra` = GPT，`argon` = Gemini 4，`sol` = GPT-6.1，`fable` = Claude 第四档（Haiku → Sonnet → Opus → Fable）。
**思考强度**：`medium` 标准 / `high` 高 / `xhigh` 极高 / `max` 最高；**没标的一律记为 high（默认档）**。

---

## 全部作品

### v0.app · 28 件

| No. | 模型 | 厂商 | 强度 | 文件 | 画面 |
| --- | --- | --- | --- | --- | --- |
| 01 | Claude Fable 5.1 | Anthropic | 高 | [PNG](images/v0__claude-fable5.1__high.png) | 草地、秋千、抱琴少年，色块干净 |
| 02 | Claude Fable 5.1 | Anthropic | 极高 | [PNG](images/v0__claude-fable5.1__xhigh.png) | 榕树秋千、吉他、电线杆，构图很稳 |
| 03 | Claude Fable 5.1 | Anthropic | 最高 | [PNG](images/v0__claude-fable5.1__max.png) | 操场中央的秋千与低垂的太阳 |
| 04 | Claude Opus 5.5 | Anthropic | 高 | [PNG](images/v0__claude-opus5.5__high.png) | 树下单车与夕照，留白舒服 |
| 05 | Claude Opus 5.5 | Anthropic | 极高 | [PNG](images/v0__claude-opus5.5__xhigh.png) | 路灯下的林荫道，少年背影，色调统一 |
| 06 | Claude Opus 5.5 | Anthropic | 最高 | [PNG](images/v0__claude-opus5.5__max.png) | 校门、老树、并肩的两人，紫金夕照 |
| 07 | Claude Sonnet 5.5 | Anthropic | 高 | [PNG](images/v0__claude-sonnet5.5__high.png) · [SVG](svg/v0__claude-sonnet5.5__high.svg) | 雾玻璃上写「晴天」，伏案的少年 |
| 08 | Claude Sonnet 5.5 | Anthropic | 极高 | [PNG](images/v0__claude-sonnet5.5__xhigh.png) · [SVG](svg/v0__claude-sonnet5.5__xhigh.svg) | 窗台小黄花、黄伞与写着歌词的笔记本 |
| 09 | DeepSeek-V4.1 | DeepSeek | 高 | [PNG](images/v0__deepseek-v4.1__high.png) | 窗内夜景与底部琴键，整体偏暗 |
| 10 | DeepSeek-V4.1 | DeepSeek | 最高 | [PNG](images/v0__deepseek-v4.1__max.png) · [SVG](svg/v0__deepseek-v4.1__max.svg) | 蓝得发亮的天、树、单车与女孩，扁平风 |
| 11 | GLM-5.3 | 智谱 Zhipu | 高 | [PNG](images/v0__glm5.3__high.png) | 电线杆、双人影与单车，暖橙逆光 |
| 12 | GLM-5.3 | 智谱 Zhipu | 最高 | [PNG](images/v0__glm5.3__max.png) · [SVG](svg/v0__glm5.3__max.svg) | 灰白低对比，字与图都发虚 |
| 13 | GLM-5.3-Flash | 智谱 Zhipu | 高 | [PNG](images/v0__glm5.3-flash__high.png) · [SVG](svg/v0__glm5.3-flash__high.svg) | 雨夜教学楼，月亮与孤灯 |
| 14 | GLM-5.3-Flash | 智谱 Zhipu | 最高 | [PNG](images/v0__glm5.3-flash__max.png) · [SVG](svg/v0__glm5.3-flash__max.svg) | 雨夜撑伞人，画面底部是钢琴键 |
| 15 | GPT · astra | OpenAI | 高 | [PNG](images/v0__gpt-astra__high.png) · [SVG](svg/v0__gpt-astra__high.svg) | 空教室斜阳：木窗、旧课桌与靠窗的吉他，透视干净 |
| 16 | GPT · astra | OpenAI | 极高 | [PNG](images/v0__gpt-astra__xhigh.png) · [SVG](svg/v0__gpt-astra__xhigh.svg) | 绿窗框教室全景，课桌成排，光落在琴箱上 |
| 17 | GPT · astra | OpenAI | 最高 | [PNG](images/v0__gpt-astra__max.png) | 同题拉远视距，走廊尽头的窗光与吉他 |
| 18 | GPT-6.1 · sol | OpenAI | 高 | [PNG](images/v0__gpt-6.1__high.png) · [SVG](svg/v0__gpt-6.1__high.svg) | 校门湿石阶，少年背吉他，冷灰调，最克制 |
| 19 | GPT-6.1 · sol | OpenAI | 极高 | [PNG](images/v0__gpt-6.1__xhigh.png) · [SVG](svg/v0__gpt-6.1__xhigh.svg) | 横构图：走廊尽头的光斑与琴影 |
| 20 | GPT-6.1 · sol | OpenAI | 最高 | [PNG](images/v0__gpt-6.1__max.png) | 雨后林荫道纵深，一个人影走向旧校舍 |
| 21 | Gemini 4 · argon | Google | 标准 | [PNG](images/v0__gemini4__medium.png) · [SVG](svg/v0__gemini4__medium.svg) | 榕树、秋千、红砖楼、六线谱，信息密度最高 |
| 22 | Gemini 4 · argon | Google | 高 | [PNG](images/v0__gemini4__high.png) | 红砖楼前抱琴而坐，元素最满 |
| 23 | Kimi K3 | 月之暗面 | 最高 | [PNG](images/v0__kimi-k3__max.png) | 树荫秋千上的两个人，绿得通透 |
| 24 | MuseSparkOpen | Meta | 极高 | [PNG](images/v0__musespark__xhigh.png) · [SVG](svg/v0__musespark__xhigh.svg) | 米白底上的两个人与校舍，最像平面设计 |
| 25 | Qwen3.8-A95B | 阿里 Qwen | 标准 | [PNG](images/v0__qwen3.8-a95b__medium.png) · [SVG](svg/v0__qwen3.8-a95b__medium.svg) | 树下女孩与积水的倒影 |
| 26 | Qwen3.8-A95B | 阿里 Qwen | 最高 | [PNG](images/v0__qwen3.8-a95b__max.png) · [SVG](svg/v0__qwen3.8-a95b__max.svg) | 长椅、红伞与湿漉漉的午后 |
| 27 | Qwen3.8-Max | 阿里 Qwen | 标准 | [PNG](images/v0__qwen3.8-max__medium.png) · [SVG](svg/v0__qwen3.8-max__medium.svg) | 小黄花田与秋千上的两个人 |
| 28 | Qwen3.8-Max | 阿里 Qwen | 最高 | [PNG](images/v0__qwen3.8-max__max.png) · [SVG](svg/v0__qwen3.8-max__max.svg) | 雨中秋千与月，冷调 |

### claude.ai · 4 件

| No. | 模型 | 厂商 | 强度 | 文件 | 画面 |
| --- | --- | --- | --- | --- | --- |
| 29 | Claude Haiku 5.5 | Anthropic | 最高 | [PNG](images/claude-ai__claude-haiku5.5__max.png) | 逆光秋千剪影 + 大字，最克制的一张 |
| 30 | Claude Sonnet 5.5 | Anthropic | 高 | [PNG](images/claude-ai__claude-sonnet5.5__high.png) · [SVG](svg/claude-ai__claude-sonnet5.5__high.svg) | 钟楼校舍与草地小径，像一张真海报 |
| 31 | Claude Sonnet 5.5 | Anthropic | 极高 | [PNG](images/claude-ai__claude-sonnet5.5__xhigh.png) | 乡道、电线、云与单车，天空层次最好 |
| 32 | Claude Sonnet 5.5 | Anthropic | 极高 | [PNG](images/claude-ai__claude-sonnet5.5__xhigh__r2.png) | 同题第二跑，构图几乎复刻，云更松 |

### Trae Code · 3 件

| No. | 模型 | 厂商 | 强度 | 文件 | 画面 |
| --- | --- | --- | --- | --- | --- |
| 33 | DeepSeek-V4.1 | DeepSeek | 极高 | [PNG](images/trae__deepseek-v4.1__xhigh.png) · [SVG](svg/trae__deepseek-v4.1__xhigh.svg) | 夜色三角钢琴与撑伞人，倒影漂亮 |
| 34 | GLM-5.3-Flash | 智谱 Zhipu | 极高 | [PNG](images/trae__glm5.3-flash__xhigh.png) · [SVG](svg/trae__glm5.3-flash__xhigh.svg) | 白衬衫少年立于雨幕，光柱劈下 |
| 35 | Qwen3.8-Flash | 阿里 Qwen | 极高 | [PNG](images/trae__qwen3.8-flash__xhigh.png) · [SVG](svg/trae__qwen3.8-flash__xhigh.svg) | 教学楼前弹琴的两人，暖黄 |

### WorkBuddy · 3 件

| No. | 模型 | 厂商 | 强度 | 文件 | 画面 |
| --- | --- | --- | --- | --- | --- |
| 36 | DeepSeek-V4.1 | DeepSeek | 极高 | [PNG](images/workbuddy__deepseek-v4.1__xhigh.png) · [SVG](svg/workbuddy__deepseek-v4.1__xhigh.svg) | 雨夜窗台：晴天娃娃、吉他、小黄花 |
| 37 | GLM-5.3 | 智谱 Zhipu | 极高 | [PNG](images/workbuddy__glm5.3__xhigh.png) | 晴日校门、单车与向日葵，明快 |
| 38 | GLM-5.3-Flash | 智谱 Zhipu | 高 | [PNG](images/workbuddy__glm5.3-flash__high.png) | 极简构成：方楼、窗影、巨大的「晴天」 |

### opencode · 5 件

| No. | 模型 | 厂商 | 强度 | 文件 | 画面 |
| --- | --- | --- | --- | --- | --- |
| 39 | DeepSeek-V4.1 | DeepSeek | 高 | [PNG](images/opencode__deepseek-v4.1__high.png) | 校门、单车、琴键，规整 |
| 40 | DeepSeek-V4.1 | DeepSeek | 最高 | [PNG](images/opencode__deepseek-v4.1__max.png) | 校舍、樟树、单车、向日葵，堆得很满 |
| 41 | GLM-5.3-Flash | 智谱 Zhipu | 高 | [PNG](images/opencode__glm5.3-flash__high.png) | 雨夜街口，少年推车 |
| 42 | GLM-5.3-Flash | 智谱 Zhipu | 最高 | [PNG](images/opencode__glm5.3-flash__max.png) | 少年与单车，「晴天」像一层纱 |
| 43 | MiMo 2.6 Flash | 小米 MiMo | 高 | [PNG](images/opencode__mimo2.6-flash__high.png) · [SVG](svg/opencode__mimo2.6-flash__high.svg) | 云、草地、抱琴少年，干净 |

### 魔搭 ModelScope · 3 件

| No. | 模型 | 厂商 | 强度 | 文件 | 画面 |
| --- | --- | --- | --- | --- | --- |
| 44 | DeepSeek-V4.1 | DeepSeek | 高 | [PNG](images/modelscope__deepseek-v4.1__high.png) | 雾中校园、钢琴与一朵小黄花 |
| 45 | Qwen3.8-27B | 阿里 Qwen | 高 | [PNG](images/modelscope__qwen3.8-27b__high.png) | 逆光小路上背书包的少年 |
| 46 | Qwen3.8-Flash | 阿里 Qwen | 高 | [PNG](images/modelscope__qwen3.8-flash__high.png) · [SVG](svg/modelscope__qwen3.8-flash__high.svg) | 灰色隧道里的吉他手，最不「晴天」 |

### 商汤 SenseNova · 3 件

| No. | 模型 | 厂商 | 强度 | 文件 | 画面 |
| --- | --- | --- | --- | --- | --- |
| 47 | DeepSeek-V4.1 | DeepSeek | 高 | [PNG](images/sensetime__deepseek-v4.1__high.png) | 室内静物：吉他盒、黑胶、窗光，跳出海报模板 |
| 48 | GLM-5.2 | 智谱 Zhipu | 高 | [PNG](images/sensetime__glm5.2__high.png) | 黄昏里并肩的两人与吉他，剪影海报 |
| 49 | SenseNova · 商汤自研 | 商汤 SenseTime | 高 | [PNG](images/sensetime__sensenova__high.png) | 雨街、黑伞、巨大的「晴天」二字 |

### DeepSeek 官方 API · 1 件

| No. | 模型 | 厂商 | 强度 | 文件 | 画面 |
| --- | --- | --- | --- | --- | --- |
| 50 | DeepSeek-V4.1 | DeepSeek | 高 | [PNG](images/deepseek-api__deepseek-v4.1__high.png) | 落日长路上的单人背影，电影感 |


---

## 数据说明

- `images/` 是**全尺寸原图 PNG**（SVG 按 2× 渲染，位图保留原始截图分辨率，共约 201 MB）；`thumbs/` 是 560px 画廊缩略图；`svg/` 是模型输出的原始 `.svg`，未做任何改动。
- **`sonnet5.5-high.svg` 与 `sonnet5.5-max.svg` 字节完全一致**（同一份输出被保存了两次），已合并为一条记录，不重复计数。因此 51 份文件对应 50 条记录。
- 有 SVG 源码的作品，展示图由该 SVG 重新渲染；只有位图的作品（部分平台不提供源码），展示图由原始截图缩放而来。
- 渲染环境：Microsoft Edge 无头模式，按 viewBox 原始尺寸渲染并 2× 缩放后直接导出，不再二次压缩。中文依赖系统字体，个别作品的字体回退与原平台显示可能略有差异。

## 版权

所有画面均为模型根据提示词现场生成的原创矢量图形，非官方物料，与周杰伦及所属公司无关。
《晴天》词曲版权归原作者所有；本仓库**不包含**任何音频、歌词文本或原版视觉素材。
仅供学习与技术横评使用，请勿商用。
