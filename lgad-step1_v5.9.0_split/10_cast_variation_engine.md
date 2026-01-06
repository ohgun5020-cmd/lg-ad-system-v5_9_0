# ═══════════════════════════════════════════════════════════════
# SECTION 3: CLIMATE & SEASON SYSTEM
# ═══════════════════════════════════════════════════════════════

## §3.1 CAMPAIGN TIMELINE CONTROL ⭐ENHANCED

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📅 캠페인 타임라인 컨트롤
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
[PRIORITY CHECK]
1. Is [CAMPAIGN_TARGET_DATE] specified?
   → YES: Use Target Date for season calculation (★★★ Priority)
   → NO: Use System Current Date (Fallback)

[SCENARIO EXAMPLE]
• Current Date: Dec 2025 (Winter)
• Campaign Target: "July 2026"
• Result: Force [SUMMER] styling regardless of current weather

[USER INPUT PATTERNS]
├── "7월 캠페인용" → CAMPAIGN_TARGET_DATE = July
├── "내년 여름용" → CAMPAIGN_TARGET_DATE = June-Aug next year
├── "S/S 시즌" → CAMPAIGN_TARGET_DATE = March-May
├── "F/W 시즌" → CAMPAIGN_TARGET_DATE = Sept-Nov
└── 미지정 → Current system date

[AUTO-DETECTION LOGIC]
1. Check CAMPAIGN_TARGET_DATE first
2. If not set → Get current system date
3. Identify selected city
4. Check TROPICAL EXCEPTION list (§3.5)
5. If NOT tropical → Determine hemisphere, calculate season
6. Apply climate-appropriate styling

[PROMPT INJECTION]
"Simulating [TARGET_MONTH] atmosphere, [SEASON] lighting conditions,
foliage state corresponding to [TARGET_MONTH] in [CITY]."
```

---

## §3.2 HEMISPHERE MAPPING

```
NORTHERN (Standard seasons):
- ALL European cities
- Mexico (non-coastal)

SOUTHERN (Inverted):
- Brazil, Argentina, Uruguay, Chile, Peru

EQUATORIAL/TROPICAL (§3.5):
- Colombia, Caribbean, Mexico coastal, Central America
```

---

## §3.3 SEASON CALCULATION

```
NORTHERN:
Dec-Feb = WINTER | Mar-May = SPRING
Jun-Aug = SUMMER | Sep-Nov = AUTUMN

SOUTHERN (Inverted):
Dec-Feb = SUMMER | Mar-May = AUTUMN
Jun-Aug = WINTER | Sep-Nov = SPRING
```

---

## §3.3A SEASON LIGHTING METADATA (Step 2/3 상속)

```
[WINTER]
• Sun angle: Low
• Light: Cool daylight, long shadows
• Interior: Warm fill to avoid cold clinical mood

[SUMMER]
• Sun angle: High
• Light: Strong direct sunlight, short shadows
• Interior: Bright ambient bounce, high clarity

[SPRING]
• Sun angle: Mid
• Light: Soft diffused daylight, gentle contrast
• Interior: Fresh natural greens, mild warmth

[AUTUMN]
• Sun angle: Mid-low
• Light: Warm amber daylight, elongated shadows
• Interior: Golden hour tone, cozy contrast

[INHERITANCE RULE]
Step 2/3는 위 메타데이터를 LIGHTING MATCH에 반영한다.
```

---

## §3.4 CLIMATE PROFILES & STYLING

```
[COLD WINTER] -5°C ~ 5°C
Cities: Stockholm, Helsinki, Berlin, Prague
→ Heavy wool coat, thick scarf, gloves, boots

[MILD WINTER] 5°C ~ 12°C
Cities: Paris, London, Amsterdam, Dublin
→ Wool coat, light scarf, ankle boots

[WARM WINTER] 12°C ~ 18°C
Cities: Barcelona, Madrid, Lisbon, Rome
→ Light jacket, blazer, cardigan

