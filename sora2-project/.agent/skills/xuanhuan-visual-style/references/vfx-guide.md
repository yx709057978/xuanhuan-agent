# 特效详细指南 (VFX Guide)

> 《末法》项目的特效视觉规范

---

## 灵气/灵力特效

### 正常灵气

**视觉特征**：
- 形态：流动的光丝、漂浮的粒子
- 颜色：冷蓝色 (#4169E1) 为主
- 透明度：半透明，可见但不遮挡
- 动态：缓慢流动、轻微脉动

**Sora 描述模板**：
```
"Wisps of pale blue spirit energy, flowing like luminous smoke,
tiny glowing particles drifting slowly, semi-transparent,
gentle pulsing glow, ethereal and mystical"
```

**变体**：

| 状态 | 颜色变化 | 形态变化 |
|-----|---------|---------|
| 微弱 | 更淡、更透明 | 稀疏、断续 |
| 强盛 | 更亮、更饱和 | 密集、流畅 |
| 吸收中 | 向中心汇聚 | 漩涡状 |
| 释放中 | 向外扩散 | 爆发状 |

### 污染灵气

**视觉特征**：
- 形态：粘稠、油腻的流动
- 颜色：毒绿 (#7FFF00) + 病紫 (#4B0082)
- 透明度：较不透明，有实体感
- 动态：不规则蠕动、留下残迹

**Sora 描述模板**：
```
"Corrupted spirit energy, sickly green-purple color,
viscous and oily texture, leaving dark residue trails,
irregular pulsing, toxic and unsettling appearance"
```

### 灵气暴走（高潮场景）

**视觉特征**：
- 形态：狂暴的漩涡、闪电
- 颜色：品红 (#FF00FF) + 白色闪电
- 透明度：核心过曝，边缘半透明
- 动态：快速旋转、不稳定闪烁

**Sora 描述模板**：
```
"Rampaging spirit energy storm, violent magenta vortex,
white lightning crackling within, unstable pulsing,
blinding at center, chaotic and dangerous"
```

---

## 阵法特效

### 正常阵法

**视觉特征**：
- 符文：金色 (#FFD700)，古篆字体风格
- 线条：蓝色 (#4169E1) 能量连线
- 形态：几何图案，圆形为主
- 动态：缓慢旋转，符文悬浮

**Sora 描述模板**：
```
"Mystical array formation, golden runes floating in circular
pattern, blue energy lines connecting nodes, slowly rotating,
ancient symbols glowing with power, geometric precision"
```

**层次结构**：
```
第一层：地面/空中的主圆
第二层：内部的几何图案
第三层：悬浮的符文
第四层：连接的能量线
第五层：外围的光晕
```

### 破败阵法（青云宗）

**视觉特征**：
- 符文：暗金 (#B8860B)，部分缺失
- 线条：灰蓝 (#708090)，断断续续
- 形态：不完整，有裂痕
- 动态：微弱闪烁，随时熄灭

**Sora 描述模板**：
```
"Decrepit array formation, faded golden runes barely visible,
some symbols missing or corrupted, flickering weakly,
cracked pattern on weathered stone, pathetic remnant"
```

### 阵法激活

**视觉特征**：
- 从中心向外扩散
- 符文依次亮起
- 能量线快速连接
- 最终形成完整图案

**Sora 描述模板**：
```
"Array activating, light spreading from center outward,
runes lighting up in sequence, energy lines rapidly connecting,
building to full brightness, power surge visible"
```

---

## 爆炸特效

### 小型爆炸（火雷子）

**视觉特征**：
- 规模：2-3米范围
- 火焰：橙红色，快速消散
- 烟雾：黑灰色，向上飘散
- 碎片：小型碎片飞溅

**Sora 描述模板**：
```
"Small explosion, burst of orange flames, black smoke rising,
small debris flying outward, quick flash then dissipating,
localized destruction"
```

### 中型爆炸（仓库爆炸）

**视觉特征**：
- 规模：10-20米范围
- 火焰：黄橙红渐变，持续燃烧
- 烟雾：浓厚黑烟，蘑菇云状
- 碎片：大型碎片、木板、瓦片
- 冲击波：可见的空气扭曲

**Sora 描述模板**：
```
"Medium explosion, massive fireball of yellow-orange flames,
thick black smoke forming mushroom cloud, large debris flying,
visible shockwave distorting air, sustained burning aftermath"
```

### 大型爆炸（灵脉爆炸）

**视觉特征**：
- 规模：整个建筑/区域
- 火焰：白热核心，蓝色灵气混合
- 烟雾：遮天蔽日
- 碎片：建筑碎块、人体
- 冲击波：强烈的环形扩散

**Sora 描述模板**：
```
"Massive explosion, blinding white-hot core with blue spirit
energy, enormous fireball engulfing entire structure, debris
and bodies flying, powerful shockwave flattening surroundings,
apocalyptic destruction"
```

### 灵气爆炸（最终决战）

**视觉特征**：
- 规模：整个矿坑
- 颜色：蓝白灵气 + 紫红暴走
- 形态：无数漩涡同时爆发
- 效果：人体膨胀、炸裂

**Sora 描述模板**：
```
"Catastrophic spirit energy explosion, thousands of blue-white
vortexes erupting simultaneously, purple-red chaotic energy
mixing in, bodies swelling and bursting, blinding light storm,
total annihilation"
```

---

## 异化特效

### 轻度异化（炼气期）

**视觉特征**：
- 鳞片：零星出现，可隐藏
- 血管：发黑，隐约可见
- 眼睛：偶尔闪烁异色
- 过程：缓慢、不明显

**Sora 描述模板**：
```
"Subtle mutation, faint gray patches appearing on skin,
darkened veins barely visible, eyes occasionally flashing
with unnatural glint, unsettling but concealable"
```

### 中度异化（筑基期）

**视觉特征**：
- 鳞片/甲壳：大面积覆盖
- 骨骼：变形、突出
- 面部：扭曲、獠牙
- 过程：痛苦、明显

**Sora 描述模板**：
```
"Significant mutation, scales spreading across skin,
bones cracking and reshaping visibly, face distorting,
fangs emerging, painful transformation, clearly inhuman"
```

### 重度异化（金丹期）

**视觉特征**：
- 机械化：金属部件替换肉体
- 灵体化：部分身体半透明
- 形态：完全非人
- 过程：已完成，稳定

**Sora 描述模板**：
```
"Complete transformation, mechanical parts replacing flesh,
tubes and wires integrated into body, half the face a metal
mask, other half decaying organic matter, utterly inhuman
abomination"
```

---

## 环境特效

### 灰尘/粒子

**Sora 描述模板**：
```
"Dust motes floating in shaft of light, particles drifting
slowly, visible in light beams, adding atmosphere and age"
```

### 烟雾/雾气

**Sora 描述模板**：
```
"Thin mist at ground level, wisps of smoke drifting,
reducing visibility, adding mystery and depth"
```

### 火光/火把

**Sora 描述模板**：
```
"Flickering torchlight, warm orange glow, dancing shadows,
light source wavering, creating dynamic lighting"
```

### 雨水

**Sora 描述模板**：
```
"Heavy rain falling, water streaming down surfaces,
puddles forming, splashing on impact, wet reflections"
```

### 灵石光芒

**Sora 描述模板**：
```
"Faint blue glow from spirit stones embedded in rock,
pulsing softly, providing minimal illumination in darkness"
```

---

## 战斗特效

### 近战攻击

**Sora 描述模板**：
```
"Swift melee strike, motion blur on weapon, impact spark,
dust kicked up, target recoiling from blow"
```

### 灵力攻击

**Sora 描述模板**：
```
"Spirit energy blast, blue-white projectile streaking forward,
trailing light particles, impact explosion of energy"
```

### 防御/护盾

**Sora 描述模板**：
```
"Defensive barrier, translucent blue shield materializing,
hexagonal pattern visible, attacks splashing against surface"
```

### 受伤/流血

**Sora 描述模板**：
```
"Wound opening, dark blood spraying, pain visible on face,
staggering from impact, blood dripping to ground"
```

---

## 特效组合示例

### 提纯炉爆炸场景

```
"Refining furnace overloading, warning lights flashing red,
spirit energy leaking in unstable streams, pressure building,
then violent explosion - orange flames mixed with blue spirit
energy, black smoke billowing, debris flying, workers thrown
back by shockwave, aftermath of burning wreckage"
```

### 灵气吸食场景

```
"Worker secretly absorbing spirit energy from array, small
blue vortex forming at their palm, wisps of energy flowing
into body, face showing ecstatic expression, eyes glowing
faintly, addictive pleasure visible"
```

### 最终决战场景

```
"Thousands of miners simultaneously activating absorption,
countless blue vortexes appearing, spirit energy being pulled
from the elder's body against his will, his form withering,
energy storm building, bodies beginning to swell and burst,
chaotic destruction, blinding light, total annihilation"
```
