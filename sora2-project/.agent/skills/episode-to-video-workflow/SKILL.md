---
name: episode-to-video-workflow
description: 将小说章节转换为 Sora 2 prompt 的完整工作流程。Use when user wants to convert episode/chapter to Sora prompts, 章节转提示词, 小说转视频素材, or needs the prompt preparation pipeline.
---

# Episode to Video Workflow (章节转 Prompt 工作流)

> 将小说章节转换为可直接用于 Sora 2 的完整 prompt 包

## 快速使用

**一句话启动**：
```
"帮我把 Episode-01 转成 Sora prompts"
```

**我会自动完成**：
1. 从小说项目读取章节（路径配置见 `project-config.md`）
2. 识别所有角色和场景
3. 检查/创建角色档案（存到 `assets/characters/`）
4. 检查/创建场景档案（存到 `assets/scenes/`）
5. 自动识别并创建新变体（如换装、受伤等）
6. 生成分镜脚本
7. 生成所有镜头的 Sora prompt
8. 输出到 `episodes/episode-XX/`

**你只需要**：
- 确保 `project-config.md` 配置了正确的小说源路径
- 一句话启动
- 复制 prompts 到 Sora 2 使用

## 项目结构

```
sora2-project/                    # 本项目（视频制作）
├── .agent/skills/                # Skills 定义
├── project-config.md             # ⭐ 小说源配置
├── assets/                       # 生成的视觉档案
│   ├── characters/
│   └── scenes/
└── episodes/                     # 生成的 prompts
    └── episode-XX/

xuanhuan-project/                 # 小说项目（输入源）
├── chapters/                     # 章节文件
│   ├── Episode-01.md
│   └── ...
├── character.md                  # 角色设定
└── outline.md                    # 大纲
```

---

## 目录

