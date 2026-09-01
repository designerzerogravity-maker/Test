---
name: ian-xiaohei-illustrations
description: 生成 Ian 风格的中文正文配图。用于用户要求为中文文章、帖子、博客、Notion 文档、工作流文档、方法论、流程、结构、状态、隐喻或观点生成“怪诞”“小黑”“手绘”“正文配图”“文章插图”“配图建议”“shot list”“去标题/改图”等任务；默认使用小黑 IP、纯白手绘、少量红橙蓝批注、简洁清爽但天马行空的视觉风格。
---

# Ian 小黑怪诞正文配图

本仓库通过 Cursor project skill 使用这套视觉语言。生图走 Cursor `GenerateImage`，不要调用 Codex 的 `image_gen`。

## 核心定位

为中文文章设计和生成 16:9 横版正文配图。目标不是做商业插画、PPT 信息图或可爱卡通，而是把文章里的关键判断、流程、结构、状态或隐喻，变成一张清爽、怪诞、有创意、可读但不说明书的手绘解释图。

默认视觉 IP 是“小黑”：黑色实心、白点眼、细腿、空表情，认真做一件荒诞但成立的事。小黑必须参与画面的核心动作，不能只是站在旁边当装饰。

## 先读这些参考

按任务需要读取，不要一次塞满上下文：

- `references/style-dna.md`：风格 DNA、颜色、文字、禁忌。
- `references/xiaohei-ip.md`：小黑 IP 的形象、性格、动作库和禁忌。
- `references/composition-patterns.md`：结构类型、原创隐喻方法和反复刻规则。
- `references/prompt-template.md`：单张生图提示词模板。
- `references/qa-checklist.md`：生成后检查和迭代规则。
- `assets/examples/`：只作低频视觉校准，不进入默认生成路径。不要照抄这些案例的构图、物件或标注。

## 工作流

### 1. 消化正文

先读用户给的正文、链接、Notion 页面、Markdown 文件或截图内容。提炼：

- 核心观点是什么
- 哪些段落承担认知转折
- 哪些内容适合用图解释
- 哪些地方只适合文字，不需要图

不要平均配图。优先选择“认知锚点”，例如：核心判断、两个断点、输入输出闭环、分流、前后对比、一鱼多吃、承接路径、常见坑、角色状态变化。

### 2. 先出配图策略

如果用户只是说“分析怎么配图 / 思考哪些地方需要配图”，先给 shot list。每张图写清楚：

- 放在哪个段落后
- 图的主题
- 核心意思
- 结构类型
- 小黑在图里做什么
- 建议元素
- 建议中文标注词

默认 4-8 张。文章很短时 1-3 张；长文也不要轻易超过 9 张。够用就好，避免把正文做成画册。

### 3. 单张生成（Cursor）

如果用户明确要求“生成 / 输出 / 做图 / 帮我生成”，不要停下来等确认。每张图单独调用 Cursor 的 `GenerateImage` 工具（`cursor` namespace），不要把多张图拼在一张里。

调用约定：

1. 先 `GetDynamicTools` 确认 `cursor` / `GenerateImage` 的参数。
2. 按 `references/prompt-template.md` 填好英文提示词，作为 `description`。
3. 设置 `aspect_ratio` 为 `"16:9"`。
4. 设置 `filename` 为 `01-topic-name.png` 这种顺序名。
5. **风格校准（每次最多 2 张，只借线条密度/留白/小黑外形，不借构图）：** 把本 skill 里 `assets/examples/` 中的图放进 `reference_image_paths`。轮换使用不同样例，避免新图长得像同一张旧案例。默认轮换：
   - 第 1 张：`assets/examples/02-minimum-loop.png` + `assets/examples/13-system-bearing.png`
   - 第 2 张：`assets/examples/06-three-sources.png` + `assets/examples/14-trust-bridge.png`
   - 第 3 张：`assets/examples/07-three-content-jobs.png` + `assets/examples/10-information-well.png`
   - 之后循环。路径要用本 skill 目录的绝对路径。
6. 提示词里明确写：match the *line weight, white space, deadpan 小黑 silhouette, and sparse red/orange/blue handwriting* of the reference images; **do not copy their objects, layout, or labels**.

每张图只讲一个核心结构。提示词必须包含：

- 16:9 横版中文正文配图
- 纯白背景
- 黑色手绘线稿
- 少量红色/橙色/蓝色中文手写批注
- 大量留白
- 小黑作为核心动作主体
- 禁止 PPT、商业插画、幼稚可爱、复杂架构、左上角类型标题

不要复刻过往案例。案例只提供风格密度和小黑参与方式，不能直接复用“传送带断点 / 小黑拉线 / 素材鱼 / 盖章工具箱 / 常见坑路径”等已有构图，除非用户明确要求复刻某张图。每次都要从当前文章重新发明一个奇怪但成立的隐喻。

### 4. 检查与迭代

生成后检查 `references/qa-checklist.md`。如果出现以下问题，优先重生成或局部编辑：

- 小黑只是装饰
- 画面太满
- 太像流程图/PPT
- 中文太多或错字严重
- 左上角出现“常见坑/流程图/系统架构图”等标题
- 画风太可爱、幼稚、死板
- 背景不是干净白底

### 5. 保存交付

`GenerateImage` 会把文件写到工具自己的目录。生成后立刻把最终 PNG 复制到 workspace：

```text
assets/<article-slug>-illustrations/
```

按顺序命名：

```text
01-topic-name.png
02-topic-name.png
```

保留原始生成文件，不要覆盖已有资产，除非用户明确要求替换。

如果用户只要 shot list、不要生图，就停在第 2 步，不要调用 `GenerateImage`。

## 输出口径

生成前的策略输出要短而准。生成后的交付要包含：

- 生成了几张
- 每张图的用途
- 保存路径
- 哪些图最稳，哪些图是可选

不要长篇解释风格理论；让图自己说话。
