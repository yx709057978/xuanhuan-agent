# 项目配置 (Project Config)

> 配置当前视频项目对接的小说源

## 小说源配置

```yaml
# 小说项目路径（相对于 workspace 或绝对路径）
novel_source: ../xuanhuan-project

# 章节目录
chapters_dir: chapters

# 角色设定文件
character_file: character.md

# 大纲文件
outline_file: outline.md
```

## 当前对接

| 配置项 | 路径 |
|-------|------|
| 小说项目 | `../xuanhuan-project` |
| 章节目录 | `../xuanhuan-project/chapters/` |
| 角色设定 | `../xuanhuan-project/character.md` |
| 大纲 | `../xuanhuan-project/outline.md` |

## 输出目录

| 输出类型 | 路径 |
|---------|------|
| 角色档案 | `./assets/characters/` |
| 场景档案 | `./assets/scenes/` |
| 分镜脚本 | `./episodes/episode-XX/storyboard.md` |
| Sora Prompts | `./episodes/episode-XX/prompts/` |

## 使用方式

配置好后，直接说：
```
"帮我把 Episode-01 转成 Sora prompts"
```

我会自动：
1. 从 `../xuanhuan-project/chapters/Episode-01.md` 读取章节
2. 参考 `../xuanhuan-project/character.md` 获取角色信息
3. 输出到 `./assets/` 和 `./episodes/`

## 切换小说项目

如果要对接其他小说项目，修改上面的 `novel_source` 即可：
```yaml
novel_source: ../another-novel-project
```
