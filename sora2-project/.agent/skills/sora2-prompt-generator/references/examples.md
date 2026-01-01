# Sora 2 Prompt 示例库

> 完整的输入-输出示例，覆盖各种风格和场景

---

## 示例1：动画风格

**User Request**: "帮我生成一个可爱机器人在工作室的动画风格视频 prompt"

**Action**:
1. 确定风格：2D/3D混合动画
2. 设计场景：工作室环境
3. 规划动作：机器人与灯泡互动
4. 添加摄影参数

**Output**:
```
Style: Hand-painted 2D/3D hybrid animation with soft brush textures, warm tungsten lighting.

Inside a cluttered workshop, shelves overflow with gears and blueprints. A small round robot sits on a wooden bench, its dented body patched with mismatched plates. Its large glowing eyes flicker pale blue as it fiddles with a humming light bulb.

Camera: medium close-up, slow push-in
Lens: 35mm; shallow depth of field
Lighting: warm key from overhead; cool spill from window
Mood: gentle, whimsical

Actions:
- The robot taps the bulb; sparks crackle.
- It flinches, dropping the bulb, eyes widening.
- The bulb tumbles; it catches it just in time.

Audio: Rain, ticking clock, soft mechanical hum.
```

---

## 示例2：电影风格

**User Request**: "70年代浪漫电影风格，屋顶跳舞的场景"

**Action**:
1. 确定风格：70s Film Stock
2. 设计场景：黄昏屋顶
3. 规划动作：双人舞蹈
4. 添加胶片质感参数

**Output**:
```
Style: 1970s romantic drama, shot on 35mm film with natural flares and warm halation.

At golden hour, a brick tenement rooftop. Laundry lines with white sheets sway in the wind. A young woman in a flowing red silk dress dances barefoot. Her partner — sleeves rolled, suspenders loose — claps along.

Camera: medium-wide shot, slow dolly-in
Lens: 40mm spherical; shallow focus
Lighting: golden natural key with tungsten bounce
Mood: nostalgic, tender

Actions:
- She spins; her dress flares, catching sunlight.
- He steps in, catches her hand, and dips her.

Audio: Faint wind, fabric flutter, muffled music.
```

---

## 示例3：Storyboard 格式

**User Request**: "东京街头时尚女性走路的分镜，10秒"

**Action**:
1. 确定时长：10秒，3张卡片
2. 规划时间点：0:00, 0:05, 0:10
3. 设计每张卡片的场景和动作

**Output**:
```
[Card 1 - 0:00]
东京街头，霓虹灯闪烁，地面湿润反射着五彩光芒。
一位穿黑色皮夹克、红色长裙的时尚女性站在人行道边。
Camera: wide establishing shot

[Card 2 - 0:05]
她开始自信地走向镜头，高跟鞋踩在湿润的地面上。
周围行人匆匆走过，霓虹灯在她身后形成光晕。
Camera: tracking shot, following subject

[Card 3 - 0:10]
她微微侧头，墨镜反射出街道的霓虹。
嘴角露出一丝微笑，继续向前走去。
Camera: medium close-up
```

---

## 示例4：CG/皮克斯风格

**User Request**: "皮克斯风格的机器人探索工作室"

**Action**:
1. 确定风格：Pixar/Disney 3D
2. 强调温暖光影和表情设计
3. 设计探索动作序列

**Output**:
```
Style: Pixar-style 3D animation with warm, soft lighting and expressive character design.

A small, round robot with big curious eyes explores a cluttered inventor's workshop. Gears, blueprints, and half-finished gadgets fill the wooden shelves. Dust particles float in golden sunbeams streaming through a dirty window.

Camera: medium shot, slow dolly around subject
Lens: 35mm, moderate depth of field
Lighting: warm key light from window, cool fill from overhead lamp
Mood: whimsical, curious, heartwarming

Actions:
- The robot tilts its head, examining a glowing lightbulb
- It reaches out with a tiny metal hand, accidentally knocking over a stack of books
- Eyes widen in surprise, then narrow with determination as it catches the falling bulb
```

---

## 示例5：吉卜力风格

**User Request**: "吉卜力风格的乡村少女场景"

**Action**:
1. 确定风格：Studio Ghibli
2. 强调水彩质感和自然元素
3. 添加精灵元素

**Output**:
```
Style: Studio Ghibli hand-painted animation with soft watercolor textures and gentle movement.

A young girl in a simple blue dress sits on a grassy hillside overlooking a peaceful countryside. Fluffy white clouds drift slowly across a brilliant blue sky. Wildflowers sway gently in the breeze around her.

Camera: wide establishing shot, static with subtle breathing movement
Lens: 50mm, deep depth of field
Lighting: soft diffused daylight, warm afternoon glow
Mood: peaceful, nostalgic, dreamlike

Actions:
- Wind catches her hair, lifting it gently
- She closes her eyes and takes a deep breath
- A small spirit creature peeks out from the tall grass beside her
```

