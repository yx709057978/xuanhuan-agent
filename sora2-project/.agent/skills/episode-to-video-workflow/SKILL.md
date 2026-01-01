---
name: episode-to-video-workflow
description: 将小说章节转换为 Sora 2 视频的完整工作流程。Use when user wants to convert episode/chapter to video, 章节转视频, 小说转视频, or needs the full production pipeline.
---

# Episode to Video Workflow (章节转视频工作流)

> 将《末法》小说章节转换为 Sora 2 视频的标准化流程

## 目录

- [工作流概览](#工作流概览)
- [Phase 1: 前期准备](#phase-1-前期准备)
- [Phase 2: 分镜生成](#phase-2-分镜生成)
- [Phase 3: Prompt 生成](#phase-3-prompt-生成)
- [Phase 4: 视频生成](#phase-4-视频生成)
- [Phase 5: 后期整合](#phase-5-后期整合)
- [快速参考](#快速参考)

---

## 工作流概览

```
┌─────────────────────────────────────────────────────────────┐
│                    Episode-XX.md (输入)                      │
└─────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────┐
│  Phase 1: 前期准备                                           │
│  ├── 1.1 提取角色列表 → 检查角色档案                          │
│  ├── 1.2 提取场景列表 → 检查场景档案                          │
│  └── 1.3 确认视觉风格                                        │
│  使用: character-visual-bible, scene-environment-library,   │
│        xuanhuan-visual-style                                │
└─────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────┐
│  Phase 2: 分镜生成                                           │
│  ├── 2.1 拆分场景                                            │
│  ├── 2.2 确定镜头数量和类型                                   │
│  └── 2.3 生成分镜卡片                                        │
│  使用: storyboard-generator                                 │
└─────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────┐
│  Phase 3: Prompt 生成                                        │
│  ├── 3.1 为每个镜头生成 Sora prompt                          │
│  ├── 3.2 注入角色/场景描述块                                  │
│  └── 3.3 一致性检查                                          │
│  使用: sora2-prompt-generator, xuanhuan-visual-style        │
└─────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────┐
│  Phase 4: 视频生成 (Sora 2)                                  │
│  ├── 4.1 逐镜头生成                                          │
│  ├── 4.2 检查一致性                                          │
│  └── 4.3 必要时重新生成                                      │
└─────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────┐
│  Phase 5: 后期整合                                           │
│  ├── 5.1 视频剪辑                                            │
│  ├── 5.2 添加音效/配乐                                       │
│  └── 5.3 添加字幕/旁白                                       │
└─────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────┐
│                    完成的视频 (输出)                          │
└─────────────────────────────────────────────────────────────┘
```

---

## Phase 1: 前期准备

### 1.1 提取角色列表

**操作**：阅读章节，列出所有出场角色

**检查清单**：
- [ ] 主要角色是否有完整的视觉档案？
- [ ] 配角是否至少有快速卡？
- [ ] 角色的当前状态是否需要特殊变体？

**示例**（第1集）：
```
出场角色：
1. 陈十一 - 主角 [需要完整档案]
2. 吴算子 - 重要配角 [需要完整档案]
3. 沈红药 - 女主 [需要完整档案]
4. 王执事 - 炮灰反派 [需要快速卡]
5. 杂役甲 - 龙套 [通用描述即可]
```

**如果缺少档案**：
```
请求示例：
"使用 character-visual-bible 为 [角色名] 创建视觉档案，
参考 character.md 中的描述"
```

### 1.2 提取场景列表

**操作**：阅读章节，列出所有场景

**检查清单**：
- [ ] 主要场景是否有完整档案？
- [ ] 场景的时间/天气是否需要特殊变体？
- [ ] 是否有新场景需要创建？

**示例**（第1集）：
```
出场场景：
1. 青云宗山门外 - 夜晚 [需要档案]
2. 青云宗主殿前广场 - 夜晚 [需要档案]
3. 青云宗主殿内 - 夜晚 [需要档案]
4. 提纯房 - 白天 [需要档案]
```

**如果缺少档案**：
```
请求示例：
"使用 scene-environment-library 为 [场景名] 创建场景档案，
参考 Episode-XX.md 中的描述"
```

### 1.3 确认视觉风格

**操作**：确认本集的视觉风格设定

**检查项**：
- [ ] 整体色调是否符合 xuanhuan-visual-style？
- [ ] 是否有特殊场景需要调整色调？
- [ ] 特效风格是否确定？

**默认风格块**（复制用）：
```
Dark fantasy animation style, gritty and desaturated color palette,
high contrast lighting with deep shadows, film grain texture,
atmospheric dust and haze, bleak post-apocalyptic cultivation world,
dark humor undertones.
```

---

## Phase 2: 分镜生成

### 2.1 拆分场景

**操作**：将章节按场景拆分

**场景拆分标准**：
- 地点变化 = 新场景
- 时间跳跃 = 新场景
- 重大情绪转折 = 可能新场景

**示例**（第1集）：
```
场景 1: 青云宗山门外 (0:00-0:15)
场景 2: 主殿前广场 - 碰瓷 (0:15-0:45)
场景 3: 主殿内 - 签契约 (0:45-1:15)
场景 4: 提纯房 - 开锁 (1:15-1:45)
```

### 2.2 确定镜头数量

**参考标准**：

| 场景类型 | 镜头数/10秒 | 说明 |
|---------|------------|------|
| 对话场景 | 2-3 | 正反打 + 双人 |
| 动作场景 | 4-6 | 快节奏 |
| 氛围场景 | 1-2 | 长镜头 |
| 喜剧场景 | 3-4 | 反应镜头多 |

**示例**（场景2：碰瓷）：
```
时长：30秒
类型：喜剧 + 对话
镜头数：8-10个
```

### 2.3 生成分镜卡片

**请求示例**：
```
"使用 storyboard-generator 将 Episode-01.md 的场景2（碰瓷场景）
转换为分镜脚本，包含 8-10 个镜头"
```

**输出格式**：
```markdown
## 场景 2: 主殿前广场 - 碰瓷
**时长**: 30秒 | **镜头数**: 8 | **氛围**: 荒诞、喜剧

### Shot 1 (0:00-0:04)
**镜头类型**: Medium shot
**场景**: 破败广场，杂草丛生
**角色**: 陈十一落地，环顾四周
**动作**: 皱眉，准备撤退
**Sora Card**: [待生成]

### Shot 2 (0:04-0:08)
**镜头类型**: Close-up (脚部)
**场景**: 地面杂草
**角色**: 陈十一的脚踩到"杂草堆"
**动作**: 踩下去，感觉软绵绵
**Sora Card**: [待生成]

...
```

---

## Phase 3: Prompt 生成

### 3.1 为每个镜头生成 Sora Prompt

**请求示例**：
```
"使用 sora2-prompt-generator 为场景2的 Shot 1 生成完整的 Sora prompt，
注入陈十一的角色描述和青云宗广场的场景描述"
```

### 3.2 注入描述块

**Prompt 结构**：
```
[风格描述块]

[场景描述块 - 来自 scene-environment-library]

[角色描述块 - 来自 character-visual-bible]

[动作描述]

[镜头参数]
```

**完整示例**：
```
Dark fantasy animation style, gritty desaturated colors, high contrast.

Dilapidated sect courtyard at night, cracked stone floor overgrown
with weeds, broken signboard, cold blue moonlight, eerie atmosphere.

Lean young man in patched gray robe (Chen Shiyi), messy black hair
falling over left eye, sharp features, mischievous glint in eyes.

He lands softly on the ground, looks around with a frown, notices
the extreme poverty, mutters to himself and prepares to retreat.

Camera: Medium shot, eye level
Lighting: Cold blue moonlight from above
Mood: Darkly comedic, ironic
```

### 3.3 一致性检查

**检查清单**：
- [ ] 角色描述是否在所有镜头中一致？
- [ ] 场景描述是否在所有镜头中一致？
- [ ] 风格描述是否在所有镜头中一致？
- [ ] 颜色词汇是否一致？
- [ ] 光线描述是否一致？

**常见问题**：
| 问题 | 解决方案 |
|-----|---------|
| 角色外观变化 | 在每个 prompt 重复核心特征 |
| 场景不一致 | 使用相同的场景描述块 |
| 色调漂移 | 明确指定颜色名称 |

---

## Phase 4: 视频生成

### 4.1 Sora 2 生成设置

**推荐设置**：
```
Duration: 5-10 秒/镜头
Resolution: 1280x720 (16:9)
Production Level: Cinematic
Pacing: 根据场景调整
```

### 4.2 生成顺序

**建议顺序**：
1. 先生成建立镜头（确定场景基调）
2. 再生成角色特写（确定角色外观）
3. 最后生成动作镜头

### 4.3 一致性检查

**检查项**：
- [ ] 角色面部是否一致？
- [ ] 服装颜色是否一致？
- [ ] 场景元素是否一致？
- [ ] 光线是否一致？

**如果不一致**：
1. 调整 prompt，增加更多具体描述
2. 使用 Sora 的 Remix 功能微调
3. 必要时重新生成

---

## Phase 5: 后期整合

### 5.1 视频剪辑

**工具建议**：
- DaVinci Resolve（免费）
- Premiere Pro
- Final Cut Pro

**剪辑要点**：
- 按分镜顺序排列
- 调整转场（硬切为主）
- 统一色调（如有偏差）

### 5.2 音效/配乐

**音效类型**：
- 环境音（风声、虫鸣、脚步）
- 动作音效（爆炸、打斗）
- UI音效（字幕出现）

**配乐风格**：
- 整体：阴暗、压抑
- 喜剧场景：荒诞、讽刺
- 紧张场景：紧迫、不安

### 5.3 字幕/旁白

**字幕类型**：
- 对话字幕
- 独白字幕（斜体）
- 场景转换字幕
- 结尾黑屏字幕（金句）

**旁白处理**：
- 可用 AI 配音或真人配音
- 独白部分建议保留

---

## 快速参考

### 单集完整流程命令

```
Step 1: 准备
"列出 Episode-XX.md 中的所有角色和场景，检查是否有缺失的档案"

Step 2: 分镜
"使用 storyboard-generator 将 Episode-XX.md 转换为完整分镜脚本"

Step 3: Prompt
"为 [场景X] 的所有镜头生成 Sora prompt，使用 xuanhuan-visual-style 的默认风格"

Step 4: 检查
"检查生成的 prompt 的一致性，确保角色和场景描述统一"
```

### 时间估算

| 阶段 | 预计时间 | 说明 |
|-----|---------|------|
| Phase 1 | 10-30分钟 | 首次需要创建档案较久 |
| Phase 2 | 20-40分钟 | 取决于章节长度 |
| Phase 3 | 30-60分钟 | 每个镜头约3-5分钟 |
| Phase 4 | 1-3小时 | Sora 生成 + 迭代 |
| Phase 5 | 1-2小时 | 剪辑 + 音效 |

**单集总计**：约 3-6 小时（熟练后可缩短）

### 输出文件结构

```
Episode-XX/
├── 01-preparation/
│   ├── characters.md      # 本集角色列表
│   └── scenes.md          # 本集场景列表
├── 02-storyboard/
│   └── storyboard.md      # 完整分镜脚本
├── 03-prompts/
│   ├── scene-01/
│   │   ├── shot-01.txt    # 每个镜头的 prompt
│   │   ├── shot-02.txt
│   │   └── ...
│   └── scene-02/
│       └── ...
├── 04-videos/
│   ├── raw/               # Sora 生成的原始视频
│   └── selected/          # 选中的最终版本
└── 05-final/
    └── Episode-XX.mp4     # 最终成品
```

---

## 相关资源

### 配套 Skills

- `character-visual-bible` - 角色视觉档案
- `scene-environment-library` - 场景环境档案
- `storyboard-generator` - 分镜脚本生成
- `sora2-prompt-generator` - Sora prompt 生成
- `xuanhuan-visual-style` - 视觉风格指南

### 项目文件

- `xuanhuan-project/character.md` - 角色设定
- `xuanhuan-project/outline.md` - 故事大纲
- `xuanhuan-project/chapters/` - 章节内容