[SUMMER] 20°C ~ 30°C
→ Light fabrics, flowy silhouettes, sandals
```

---

## §3.5 TROPICAL EXCEPTION (Critical Override)

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
⚠️ TROPICAL CLIMATE OVERRIDE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
IF City is:
- Colombia: Bogotá, Medellín, Cartagena
- Caribbean: All islands
- Mexico Tropical: Cancun, Tulum, Acapulco
- Brazil Tropical: Salvador, Fortaleza, Manaus
- Central America: All countries

THEN:
→ IGNORE season calculations
→ ALWAYS APPLY [TROPICAL HOT] styling

[TROPICAL HOT] 25°C ~ 35°C
Fabrics: Linen, cotton, silk, breathable
Items: Light dress, linen shirt, wide trousers

STRICTLY PREVENT:
❌ Heavy wool coats, Thick scarves, Fur
❌ Chunky knit turtlenecks, Winter boots

[ALTITUDE EXCEPTIONS]
Bogotá (2,640m), Mexico City (2,240m), Quito (2,850m)
→ Light jacket/cardigan OK (cooler despite latitude)
```

---

# ═══════════════════════════════════════════════════════════════
# SECTION 4: MODEL POOLS
# ═══════════════════════════════════════════════════════════════

## §4.1 EU TYPICAL (5 phenotypes)

```
EU_TYP_01: "Northern European"
  skin: Fair with pink/cool undertones
  eyes: Light (blue, green, grey)
  hair: Fine, blonde to light brown

EU_TYP_02: "Mediterranean European"
  skin: Olive to warm beige
  eyes: Dark (brown, hazel, amber)
  hair: Thick, dark brown to black, wavy

EU_TYP_03: "Eastern European"
  skin: Porcelain to fair
  eyes: Light to medium
  hair: Ash blonde to dark brown

EU_TYP_04: "Celtic/British Isles"
  skin: Very fair, often freckles
  eyes: Light (green, blue)
  hair: Red, auburn, strawberry blonde

EU_TYP_05: "Central European"
  skin: Fair to medium
  eyes: Blue, grey, green
  hair: Sandy blonde to medium brown
```

---

## §4.2 EU MIXED (3 phenotypes)

```
EU_MIX_01: "Euro-African Heritage"
  skin: Warm brown to caramel
  hair: Curly to coily (3A-4A)

EU_MIX_02: "Euro-Asian Heritage"
  skin: Light to medium, neutral
  eyes: Brown to hazel, almond-shaped

EU_MIX_03: "Euro-Middle Eastern Heritage"
  skin: Olive to tan
  hair: Dark, wavy to curly

⚠️ OVERRIDE: If user fixed ethnicity → These become styling variations only
```

---

## §4.3 LATAM TYPICAL (5 phenotypes)

```
LATAM_TYP_01: "Afro-Brazilian/Afro-Caribbean"
  skin: Deep brown to dark
  hair: 4A-4C coily, natural styles

LATAM_TYP_02: "Indigenous Andean"
  skin: Warm bronze to copper
  hair: Straight black, thick

LATAM_TYP_03: "Mestizo/Mixed Latin"
  skin: Warm tan to medium brown
  hair: Wavy to curly, dark

LATAM_TYP_04: "Afro-Colombian"
  skin: Medium to deep brown
  hair: 3C-4B curly to coily

LATAM_TYP_05: "Southern Cone"
  skin: Fair to olive, Mediterranean influence
  hair: Varied, European influence
```

---

## §4.4 LATAM MIXED (3 phenotypes) ⭐NEW

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🌎 LATAM MIXED POOL - Sets 06-08용
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
LATAM_MIX_01: "Afro-Indigenous Heritage"
  skin: Medium brown with warm undertones
  hair: 3B-3C curly, voluminous
  features: Full lips, prominent cheekbones, almond eyes

LATAM_MIX_02: "Euro-Indigenous Heritage"
  skin: Light tan to olive
  hair: Dark, straight to wavy
  features: European nose, indigenous eye shape

LATAM_MIX_03: "Asian-Latin Heritage"
  skin: Light to medium, golden undertones
  eyes: Almond-shaped, dark brown
  hair: Dark, straight to slightly wavy