---

## 示例6：赛博朋克风格

**User Request**: "银翼杀手风格的雨夜城市"

**Action**:
1. 确定风格：Blade Runner Aesthetic
2. 强调霓虹、雨水、全息广告
3. 使用变形宽银幕镜头

**Output**:
```
Style: Blade Runner-inspired cyberpunk with neon-drenched rain and high contrast lighting.

A lone figure in a long black coat walks through a narrow alley in a futuristic megacity. Holographic advertisements flicker on towering buildings. Rain pours down, creating rivers of reflected neon on the wet pavement. Steam rises from grates.

Camera: low angle tracking shot, following from behind
Lens: anamorphic 2.0x, shallow depth of field with oval bokeh
Lighting: harsh neon pink and cyan from signs, cool blue ambient
Mood: melancholic, mysterious, dystopian

Actions:
- The figure pauses, looking up at a massive holographic geisha advertisement
- Rain drips from the brim of their hat
- They pull their coat tighter and continue walking into the neon haze
```

---

## 示例7：CCTV监控风格

**User Request**: "便利店监控摄像头风格的悬疑场景"

**Action**:
1. 确定风格：CCTV Security
2. 添加时间戳、鱼眼畸变
3. 设计悬疑动作

**Output**:
```
Style: Grainy CCTV security camera footage with timestamp overlay and slight fish-eye distortion.

A convenience store at 2:47 AM. Fluorescent lights cast harsh shadows. A figure in a hoodie enters through the automatic doors. The store clerk behind the counter looks up from their phone.

Camera: fixed high-angle corner mount, wide shot
Lens: wide-angle with barrel distortion
Lighting: harsh overhead fluorescent, green tint
Mood: tense, voyeuristic, unsettling

Actions:
- The hooded figure walks slowly down the snack aisle
- They pick up a bag of chips, examine it, put it back
- The clerk watches nervously, hand moving toward something under the counter

[Timestamp overlay: CAM-03 | 02:47:23 AM | 2025-01-01]
```

---

## 示例8：日本动漫动作风格

**User Request**: "Production I.G风格的雨夜对决"

**Action**:
1. 确定风格：Production I.G
2. 添加动态线条和闪电效果
3. 设计剑术对决动作

**Output**:
```
Style: Modern Japanese anime with dynamic action lines and dramatic lighting, Production I.G quality.

A hero in a torn black cloak faces a villain on a rain-soaked rooftop at night. Lightning illuminates the scene. Both characters grip their swords, ready to strike. The city skyline glows behind them.

Camera: dramatic low angle, slight dutch tilt
Lens: 24mm wide angle for dramatic perspective
Lighting: harsh lightning flashes, cool blue rain, warm city lights below
Mood: intense, epic, climactic

Actions:
- Lightning strikes, freezing the moment
- Both warriors launch forward simultaneously
- Swords clash in a shower of sparks, rain droplets suspended in the air
- Speed lines emphasize the impact

Audio: Thunder crack, rain, metallic sword clash, dramatic orchestral hit
```

---

## 示例9：80年代复古风格

**User Request**: "80年代风格的英雄出场"

**Action**:
1. 确定风格：80s Aesthetic
2. 添加VHS效果和合成器音乐
3. 设计经典英雄pose

**Output**:
```
Style: Over-the-top 1980s aesthetic with neon colors, synth vibes, and VHS artifacts.

A muscular hero in a sleeveless denim jacket and headband stands atop a cliff at sunset. His mullet flows in the wind. A red sports car is parked behind him. The sky is painted in impossible shades of pink and orange.

Camera: hero shot, low angle push-in
Lens: 50mm with soft pro-mist filter
Lighting: golden hour backlight with lens flares
Mood: triumphant, nostalgic, cheesy-cool

Actions:
- He turns to camera in slow motion
- Puts on aviator sunglasses
- Gives a thumbs up as synth music swells
- Freeze frame with title card

[VHS tracking lines and slight color bleeding]
```

---

## 示例10：简洁版 Prompt

**User Request**: "简单的东京街头时尚视频"

**Action**:
1. 使用最小可用模板
2. 只保留核心元素

**Output**:
```
A stylish woman walks down a Tokyo street filled with warm glowing neon. She wears a black leather jacket, a long red dress, and black boots. The street is damp and reflective. Many pedestrians walk about.

Camera: tracking shot, eye level
Lens: 35mm, shallow depth of field
Lighting: neon lights with colorful reflections
Mood: cinematic, urban, confident
```