- [快速使用](#快速使用)
- [项目配置](#项目配置)
- [自动化流程详解](#自动化流程详解)
- [输出规范](#输出规范)
- [手动干预场景](#手动干预场景)
- [快速参考](#快速参考)

---

## 项目配置

在开始之前，确保 `project-config.md` 配置正确：

```yaml
# 小说项目路径
novel_source: ../xuanhuan-project

# 章节目录
chapters_dir: chapters

# 角色设定文件  
character_file: character.md
```

**切换到其他小说项目**：
```
你: "把小说源切换到 ../another-novel"
```

我会更新 `project-config.md`。

---

## 自动化流程详解

```
┌─────────────────────────────────────────────────────────────┐
│  用户输入: "帮我把 Episode-XX 转成 Sora prompts"             │
└─────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────┐
│  Step 1: 章节分析                                            │
│  ├── 读取 Episode-XX.md                                      │
│  ├── 提取所有出场角色                                        │
│  ├── 提取所有场景                                            │
│  └── 识别角色状态变化（换装、受伤等）                         │
└─────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────┐
│  Step 2: 资产检查与创建                                      │
│  ├── 检查 assets/characters/ 已有档案                        │
│  │   ├── 已有 → 复用                                        │
│  │   └── 缺失 → 自动创建                                    │
│  ├── 检查 assets/scenes/ 已有档案                            │
│  │   ├── 已有 → 复用                                        │
│  │   └── 缺失 → 自动创建                                    │
│  └── 检查是否需要新变体                                      │
│      ├── 章节描述与已有变体匹配 → 使用已有                   │
│      └── 章节描述有新状态 → 自动创建新变体                   │
└─────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────┐
│  Step 3: 分镜生成                                            │
│  ├── 按场景拆分章节                                          │
│  ├── 确定每个场景的镜头数量和类型                            │
│  └── 生成分镜卡片                                            │
└─────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────┐
│  Step 4: Prompt 生成                                         │
│  ├── 为每个镜头组合: 风格 + 场景 + 角色 + 动作               │
│  ├── 自动注入正确的变体                                      │
│  └── 一致性检查                                              │
└─────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────┐
│  Step 5: 输出                                                │
│  ├── episodes/episode-XX/metadata.md                        │
│  ├── episodes/episode-XX/storyboard.md                      │
│  └── episodes/episode-XX/prompts/scene-XX/shot-XX.txt       │
└─────────────────────────────────────────────────────────────┘
```

### 自动变体识别逻辑

我会从章节文本中自动识别角色状态变化：

| 章节描述 | 自动识别 | 动作 |
|---------|---------|------|
| "陈十一穿着破烂囚服" | 服装变化 | 创建 `[ep30-prisoner]` 变体 |
| "陈十一浑身是血" | 受伤状态 | 使用/创建 `[injured]` 变体 |
| "陈十一换上偷来的华服" | 临时装扮 | 创建 `[ep45-disguise]` 变体 |
| "陈十一一身满是暗袋的道袍" | 默认状态 | 使用 `[default]` 变体 |

### 首次 vs 后续处理

**首次处理 Episode-01**：
- 需要创建大量角色/场景档案
- 耗时较长（约 30-60 分钟）
- 建立基础资产库

**后续处理 Episode-02+**：
- 大部分资产已存在，直接复用
- 只创建新角色/场景/变体
- 耗时较短（约 10-20 分钟）

---

## 手动干预场景

大部分情况下全自动，但以下情况可能需要你确认：

| 情况 | 我会问你 |
|-----|---------|
| 角色描述模糊 | "章节中 XX 的外观描述不够详细，需要补充吗？" |
| 不确定是否新变体 | "陈十一这集'衣服有些脏'，是创建新变体还是用默认？" |
| 新角色重要性不明 | "赵二狗是重要角色还是龙套？决定档案详细程度" |
| 场景描述冲突 | "这个场景和已有档案描述有差异，以哪个为准？" |

---

## 输出规范

### 项目结构

采用**全局资产库 + 每集输出**的结构，确保跨集一致性：

```
sora2-project/
├── .agent/skills/              # Skills（工具定义）
│
├── assets/                     # ═══ 全局资产库（跨集复用）═══
│   ├── characters/             # 角色视觉档案
│   │   ├── chen-shiyi.md       # 固定特征 + 所有变体
│   │   ├── wu-suanzi.md
│   │   └── ...
│   ├── scenes/                 # 场景视觉档案
│   │   ├── qingyun-gate.md     # 固定元素 + 时间/天气变体
│   │   ├── refining-room.md
│   │   └── ...
│   └── style.md                # 项目视觉风格摘要
│
└── episodes/                   # ═══ 每集输出 ═══
    ├── episode-01/
    │   ├── metadata.md         # 本集使用的角色/场景/变体
    │   ├── storyboard.md       # 分镜脚本
    │   └── prompts/            # Sora prompts
    │       ├── scene-01/
    │       │   ├── shot-01.txt
    │       │   └── ...
    │       └── ...
    ├── episode-02/
    └── ...
```

### 资产复用流程

```
处理 Episode-01：
├── 检查 assets/characters/chen-shiyi.md
│   └── 不存在 → 创建（固定特征 + default 变体）
├── 检查本集是否需要新变体
│   └── 需要 → 在 chen-shiyi.md 添加新变体
└── 生成 prompts → 引用 [固定特征] + [指定变体]

处理 Episode-15：
├── 检查 assets/characters/chen-shiyi.md
│   └── 已存在 → 复用
├── 本集需要夜行衣造型
│   └── 在 chen-shiyi.md 添加 [ep15-nightwear] 变体
└── 生成 prompts → 引用 [固定特征] + [ep15-nightwear]

处理 Episode-30：
├── chen-shiyi.md 已有多个变体
├── 本集需要囚服造型
│   └── 添加 [ep30-prisoner] 变体
└── 生成 prompts → 引用 [固定特征] + [ep30-prisoner]
```

### Prompt 文件格式

每个 `shot-XX.txt` 包含：

```
=== SHOT INFO ===
Episode: 01
Scene: 青云宗山门外
Shot: 01/04
Duration: 4s
Type: Medium shot

=== CHARACTER REFS ===
- 陈十一: [fixed] + [default]

=== SCENE REFS ===
- 青云宗山门外: [night]

=== SORA PROMPT ===
[完整的 Sora 2 prompt，可直接复制使用]

=== NOTES ===
- 与前一镜头的衔接点
- 需要注意的一致性要素
```

### metadata.md 格式

每集的 `metadata.md` 记录本集使用的资产和变体：

```markdown
# Episode-01 Metadata

## 使用角色
| 角色 | 档案路径 | 使用变体 |
|-----|---------|---------|
| 陈十一 | assets/characters/chen-shiyi.md | [default] |
| 吴算子 | assets/characters/wu-suanzi.md | [default] |
| 王执事 | assets/characters/wang-zhishi.md | [default] |

## 使用场景
| 场景 | 档案路径 | 使用变体 |
|-----|---------|---------|
| 青云宗山门外 | assets/scenes/qingyun-gate.md | [night] |
| 主殿前广场 | assets/scenes/qingyun-plaza.md | [night] |
| 提纯房 | assets/scenes/refining-room.md | [day] |

## 本集新增资产
- [x] 新建角色: 王执事
- [x] 新建场景: 提纯房
- [ ] 新增变体: 无
```

---

## 快速参考

### 最简使用方式

```
你: "帮我把 Episode-01 转成 Sora prompts"
```

就这一句，我会自动完成所有工作。

### 可选的细化命令

| 场景 | 命令 |
|-----|------|
| 只分析不生成 | "分析 Episode-XX 需要哪些资产" |
| 只生成分镜 | "为 Episode-XX 生成分镜脚本" |
| 重新生成某个镜头 | "重新生成 Episode-XX Scene-1 Shot-3" |
| 修改角色变体 | "把陈十一的 [injured] 变体改成..." |
| 批量处理 | "帮我把 Episode-01 到 05 都转成 prompts" |

### 时间估算

| 情况 | 预计时间 |
|-----|---------|
| 首集（需创建大量档案） | 30-60 分钟 |
| 后续集（复用已有档案） | 10-20 分钟 |
| 批量处理（5集） | 1-2 小时 |

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
