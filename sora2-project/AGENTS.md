# AGENTS

<skills_system priority="1">

## Available Skills

<!-- SKILLS_TABLE_START -->
<usage>
When users ask you to perform tasks, check if any of the available skills below can help complete the task more effectively. Skills provide specialized capabilities and domain knowledge.

How to use skills:
- Invoke: Bash("openskills read <skill-name>")
- The skill content will load with detailed instructions on how to complete the task
- Base directory provided in output for resolving bundled resources (references/, scripts/, assets/)

Usage notes:
- Only use skills listed in <available_skills> below
- Do not invoke a skill that is already loaded in your context
- Each skill invocation is stateless
</usage>

<available_skills>

<skill>
<name>character-visual-bible</name>
<description>创建和维护角色视觉设定，确保 Sora 2 生成中的角色一致性。Use when user asks about character design, 角色设定, 人设, 角色一致性, character consistency, visual bible, or needs to maintain character appearance across shots.</description>
<location>project</location>
</skill>

<skill>
<name>episode-to-video-workflow</name>
<description>将小说章节转换为 Sora 2 prompt 的完整工作流程。Use when user wants to convert episode/chapter to Sora prompts, 章节转提示词, 小说转视频素材, or needs the prompt preparation pipeline.</description>
<location>project</location>
</skill>

<skill>
<name>scene-environment-library</name>
<description>创建和管理场景环境视觉档案，为 Sora 2 提供一致的场景描述。Use when user asks about scene design, 场景设定, 环境描述, location description, setting, background, or needs to maintain scene consistency across shots.</description>
<location>project</location>
</skill>

<skill>
<name>sora2-prompt-generator</name>
<description>Generates professional Sora 2 video prompts with cinematic parameters and storyboard format. Use when user asks to create AI video prompts, write Sora prompts, or mentions "Sora 2", "视频生成", "AI视频", "text-to-video", "storyboard", "分镜".</description>
<location>project</location>
</skill>

<skill>
<name>storyboard-generator</name>
<description>将小说章节/剧本拆解为 Sora 2 可用的分镜脚本。Use when user asks to create storyboard, breakdown scenes, 分镜, 拆解场景, 场景卡片, or convert script/novel to video shots.</description>
<location>project</location>
</skill>

<skill>
<name>xuanhuan-visual-style</name>
<description>《末法》玄幻短剧的视觉风格指南，定义整体美学、色调、特效风格。Use when user asks about visual style, 视觉风格, 画面风格, art direction, or needs guidance on the overall look of the xuanhuan project.</description>
<location>project</location>
</skill>

</available_skills>
<!-- SKILLS_TABLE_END -->

</skills_system>