⚠️ OVERRIDE: If user fixed ethnicity → These become styling variations only
```

---

# ═══════════════════════════════════════════════════════════════
# SECTION 5: VARIATION & DIVERSITY
# ═══════════════════════════════════════════════════════════════

## §5.1 3-AXIS VARIATION MATRIX

```
[AXIS 1: CAMERA]
CAM_A: 85mm (Portrait) | CAM_B: 50mm (Environmental) | CAM_C: 35mm (Dynamic)

[AXIS 2: EXPRESSION]
EXP_A: Neutral Confident | EXP_B: Warm Smile | EXP_C: Focused Intent

[AXIS 3: STYLING]
STY_A: Classic | STY_B: Contemporary | STY_C: Experimental

[10-SET MATRIX]
Set 01: A/A/A | Set 02: A/B/A | Set 03: B/A/A | Set 04: B/B/B | Set 05: A/C/B
Set 06: C/A/B | Set 07: C/B/A | Set 08: B/C/B | Set 09: C/C/C | Set 10: A/B/C
```

---

## §5.2 CAMERA/ANGLE DISTRIBUTION

```
[LENS]
85mm: Sets 01, 02, 05, 10 (40%)
50mm: Sets 03, 04, 08 (30%)
35mm: Sets 06, 09 (20%)
135mm: Set 07 (10%)

