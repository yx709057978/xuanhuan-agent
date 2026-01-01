---
name: sora2-prompt-generator
description: Generates professional Sora 2 video prompts with cinematic parameters and storyboard format. Use when user asks to create AI video prompts, write Sora prompts, or mentions "Sora 2", "视频生成", "AI视频", "text-to-video", "storyboard", "分镜".
---

# Sora 2 Prompt Generator

> 专业的 Sora 2 视频 Prompt 生成器，基于官方指南和最佳实践

## 目录

- [When to Use](#when-to-use)
- [核心原则](#核心原则)
- [Prompt 结构](#prompt-结构)
- [Storyboard 模式](#storyboard-模式)
- [参数速查](#参数速查)
- [快速示例](#快速示例)
- [最佳实践](#最佳实践)
- [故障排除](#故障排除)
- [相关资源](#相关资源)

---

## When to Use

- 用户要求生成 Sora 2 视频 prompt
- 用户提到 "AI视频"、"视频生成"、"text-to-video"、"分镜"
- 用户想要创建电影级别的视频描述
- 用户需要使用 Storyboard 分镜模式
- 用户需要优化现有的视频 prompt
- 用户询问特定风格（如"吉卜力风格"、"赛博朋克"）的 prompt 写法

**不适用场景**:
- 用户只是询问 Sora 2 的功能介绍（非 prompt 生成）
- 用户需要图片生成 prompt（Midjourney/DALL-E 等）

---

## 核心原则

### 1. 像给摄影师简报一样写 Prompt

把 prompt 当作给从未看过你分镜的摄影师的简报。细节越具体，结果越可控。

### 2. 弱 vs 强 Prompt 对比

| 弱 ❌ | 强 ✅ |
|------|------|
| "A beautiful street at night" | "Wet asphalt, zebra crosswalk, neon signs reflecting in puddles" |
| "Person moves quickly" | "Cyclist pedals three times, brakes, and stops at crosswalk" |
| "Cinematic look" | "Anamorphic 2.0x lens, shallow DOF, volumetric light" |
| "brightly lit room" | "soft window light with a warm lamp fill and a cool edge from the hallway" |

### 3. 一个镜头一个动作

- 每个镜头：一个清晰的摄像机运动 + 一个清晰的主体动作
- 用节拍描述动作："Actor takes four steps to the window, pauses, and pulls the curtain"

### 4. 短片段效果更好

- 建议用多个短片段拼接，而非一个长片段
- 模型在短片段中更可靠地遵循指令

---

## Prompt 结构

### 基础模板

```
[场景描述：角色、服装、场景、天气等细节]

Cinematography:
Camera shot: [取景和角度]
Mood: [整体氛围]

Actions:
- [动作1：具体的节拍或手势]
- [动作2：另一个明确的动作]
- [动作3：动作或对话]

Dialogue:
[对话内容，保持简短]
```

### Shot List 模板（推荐）

像导演一样用镜头列表结构化 prompt：

```
Scene: [场景/时间/天气]
Subject/action: [谁，做什么，情绪/节奏]
Camera: [角度, 取景, 镜头, 运动, 焦点]
Lighting: [光源, 方向, 氛围, 颜色]
Physics: [材质, 力, 交互]
Audio: [环境音, 1-2个音效, 一句对话]
Exclusions: [要避免的元素]
```

---

## Storyboard 模式

Storyboard 是 Sora 2 的高级编辑工具，让你在时间线上精确控制每个动作和场景。

### Storyboard 工作原理

- 每张卡片（Card）代表视频中的一个时刻
- 卡片描述特定时间点的场景、角色和动作
- 卡片之间的间距控制过渡节奏

### Storyboard 格式

```
[Card 1 - 0:00]
场景描述：初始状态
动作：角色的起始姿态/动作

[Card 2 - 0:05]
场景描述：中间状态
动作：关键动作发生

[Card 3 - 0:10]
场景描述：结束状态
动作：收尾动作
```

### Storyboard 示例

```
[Card 1 - 开始]
一只红色仙鹤站在溪流中，黄色尾羽在微风中轻轻摆动。
阳光从左侧照射，水面泛着金色光芒。

[Card 2 - 中间]
仙鹤缓缓低下头，准备将喙伸入水中。
水面开始出现涟漪。

[Card 3 - 结束]
仙鹤的头完全浸入水中捕鱼。
水花四溅，阳光在水珠上折射出彩虹。
```

### Storyboard 技巧

- **卡片间距**：太近会产生突兀剪切，太远会添加多余细节
- **保持适中距离**：创造最平滑的过渡
- **单独编辑每张卡片**：可以微调描述和位置
- **线性叙事**：当前版本按线性时间线排列

---

## 参数速查

### Basic 基础参数

| 参数 | 选项 | 说明 |
|-----|------|-----|
| Duration | 10s / 15s | 普通用户可用时长 |
| Resolution | 720x1280 (9:16) / 1280x720 (16:9) | 竖屏或横屏 |
| Production Level | Raw → Casual → Balanced → Cinematic → Ultra | 制作级别 |
| Pacing | Calm → Moderate → Chaotic | 节奏 |

### 热门风格预设（精选）

**电影/写实**: Cinematic Realism, Film Noir, 70s Film Stock, Documentary Style

**CG/3D动画**: Pixar/Disney 3D, DreamWorks, Claymation, Papercraft World

**日本动漫**: Studio Ghibli, Makoto Shinkai, Production I.G, Shonen Action

**赛博朋克**: Cyberpunk Neon, Blade Runner Aesthetic, Synthwave

**监控风格**: CCTV Security, Bodycam Footage, Drone Aerial

**复古风格**: 80s Aesthetic, 90s Sitcom, VHS Retro

> 📚 完整 70+ 风格列表见 [references/style-presets.md](references/style-presets.md)

### Cinematography 摄影参数

**Camera Shot**: Wide establishing / Medium / Close-up / Tracking / Handheld / Static

**Lens**: 24mm wide / 35mm balanced / 50mm standard / 85mm portrait / Anamorphic

**Lighting**: Golden hour / Soft window / Neon / Three-point / Candlelight

**Mood**: Nostalgic / Tense / Playful / Mysterious / Epic / Romantic

### Audio 音频参数

**Music**: Ambient, Orchestral, Electronic, Piano, Epic, Jazz

**Sound Effects**: Nature, Urban, Mechanical, Foley, Weather

---

## 快速示例

### 示例1：标准 Prompt

**User Request**: "帮我写一个东京街头时尚女性的视频 prompt"

**Output**:
```
A stylish woman walks down a Tokyo street filled with warm glowing neon. She wears a black leather jacket, a long red dress, and black boots. The street is damp and reflective. Many pedestrians walk about.

Camera: tracking shot, eye level
Lens: 35mm, shallow depth of field
Lighting: neon lights with colorful reflections
Mood: cinematic, urban, confident
```

### 示例2：Storyboard 格式

**User Request**: "10秒的分镜，仙鹤捕鱼"

**Output**:
```
[Card 1 - 0:00]
一只红色仙鹤站在溪流中，黄色尾羽在微风中轻轻摆动。
阳光从左侧照射，水面泛着金色光芒。

[Card 2 - 0:05]
仙鹤缓缓低下头，准备将喙伸入水中。
水面开始出现涟漪。

[Card 3 - 0:10]
仙鹤的头完全浸入水中捕鱼。
水花四溅，阳光在水珠上折射出彩虹。
```

### 示例3：吉卜力风格

**User Request**: "吉卜力风格的乡村少女"

**Output**:
```
Style: Studio Ghibli hand-painted animation with soft watercolor textures.

A young girl in a simple blue dress sits on a grassy hillside overlooking a peaceful countryside. Fluffy white clouds drift slowly across a brilliant blue sky. Wildflowers sway gently in the breeze.

Camera: wide establishing shot, static with subtle breathing movement
Lighting: soft diffused daylight, warm afternoon glow
Mood: peaceful, nostalgic, dreamlike

Actions:
- Wind catches her hair, lifting it gently
- She closes her eyes and takes a deep breath
- A small spirit creature peeks out from the tall grass
```

> 📚 更多完整示例见 [references/examples.md](references/examples.md)

---

## 最佳实践

### Do ✅

- 使用具体的动词和名词（"cyclist pedals three times" 而非 "person moves"）
- 描述可见的结果
- 用节拍描述动作时间
- 命名 3-5 个颜色锚点
- 保持每个镜头一个主要动作
- 使用 Storyboard 控制复杂序列

### Don't ❌

- 使用模糊词汇如 "beautiful", "nice", "cinematic look"
- 在一个镜头中塞入太多动作
- 忽略灯光和色彩描述
- 写过长的对话（10秒约2-3句）
- Storyboard 卡片间距太近或太远

### 迭代技巧

1. **从简单开始**：先固定摄像机，简化动作
2. **逐步添加复杂度**：一次只改一个元素
3. **使用 Remix**：说明要改什么，如 "same shot, switch to 85mm"

---

## 故障排除

| 问题 | 原因 | 解决方案 |
|------|------|---------|
| 动作不自然 | 物理描述过于复杂 | 简化交互，减少同时发生的动作 |
| 角色不一致 | 描述不够具体 | 在每张 Storyboard 卡片重复关键特征 |
| 过渡突兀 | 卡片间距不当 | 调整 Storyboard 卡片时间间距 |
| 灯光不对 | 光源描述模糊 | 明确光源方向、颜色和强度 |
| 风格不准确 | 风格词汇太泛 | 使用具体的风格参考（如 "Studio Ghibli" 而非 "anime"） |
| 色彩不稳定 | 缺少颜色锚点 | 命名 3-5 个具体颜色（teal, rust, amber） |

### 验证 Prompt 质量

生成 prompt 后，检查以下项目：

- [ ] 场景描述是否具体且可视化？
- [ ] 动作是否用节拍描述？
- [ ] 是否包含镜头和灯光信息？
- [ ] 色彩是否有锚点？
- [ ] 时长是否合适（10-15秒）？
- [ ] 是否避免了模糊词汇？

---

## 快速参考

### Prompt 公式

```
[主体描述] + [动作描述] + [环境描述] + [摄影参数] + [氛围/风格]
```

### 最小可用 Prompt

```
[场景描述，100-200字]

Camera: [镜头类型]
Lighting: [灯光描述]
Mood: [氛围词]
```

---

## 相关资源

### 本 Skill 附属文件

- [references/style-presets.md](references/style-presets.md) - 70+ 完整风格预设列表
- [references/examples.md](references/examples.md) - 10个完整输入-输出示例

### 外部资源

- [OpenAI Sora 2 官方 Prompting Guide](https://cookbook.openai.com/examples/sora/sora2_prompting_guide)
- [Sora 2 官方发布页](https://openai.com/index/sora-2/)
- [awesome_sora2_prompt (GitHub)](https://github.com/zhangchenchen/awesome_sora2_prompt) - 社区 prompt 收集
