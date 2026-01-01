---
name: scene-environment-library
description: 创建和管理场景环境视觉档案，为 Sora 2 提供一致的场景描述。Use when user asks about scene design, 场景设定, 环境描述, location description, setting, background, or needs to maintain scene consistency across shots.
---

# Scene Environment Library (场景环境库)

> 为 AI 视频生成建立场景环境档案，确保跨镜头的场景一致性

## 目录

- [When to Use](#when-to-use)
- [核心概念](#核心概念)
- [场景描述公式](#场景描述公式)
- [场景档案结构](#场景档案结构)
- [场景一致性技术](#场景一致性技术)
- [场景变体系统](#场景变体系统)
- [最佳实践](#最佳实践)

---

## When to Use

- 用户需要创建场景/环境视觉设定
- 用户需要在多个镜头中保持场景一致
- 用户要求建立场景档案/环境库
- 用户提到"场景设计"、"环境描述"、"location"
- 用户需要描述天气、光线、氛围

**不适用场景**:
- 角色视觉设计（使用 character-visual-bible）
- 直接生成 Sora prompt（使用 sora2-prompt-generator）
- 分镜脚本生成（使用 storyboard-generator）

---

## 核心概念

### Sora 2 场景理解能力

Sora 2 对场景有很强的理解能力：
- **物理模拟**: 理解材质、重力、流体、光线折射
- **环境交互**: 风吹动衣服、雨水打在地面、烟雾飘散
- **光影效果**: 反射、阴影、体积光、霓虹灯效果

### 场景描述的关键维度

| 维度 | 内容 | 示例 |
|-----|------|------|
| 地点类型 | 具体的场所 | abandoned warehouse, neon-lit alley |
| 时间 | 时段、季节 | golden hour, winter night |
| 天气 | 气象条件 | heavy rain, thick fog |
| 光线 | 光源、质量 | soft window light, harsh fluorescent |
| 氛围 | 情绪、风格 | gritty, ethereal, tense |
| 物理细节 | 材质、交互 | wet asphalt reflecting lights |

---

## 场景描述公式

### 基础公式

```
[地点类型] + [时间] + [天气] + [光线] + [氛围] + [物理细节]
```

### 完整模板

```
Scene: [场景名称]
Location: [具体地点类型和建筑风格]
Time: [时间段和季节]
Weather: [天气条件和环境效果]
Lighting: [主光源、辅助光、光线质量]
Atmosphere: [情绪氛围词]
Physical Details: [材质、表面、交互效果]
Color Palette: [3-5个主要颜色]
```

### 示例

```
Scene: 废弃工厂
Location: Abandoned industrial warehouse, brutalist concrete structure, 
         broken windows, rusted machinery
Time: Late night, winter
Weather: Heavy rain outside, water dripping through ceiling holes
Lighting: Dim moonlight through broken skylights, occasional lightning flashes,
         single flickering fluorescent tube
Atmosphere: Gritty, tense, isolated, decaying
Physical Details: Wet concrete floor with puddles reflecting light,
                 rust stains on walls, dust particles in light beams
Color Palette: Steel gray, rust orange, cold blue, deep shadow black
```

---

## 场景档案结构

### 快速场景卡

```markdown
# [场景名] 快速卡

**一句话描述**: [20字以内核心特征]

## Core Prompt (复制用)
```
[50-80字完整场景描述]
```

## 颜色方案
- 主色: [颜色]
- 副色: [颜色]
- 点缀: [颜色]

## 关键视觉锚点
1. [最重要的场景特征]
2. [第二重要特征]
3. [第三重要特征]
```

### 完整场景档案

```markdown
# [场景名] 完整档案

## 基础信息
- **场景类型**: [室内/室外/混合]
- **出现频率**: [高/中/低]
- **重要性**: [主场景/次要场景/过渡场景]

## 地点描述
- **类型**: [具体场所类型]
- **建筑风格**: [风格描述]
- **规模**: [大小描述]
- **状态**: [新旧、整洁度]

## 环境条件
- **默认时间**: [时段]
- **默认天气**: [天气]
- **季节**: [季节]

## 光线设定
- **主光源**: [描述]
- **辅助光**: [描述]
- **光线质量**: [硬/软/混合]
- **光线方向**: [描述]

## 氛围与情绪
- **主要氛围**: [词汇]
- **情绪基调**: [词汇]
- **视觉风格**: [词汇]

## 物理细节
- **地面材质**: [描述]
- **墙面材质**: [描述]
- **特殊效果**: [烟雾/灰尘/水等]
- **环境交互**: [风/雨/光等如何影响场景]

## 颜色方案
| 用途 | 颜色 | 应用 |
|-----|------|------|
| 主色 | [颜色] | [用于什么] |
| 副色 | [颜色] | [用于什么] |
| 点缀 | [颜色] | [用于什么] |

## Sora Prompt 描述块
```
[完整场景描述，80-100字]
```

## 场景变体
- 白天版: [简述]
- 夜晚版: [简述]
- 雨天版: [简述]
```

---

## 场景一致性技术

### 技术 1: 场景锚点复用

创建固定的场景描述块，在所有相关镜头中复用：

```
【场景锚点 - 每次必须包含】
Abandoned warehouse interior, concrete walls with rust stains,
broken skylights letting in cold blue moonlight, wet floor
with scattered debris, single flickering fluorescent light.
```

### 技术 2: 颜色锚点系统

为场景指定 3-5 个固定颜色：

```
场景配色方案:
- 主色: steel gray (混凝土墙)
- 副色: rust orange (锈迹)
- 点缀色: cold blue (月光)
- 阴影色: deep black
- 高光色: pale white (灯光)
```

### 技术 3: 光线一致性

在所有镜头中保持相同的光线描述：

```
✅ 一致:
Shot 1: "moonlight through broken skylights, single flickering fluorescent"
Shot 2: "moonlight through broken skylights, single flickering fluorescent"

❌ 不一致:
Shot 1: "moonlight through skylights"
Shot 2: "dim warehouse lighting"
```

### 技术 4: 物理细节重复

重复关键的物理/材质描述：

```
每张卡片重复:
- wet concrete floor (湿润的混凝土地面)
- puddles reflecting light (水坑反射光线)
- dust particles in light beams (光束中的灰尘)
```

---

## 场景变体系统

同一场景在不同条件下的视觉变化：

### 时间变体

| 时段 | 光线变化 | 氛围变化 |
|-----|---------|---------|
| 黎明 | 柔和的粉蓝色光 | 宁静、希望 |
| 上午 | 明亮的自然光 | 清新、活力 |
| 正午 | 强烈的顶光 | 炎热、刺眼 |
| 黄昏 | 金色/橙色暖光 | 怀旧、浪漫 |
| 夜晚 | 人工光/月光 | 神秘、危险 |

### 天气变体

| 天气 | 视觉效果 | 物理交互 |
|-----|---------|---------|
| 晴天 | 清晰、高对比 | 阳光投射阴影 |
| 阴天 | 柔和、低对比 | 漫射光、无明显阴影 |
| 雨天 | 湿润、反射 | 水滴、水坑、雨声 |
| 雾天 | 朦胧、低能见度 | 体积雾、轮廓模糊 |
| 雪天 | 明亮、冷色调 | 积雪、飘雪、脚印 |

### 变体描述模板

```markdown
## [场景名] - [变体名] 变体

**基于**: 默认场景
**变化条件**: [时间/天气/状态变化]

**变化点**:
- 光线: [变化描述]
- 颜色: [变化描述]
- 氛围: [变化描述]
- 物理效果: [变化描述]

**Sora 描述**:
```
[此变体的完整描述]
```
```

---

## 最佳实践

### Do ✅

- 使用**具体的地点类型**（"abandoned warehouse" 而非 "building"）
- 指定**3-5个颜色锚点**保持色调一致
- 描述**物理材质**（wet asphalt, rusted metal, cracked concrete）
- 在每个镜头**重复关键场景特征**
- 为重要场景准备**多个变体**
- 描述**光线如何与环境交互**（reflections, shadows, light beams）

### Don't ❌

- 使用模糊词汇（"nice place", "dark room"）
- 每个镜头用不同的场景描述方式
- 忽略光线和天气描述
- 只描述场景类型，不描述状态和细节
- 在不同镜头使用不同的颜色词汇

### 场景一致性检查清单

- [ ] 是否有可复用的 Core Prompt 描述块？
- [ ] 颜色方案是否确定（有具体颜色名）？
- [ ] 光线描述是否在所有镜头一致？
- [ ] 物理细节是否重复提及？
- [ ] 是否准备了必要的场景变体？

---

## 相关资源

### 本 Skill 附属文件

- [references/location-types.md](references/location-types.md) - 场景类型词库
- [references/weather-lighting.md](references/weather-lighting.md) - 天气与光线词库
- [references/atmosphere-mood.md](references/atmosphere-mood.md) - 氛围与情绪词库
- [references/scene-template.md](references/scene-template.md) - 场景档案模板

### 配套 Skills

- `sora2-prompt-generator` - 生成 Sora prompt
- `storyboard-generator` - 分镜脚本生成
- `character-visual-bible` - 角色视觉设计

### 外部参考

- [Sora 2 Prompting Guide](https://cookbook.openai.com/examples/sora/sora2_prompting_guide)
- [Veo Video Generation Prompt Guide](https://cloud.google.com/vertex-ai/generative-ai/docs/video/video-gen-prompt-guide)