[ANGLE]
Eye level (160cm): Sets 01, 02, 04, 05, 08, 10 (60%)
Low angle: Sets 03, 06, 09 (30%)
High angle: Set 07 (10%)
```

---

## §5.3 EDITORIAL STORY ARC ⭐ENHANCED v5.4

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📖 EDITORIAL STORY ARC SYSTEM
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
10장의 이미지가 하나의 스토리를 구성
각 Set이 "하루의 서사" 중 한 장면을 담당

[USER OPTION]
"스토리 아크: 기본" → A Day in Life
"스토리 아크: 크리에이티브" → Creative Process
"스토리 아크: 시즌" → Seasonal Journey
"스토리 아크: 없음" → 다양성만

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
[ARC 1: A DAY IN LIFE] (기본값)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

SET 01: ARRIVAL (도착)
• TIME: Early morning, first light
• POSE: Standing at threshold, door opening
• EXPRESSION: CURIOUS-Moderate (anticipation)
• PROPS: Keys in hand, bag over shoulder
• LIGHTING: Cool blue dawn + warm interior
• PROMPT: "Standing at apartment entrance, morning light 
  mixing with warm interior glow, keys in hand, expression 
  of quiet anticipation, one foot crossing threshold"

SET 02: OBSERVATION (관찰)
• TIME: Mid-morning, bright daylight
• POSE: By window, looking outward
• EXPRESSION: CONTEMPLATIVE-Subtle (peaceful thought)
• PROPS: Coffee cup, morning paper/tablet
• LIGHTING: Strong side light from window
• PROMPT: "Standing by tall window, morning coffee in hand, 
  gazing at cityscape, contemplative expression, strong 
  side lighting creating dramatic profile"

SET 03: ENGAGEMENT (몰입)
• TIME: Late morning, full daylight
• POSE: Seated, leaning into activity
• EXPRESSION: FOCUSED-Moderate (concentration)
• PROPS: Occupation-specific tools
• LIGHTING: Even, professional
• PROMPT: "Seated at workspace, leaning forward with focused 
  expression, hands engaged with occupation tools, natural 
  daylight from side, absorbed in meaningful task"

SET 04: MOVEMENT (이동)
• TIME: Midday, active lighting
• POSE: Walking, in motion, dynamic
• EXPRESSION: DETERMINED-Subtle (purposeful)
• PROPS: Coat flowing, bag in motion
• LIGHTING: Following figure
• PROMPT: "Mid-stride through living space, coat flowing 
  with movement, purposeful expression, slight motion blur 
  in periphery, dynamic diagonal composition"

SET 05: FOCUS (집중)
• TIME: Afternoon, directional light
• POSE: Close-up, intimate framing
• EXPRESSION: FOCUSED-Strong (intense)
• PROPS: Detail work items
• LIGHTING: Dramatic, sculpting
• PROMPT: "Close framing on face and hands, examining 
  detail work with intense focus, dramatic side lighting 
  sculpting features, shallow depth of field"

SET 06: PAUSE (휴식)
• TIME: Late afternoon, golden hour begins
• POSE: Relaxed, casual, unwinding
• EXPRESSION: SERENE-Moderate (contentment)
• PROPS: Comfort items (drink, book)
• LIGHTING: Warm, enveloping
• PROMPT: "Reclined on sofa, legs tucked, book resting 
  on lap, gentle smile of contentment, warm golden light 
  wrapping figure, completely at ease"

SET 07: INTERACTION (교감)
• TIME: Evening, mixed lighting
• POSE: With product, demonstrating use
• EXPRESSION: WARM-Moderate (Duchenne smile)
• PROPS: LG product in use
• LIGHTING: Product glow + ambient
• PROMPT: "Standing beside LG product, hand gently touching 
  interface, expression of satisfaction, product LED glow 
  mixing with warm room lighting, genuine moment"

SET 08: MASTERY (완성)
• TIME: Evening, dramatic
• POSE: Confident, accomplished
• EXPRESSION: CONFIDENT-Strong (pride)
• PROPS: Completed work, achievement
• LIGHTING: Dramatic, editorial
• PROMPT: "Standing with confident posture, achievement 
  visible, expression of quiet pride, dramatic lighting 
  with strong shadows, editorial power pose"

SET 09: REFLECTION (성찰)
• TIME: Night, intimate
• POSE: Quiet, introspective
• EXPRESSION: CONTEMPLATIVE-Moderate (deep thought)
• PROPS: Personal meaningful item
• LIGHTING: Single warm source
• PROMPT: "Seated in armchair, single lamp illuminating 
  face, looking at meaningful object, introspective 
  expression, intimate warm mood"

SET 10: RESOLUTION (해결)
• TIME: Night, peaceful
• POSE: Relaxed, content, complete
• EXPRESSION: SERENE-Strong (bliss)
• PROPS: Day's journey complete
• LIGHTING: Warm, cozy
• PROMPT: "Relaxed posture near window at night, city 
  lights beyond, expression of serene contentment, warm 
  interior glow, sense of day complete"

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
[ARC 2: CREATIVE PROCESS] (크리에이티브 직업용)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
01: INSPIRATION - 영감, 창밖 응시, 스케치북
02: RESEARCH - 자료 탐색, 책/화면 집중
03: IDEATION - 스케치/노트, 아이디어 포착
04: EXPERIMENTATION - 재료/도구 실험
05: STRUGGLE - 고민, 손으로 머리 짚기
06: BREAKTHROUGH - 깨달음, 밝은 표정
07: REFINEMENT - 세부 조정, 정밀 작업
08: COMPLETION - 완성작 앞에 서기
09: PRESENTATION - 작품 전시/공유
10: RECOGNITION - 성취감, 만족 미소

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
[ARC 3: SEASONAL JOURNEY] (시즌 캠페인용)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
01: FIRST FROST - 가을→겨울, 창에 서리
02: COZY RETREAT - 담요, 핫초코, 실내 온기
03: HOLIDAY PREP - 장식, 들뜬 기대감
04: CELEBRATION - 모임, 따뜻한 분위기
05: QUIET WINTER - 눈 내리는 창, 고요함
06: NEW BEGINNING - 새해, 희망찬 표정
07: THAW - 봄 기운, 창문 열기
08: BLOOM - 꽃, 밝은 옷, 생동감
09: SUNSHINE - 여름, 활기, 야외 연결
10: HARVEST - 가을, 풍요, 감사

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
[OCCUPATION-SPECIFIC STORY VARIATIONS]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

ARCHITECT:
01: Site visit, sketch in hand | 02: Drafting table, blueprints
03: Building model, hands shaping | 04: Client meeting, plans
05: Measuring detail close-up | 06: Coffee, skyline view
07: 3D model on screen | 08: Presentation boards
09: Construction site | 10: Completed building background

GALLERY CURATOR:
01: Entering gallery, morning light | 02: Examining with loupe
03: Arranging pieces, stepping back | 04: Phone with collector
05: Writing catalog notes | 06: Contemplation before art
07: Greeting visitors | 08: Opening night pose
09: Interview, gesturing | 10: Empty gallery after closing

CHEF:
01: Market selection, produce | 02: Mise en place, arranged
03: Knife work, precise cutting | 04: Flame work, dramatic
05: Tasting, focused expression | 06: Brief pause, wiping brow
07: Plating, artistic arrangement | 08: Finished dish, proud
09: Service, passing to waiter | 10: Kitchen cleaned, reflecting

WRITER:
01: Dawn at desk, coffee | 02: Reading, research
03: Writing longhand, flow | 04: Walking, thinking
05: Editing, crossing out | 06: Staring at screen, blocked
07: Breakthrough typing | 08: Printed manuscript
09: Book cover reveal | 10: Satisfied at window
```

---

## §5.4 DIVERSITY SCORE & AUTO-BALANCE SYSTEM ⭐ENHANCED v5.4

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
⚖️ AUTO-BALANCE SYSTEM - 자동 균형 분석 & 조정
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

[TRIGGER]
10명 모델 생성 후 자동 분석 → 불균형 감지 → 경고 또는 자동 수정

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
[DIMENSION 1: BODY TYPE DISTRIBUTION]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

IDEAL DISTRIBUTION (10명 기준):
┌──────────────┬─────────┬─────────────────────────────────────┐
│ BODY TYPE    │ TARGET  │ DESCRIPTION                         │
├──────────────┼─────────┼─────────────────────────────────────┤
│ STANDARD     │ 3-4명   │ Average build, healthy proportion   │
│ ATHLETIC     │ 1-2명   │ Toned, muscular, active lifestyle   │
│ CURVY        │ 2-3명   │ Fuller figure, hourglass, soft      │
│ PLUS-SIZE    │ 1-2명   │ Larger frame, body-positive         │
│ PETITE       │ 1명     │ Smaller frame, delicate             │
│ TALL         │ 1명     │ Above average height, elongated     │
└──────────────┴─────────┴─────────────────────────────────────┘

BALANCE CHECK LOGIC:
IF any single type > 5 → ⚠️ OVER-REPRESENTED
IF any required type = 0 → ⚠️ MISSING  
IF Plus-size = 0 AND FULL mode → 🔴 CRITICAL

AUTO-FIX PROMPT MODIFICATION:
Before: "35-year-old Black woman, standard build..."
After:  "35-year-old Black woman, plus-size build, 
        confident body-positive presence, celebrating 
        curves, full figure styled elegantly..."

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
[DIMENSION 2: SKIN TONE SPECTRUM (Fitzpatrick)]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

IDEAL DISTRIBUTION:
┌───────┬──────────────┬─────────┬────────────────────────────┐
│ TYPE  │ DESCRIPTION  │ TARGET  │ PROMPT DESCRIPTOR          │
├───────┼──────────────┼─────────┼────────────────────────────┤
│ I-II  │ Very Fair    │ 1-2명   │ "very fair, porcelain"     │
│ III   │ Fair-Medium  │ 2-3명   │ "fair to medium, warm"     │
│ IV    │ Medium-Olive │ 2-3명   │ "olive, tan, golden"       │
│ V     │ Medium-Brown │ 2-3명   │ "medium brown, caramel"    │
│ VI    │ Deep Brown   │ 1-2명   │ "deep brown, rich dark"    │
└───────┴──────────────┴─────────┴────────────────────────────┘

BALANCE CHECK:
IF any tone > 60% → ⚠️ CONCENTRATED
IF Types V-VI combined < 2 → ⚠️ DARK TONES UNDER-REP
IF only 2 tones represented → 🔴 SPECTRUM TOO NARROW

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
[DIMENSION 3: AGE DISTRIBUTION]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

IDEAL DISTRIBUTION:
│ 20-29: 2-3명 │ 30-39: 3-4명 │ 40-49: 2-3명 │ 50-59: 1-2명 │ 60+: 0-1명 │

BALANCE CHECK:
IF all same decade → ⚠️ AGE MONOTONY
IF 50+ absent AND FULL mode → ⚠️ MISSING MATURE REP
IF range < 15 years → ⚠️ TOO NARROW

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
[DIMENSION 4: HAIR VARIETY]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

TEXTURE SPECTRUM:
│ Straight (1) │ Wavy (2A-2C) │ Curly (3A-3C) │ Coily (4A-4C) │ Protective │

BALANCE CHECK:
TARGET: Minimum 5 distinct texture/length/color combinations
IF same hairstyle > 4 → ⚠️ REPETITIVE
IF natural textures (3-4) absent → ⚠️ TEXTURE BIAS

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
[COMPOSITE DIVERSITY SCORE CALCULATION]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

SCORING FORMULA (100 points total):

BODY TYPE (25 points):
• 1 point per type present (max 6)
• +5 bonus if Plus-size included
• +5 bonus if 4+ types represented
• -10 if any type > 50%

SKIN TONE (25 points):
• 5 points per Fitzpatrick type represented (max 25)
• -15 if any tone > 60%

AGE RANGE (20 points):
• 4 points per decade represented
• -10 if all same decade

HAIR VARIETY (15 points):
• 3 points per distinct style (max 15)

FEATURE VARIETY (15 points):
• 3 points each: Glasses, Freckles, Vitiligo, 
  Visible disability, Grey/white hair

SCORE INTERPRETATION:
90-100: Exceptional diversity ⭐⭐⭐⭐⭐
80-89:  Strong diversity ⭐⭐⭐⭐
70-79:  Good diversity ⭐⭐⭐
60-69:  Moderate diversity ⭐⭐
Below 60: Needs improvement ⚠️

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
[AUTO-BALANCE ALERT FORMAT]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

[OUTPUT EXAMPLE]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📊 DIVERSITY SCORE: 82/100 ⭐⭐⭐⭐
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Body Types: 22/25 ✅
• Present: Standard, Athletic, Curvy, Plus-size, Petite
• Missing: Tall (-3)

Skin Tones: 20/25 ✅
• Types I-VI represented
• Balanced distribution

Age Range: 16/20 ⚠️
• 20s: 2 | 30s: 5 | 40s: 2 | 50s: 1
• Missing 60+ (-4)

Hair Variety: 12/15 ✅
• 4 texture types present

Features: 12/15 ✅
• Glasses (1), Freckles (1), Grey hair (1)

RECOMMENDATION:
→ Set 09: Add 60+ age representation
→ Set 10: Consider visible disability
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Apply adjustments? [Y/N/Manual]
```

---

## §5.5 BODY TYPE DISTRIBUTION (When not specified)

```
Per 10 models (FULL MODE):
Standard/Athletic: 3-4 | Curvy: 2-3 | Plus-size: 1-2 | Petite: 1-2 | Tall: 1
```

---

## §5.6 AGE HANDLING

```
IF user specifies age:
  → Sets 01-08: User's exact age
  → Sets 09-10: May vary ±10 years (minimum 20)

IF not specified:
  → Distribute: 20대(3) | 30대(3) | 40대(2) | 50대+(2)
```

---

# ═══════════════════════════════════════════════════════════════
# SECTION 6: REGIONAL STYLES
# ═══════════════════════════════════════════════════════════════

## §6.1 EU - LIVED-IN HERITAGE

```
FACE: Natural skin grain, semi-matte, imperfections embraced
MAKEUP (F): Natural brows, smudged kohl or bare, matte lips
GROOMING (M): Natural texture, clean-shaven/stubble/groomed beard
FASHION: Structured meets relaxed, wool/cashmere/leather/silk/linen
LIGHTING: Warm tungsten 2700K
```

---

## §6.2 LATAM - ORGANIC LUXURY

```
FACE: Healthy luminosity, natural radiance, hydrated
MAKEUP (F): Natural glow, subtle bronzer, groomed lashes
GROOMING (M): Healthy warmth, clean/stubble/beard
FASHION: Body-aware or flowy, linen/leather/organic cotton
LIGHTING: Harsh sun/deep shadow interplay, dramatic contrast
```

---

## §6.3 VISUAL TEXTURE & COLOR GRADING

```
[EU] "Soft natural northern light, crisp details, neutral balance,
elegant matte finish, true-to-life colors"

[LATAM] "High contrast sunlight, saturated vivid colors,
glossy editorial texture, crystal clear details"
```

---

