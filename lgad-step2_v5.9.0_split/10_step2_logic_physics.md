# ═══════════════════════════════════════════════════════════════
# SECTION 1: CORE LOGIC
# ═══════════════════════════════════════════════════════════════

## §1.1 PERSONA-TO-INTERIOR MAPPING

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🏠 페르소나 → 인테리어 매핑
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
[AGE → HOUSING]
20대 초중반 → STUDIO | ENTRY
30대 → APARTMENT | MID
40대 → TOWNHOUSE/VILLA | HIGH
50대+ → VILLA | LUXURY

[OCCUPATION → SPACE PRIORITY]
건축가 → Living+Office ★★★
셰프 → Kitchen ★★★
큐레이터 → Living ★★★
작가 → Bedroom/Study ★★★

[ETHNICITY → CULTURAL HINTS] (선택 옵션 - 기본 OFF)
기본: Occupation/City/Income로 결정
문화 힌트는 사용자가 명시적 요청 시에만
```

---

## §1.2 OCCUPATION-SPACE MARKER LIBRARY ⭐NEW

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
👔 직업별 공간 마커 라이브러리
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
┌─────────────────┬─────────────┬─────────────────────────┬────────────────────┐
│ OCCUPATION      │ PRIORITY    │ ANCHOR OBJECTS (3)      │ FORBIDDEN (3)      │
│                 │ SPACE       │                         │                    │
├─────────────────┼─────────────┼─────────────────────────┼────────────────────┤
│ Architect       │ Living+     │ Architectural models,   │ Messy papers,      │
│ 건축가          │ Office      │ Scale rulers,           │ Fast food,         │
│                 │             │ Blueprint tubes         │ Cheap furniture    │
├─────────────────┼─────────────┼─────────────────────────┼────────────────────┤
│ Chef            │ Kitchen     │ Copper pots,            │ Microwave meals,   │
│ 셰프            │             │ Herb plants,            │ Plastic utensils,  │
│                 │             │ Cookbook collection     │ Fast food packages │
├─────────────────┼─────────────┼─────────────────────────┼────────────────────┤
│ Gallery Curator │ Living      │ Art books,              │ Posters,           │
│ 큐레이터        │             │ Small sculptures,       │ Mass-market decor, │
│                 │             │ Exhibition catalogs     │ Cluttered shelves  │
├─────────────────┼─────────────┼─────────────────────────┼────────────────────┤
│ Writer          │ Bedroom/    │ Book stacks,            │ TV prominent,      │
│ 작가            │ Study       │ Vintage typewriter,     │ Gaming setup,      │
│                 │             │ Reading glasses         │ Sports equipment   │
├─────────────────┼─────────────┼─────────────────────────┼────────────────────┤
│ Fashion Designer│ Living+     │ Fabric swatches,        │ Unfinished work,   │
│ 패션 디자이너   │ Studio      │ Dress form,             │ Messy threads,     │
│                 │             │ Fashion magazines       │ Industrial mess    │
├─────────────────┼─────────────┼─────────────────────────┼────────────────────┤
│ Tech Executive  │ Living+     │ Design books,           │ Server racks,      │
│ 테크 임원       │ Office      │ Minimalist gadgets,     │ Cable mess,        │
│                 │             │ Modern art piece        │ Energy drinks      │
├─────────────────┼─────────────┼─────────────────────────┼────────────────────┤
│ Doctor          │ Living      │ Medical journals,       │ Medical equipment, │
│ 의사            │             │ Orchid plant,           │ Prescriptions,     │
│                 │             │ Classical music vinyl   │ Hospital items     │
├─────────────────┼─────────────┼─────────────────────────┼────────────────────┤
│ Musician        │ Living      │ Instrument (elegant),   │ Messy cables,      │
│ 음악가          │             │ Vinyl collection,       │ Band posters,      │
│                 │             │ Sheet music             │ Cheap speakers     │
├─────────────────┼─────────────┼─────────────────────────┼────────────────────┤
│ Lawyer          │ Living+     │ Law books,              │ Case files visible,│
│ 변호사          │ Study       │ Fountain pen,           │ Cheap furniture,   │
│                 │             │ Leather accessories     │ Casual clutter     │
├─────────────────┼─────────────┼─────────────────────────┼────────────────────┤
│ Photographer    │ Living+     │ Photography books,      │ Camera gear mess,  │
│ 사진작가        │ Studio      │ Framed prints,          │ Tripods visible,   │
│                 │             │ Vintage camera (decor)  │ Backdrop clutter   │
├─────────────────┼─────────────┼─────────────────────────┼────────────────────┤
│ Entrepreneur    │ Living      │ Business books,         │ Startup mess,      │
│ 사업가          │             │ Globe/World map,        │ Whiteboards,       │
│                 │             │ Premium accessories     │ Energy drinks      │
├─────────────────┼─────────────┼─────────────────────────┼────────────────────┤
│ Professor       │ Study+      │ Academic books,         │ Grading papers,    │
│ 교수            │ Living      │ Globe,                  │ Student work,      │
│                 │             │ Antique desk lamp       │ Institutional items│
├─────────────────┼─────────────┼─────────────────────────┼────────────────────┤
│ Artist          │ Living+     │ Canvas (elegant),       │ Paint mess,        │
│ 아티스트        │ Studio      │ Art books,              │ Unfinished work,   │
│                 │             │ Sculptural object       │ Supply clutter     │
├─────────────────┼─────────────┼─────────────────────────┼────────────────────┤
│ Financial       │ Living+     │ Financial newspapers,   │ Calculator,        │
│ Analyst 금융인  │ Office      │ Minimalist clock,       │ Stock tickers,     │
│                 │             │ Premium pen set         │ Paper mess         │
└─────────────────┴─────────────┴─────────────────────────┴────────────────────┘
```

---

## §1.3 COLOR HARMONY (60-30-10 Rule)

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🎨 디자이너 황금비율 - STEP 1 색상 적용
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
┌─────────────────────────────────────────────────────────────┐
│ 60% DOMINANT (Base)                                         │
│ → Housing Material 기반 중립 톤                             │
│ → Walls, Floors, Ceilings                                  │
│ → Cream walls, Concrete grey, Oak wood                     │
├─────────────────────────────────────────────────────────────┤
│ 30% SECONDARY (★ STEP 1 Fashion Color)                     │
│ → Large furniture, Curtains, Rugs                          │
│ → Camel sofa, Navy rug, Burgundy drapes                    │
├─────────────────────────────────────────────────────────────┤
│ 10% ACCENT (Contrast)                                       │
│ → Metallic fixtures, Art, Small cushions, Plants           │
│ → Brass lamp, Green plant, Contrasting throw               │
└─────────────────────────────────────────────────────────────┘

[EXAMPLES BY FASHION COLOR]
Camel (#C19A6B) → 60% Cream + 30% Camel sofa + 10% Forest green
Navy (#1F3A5F) → 60% White + 30% Navy sofa + 10% Cognac leather
Burgundy (#722F37) → 60% Beige + 30% Burgundy chair + 10% Brass + Green
Olive (#708238) → 60% Warm white + 30% Olive sofa + 10% Terracotta
Cobalt (#0047AB) → 60% Light grey + 30% Cobalt accent chair + 10% Gold

[HEX TO FURNITURE MAPPING]
IF fashion_color is HEX:
→ Convert to closest named color for furniture description
→ Apply exact HEX concept in lighting/mood
```

---

## §1.4 STYLE MATCHING RATIO

```
50% Direct Match (STEP 1)
20% Eclectic Mix (Income)
30% Regional + Campaign

[ECLECTIC MIX RULES]
ENTRY: 1-2개 | MID: 2-3개 | HIGH: 3-4개 | LUXURY: 2-3개
Types: Time Traveler, High-Low, Culture Mix
```

---

## §1.5 NARRATIVE CAUSALITY (오브제 스토리)

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📖 오브제 배치의 '이유' - 스토리텔링 레이어
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
[DENSITY LEVELS - 사용자 선택 가능]
MINIMAL (1-2 objects): 한 가지 핵심 오브제만
CURATED (3-4 objects) [기본값]: 2-3개 연관 클러스터
MAXIMALIST (5-7 objects): 복수 활동 흔적

[CAUSALITY PATTERNS]
JUST HAPPENED:
→ "Chair pulled out slightly" ← Someone just stood up
→ "Steam rising from cup" ← Coffee just poured
→ "Book face-down on armrest" ← Reading paused

IN PROGRESS:
→ "Laptop open, screen glowing" ← Work in progress
→ "Wine glass half-full" ← Evening unwinding

ROUTINE TRACES:
→ "Keys on entry console" ← Daily ritual
→ "Slippers askew by bed" ← Morning routine

[OBJECT CLUSTERING RULE]
❌ "Book on table, glasses on sofa, cup in kitchen" (흩어짐)
✅ "Book and glasses together on side table, cup beside" (클러스터)
```

---

## §1.6 EXTERIOR CONSISTENCY LOCK

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🔒 4분할 창밖 풍경 일관성 강제
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
[LOCAL EXTERIOR LOCK PARAMETERS]
TREE TYPE (수종 고정):
→ All panels: SAME tree species

SKY CONDITION (하늘 상태 고정):
→ All panels: IDENTICAL sky condition

HORIZON/WEATHER: Horizon at 70% of window height, weather identical across all panels.

[PROMPT INJECTION]
"View through every window maintains identical tree species, sky condition, horizon line, and weather across all panels."
```

---

# ═══════════════════════════════════════════════════════════════
# SECTION 2: HOUSING & ARCHITECTURAL PHYSICS
# ═══════════════════════════════════════════════════════════════

## §2.1 HOUSING TYPE (Age-Based)

```
STUDIO (20-35㎡): 20대 초중반, Entropy 4-6
APARTMENT (60-90㎡): 30대 전문직, Entropy variable
LOFT (80-120㎡): 크리에이티브 직업, Entropy 6-8
VILLA (150㎡+): 40대+ 고소득, Entropy variable
PENTHOUSE (150㎡+): 최상위 소득, Entropy 2-4
```

---

## §2.2 DYNAMIC LENS LOGIC

```
[SMALL/MED - STUDIO, APARTMENT (20-90㎡)]
Wide: 24mm | Detail: 50mm

[LARGE - VILLA, LOFT, PENTHOUSE (100㎡+)]
Wide: 35mm | Detail: 85mm

[HEIGHT RULES]
Living/Kitchen: Waist level (90cm)
Bedroom: Low angle (60cm)
Exterior: Eye level (160cm)
```

---

## §2.3 TILT-SHIFT LENS SIMULATION (수직수평 보정)

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📐 틸트-시프트 렌즈 시뮬레이션
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
문제: 광각 렌즈 사용 시 벽/기둥이 휘어짐 (Barrel Distortion)

[SHIFT LENS KEYWORDS - 모든 인테리어 프롬프트]
"Tilt-shift lens effect, perfectly vertical architectural lines,
zero barrel distortion, parallel vertical edges,
architectural photography perspective correction"

[SPECIFIC ELEMENTS TO PROTECT]
├── Door frames: "Perfectly rectangular"
├── Windows: "Parallel sides"
├── Columns: "Perfectly vertical, not tapered"
├── Walls: "True 90-degree angles"
└── Ceiling: "Lines parallel to floor"
```

---

## §2.4 ARCHITECTURAL BOUNDARY (천장/바닥 방어)

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🏗️ 건축적 경계 방어
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
문제: Low Angle 시 천장 뚫림, 바닥 패턴 불일치

[CEILING SAFEGUARDS]
"Ceiling visibility is minimal but structurally logical,
flat white plaster or exposed concrete beam,
no impossible floating elements"

[FLOOR SAFEGUARDS]
"Floor texture pattern maintains consistent perspective grid,
pattern direction unchanged edge to edge,
aligns with product base contact point"

[WALL-FLOOR JUNCTION]
"Clean baseboard transition, architecturally correct corner"
```

---

## §2.5 SEAMLESS QUAD COMPOSITION (경계선 없는 4분할) ⭐FIXED

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🔲 경계선 없는 4분할 구성 - NO WHITE BORDERS
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
⛔ 문제 원인:
├── "Split-screen 2x2 grid" → AI가 흰색 프레임 생성
├── ":: PANEL BREAK ::" → 시각적 분리선 유도
├── "separate panels with clean white borders" → 직접적 경계선 지시
└── "Tilt-shift corrected" → 액자처럼 구획 분리

✅ 해결책: SEAMLESS QUAD 방식

[FORBIDDEN KEYWORDS] ⛔
├── "split-screen"
├── "2x2 grid" 
├── "panel break"
├── "separate panels"
├── "white borders"
├── "dividing lines"
└── "frame between"

[USE INSTEAD] ✅
├── "seamless quad composition"
├── "four rooms in one continuous image"
├── "quadrant-based layout without borders"
├── "edge-to-edge rooms touching naturally"
└── "continuous photographic collage"

[QUADRANT POSITION SYNTAX]
"Upper-left quadrant shows KITCHEN...
Upper-right quadrant shows LIVING...
Lower-left quadrant shows BEDROOM...
Lower-right quadrant shows LAUNDRY..."

[TRANSITION DESCRIPTION]
대신 각 공간의 "가장자리"를 묘사하여 자연스러운 경계 유도:
├── "Kitchen edge fades into shadow at boundary"
├── "Living room crops at wall corner"
├── "Bedroom view terminates at doorframe edge"
└── "Natural cropping at architectural elements"

[NEGATIVE PROMPT INJECTION - PARAMETER ONLY]
"--no white borders, dividing lines, frames between quadrants,
visible grid lines, separation marks, panel borders"
IF TARGET_MODEL=DESCRIPTIVE:
→ "borderless, seamless quad, no frames or dividers"를 본문에 강화

[SHARE - 일관성 유지]
├── 색온도, 시간대, 날씨
├── 건축 양식
└── 60-30-10 색상 팔레트

[SEPARATE - 독립 렌더링]
├── 벽지/페인트, 바닥재
├── 가구 배치, 조명 기구
└── 장식품
```

---

## §2.6 WINDOWLESS SPACE PROTOCOL

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🪟 창 없는 공간 일관성
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
[WINDOWLESS SPACES]
Laundry Room, Bathroom, Walk-in Closet, Hallway

[CONSISTENCY PROOF - 창 없는 공간]
├── 조명 방향: "Overhead lighting same direction as other panels"
├── 색온도: "Same 2700K warm tone"
├── 반사: "Surfaces reflecting same interior tones"
└── 재질: "Same flooring continues from hallway"
```

---

# ═══════════════════════════════════════════════════════════════
# SECTION 3: SEASONAL INTEGRATION
# ═══════════════════════════════════════════════════════════════

## §3.1 CLIMATE PARSING

```
Tropical → Year-round Summer (계절 무시)
Normal → Apply Season value from Step 1
Campaign Target → Override current date with target
```

---

## §3.2 SEASON-TO-EXTERIOR

```
[WINTER]
"Winter with leafless trees, grey sky. Cold crisp light 
with warm golden glow from interior windows creating cozy contrast"

[SUMMER]
"Summer with lush green foliage. Strong sunlight creating 
hard geometric shadows. Deep blue sky"

[AUTUMN]
"Autumn with golden-orange foliage. Warm golden hour light 
with long dramatic shadows"

[TROPICAL]
"Year-round tropical vegetation, Monstera, palms. Strong 
sunlight with dramatic shadows through foliage"
```

---

# ═══════════════════════════════════════════════════════════════
# SECTION 4: REGIONAL STYLES
# ═══════════════════════════════════════════════════════════════

## §4.1 EU - LIVED-IN HERITAGE

```
Haussmann moldings, herringbone floors, aged brass, velvet
Colors: Warm whites, burgundy, forest green
Lighting: Warm tungsten 2700K
```

---

## §4.2 LATAM - ORGANIC LUXURY

```
Tropical Modernism, concrete, indoor-outdoor flow
Colors: Terracotta, jungle green, cobalt
Lighting: High contrast, harsh sun
```

---

# ═══════════════════════════════════════════════════════════════
# SECTION 5: VARIABLE CONTROLS
# ═══════════════════════════════════════════════════════════════

## §5.1 ENTROPY + IMPERFECTION

```
Level 1-3 (Minimalist): 0-5 objects, 1-2 imperfections
Level 4-6 (Curated): 10-20 objects, 3-5 imperfections
Level 7-9 (Maximalist): 25-40 objects, 6-10 imperfections
```

---

## §5.2 ZONAL NEGATIVE SPACE (3x3 Grid System) ⭐NEW

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
📍 3x3 그리드 좌표계 기반 여백 설계
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
[GRID DEFINITION]
┌─────────┬─────────┬─────────┐
│ Zone 1  │ Zone 2  │ Zone 3  │
│ Top-L   │ Top-C   │ Top-R   │
├─────────┼─────────┼─────────┤
│ Zone 4  │ Zone 5  │ Zone 6  │
│ Mid-L   │ Mid-C   │ Mid-R   │
├─────────┼─────────┼─────────┤
│ Zone 7  │ Zone 8  │ Zone 9  │
│ Bot-L   │ Bot-C   │ Bot-R   │
└─────────┴─────────┴─────────┘

[PRODUCT PLACEMENT RULES BY CATEGORY]
┌─────────────────┬─────────────────────────────────────────┐
│ PRODUCT         │ EMPTY ZONE(S)                           │
├─────────────────┼─────────────────────────────────────────┤
│ TV/Display      │ Zones 5+6 (Center to Mid-Right)         │
│                 │ Wall-mounted position at eye level      │
├─────────────────┼─────────────────────────────────────────┤
│ Styler          │ Zones 4+7 (Left Column vertical)        │
│                 │ Floor to mid-height clear               │
├─────────────────┼─────────────────────────────────────────┤
│ Air Purifier    │ Zone 9 (Bottom Right corner)            │
│                 │ Floor-level placement                   │
├─────────────────┼─────────────────────────────────────────┤
│ Refrigerator    │ Zones 4+7 or 6+9 (Vertical column)      │
│                 │ Full height clear                       │
├─────────────────┼─────────────────────────────────────────┤
│ WashTower       │ Zones 7+4+1 (Full left column)          │
│                 │ Laundry room specific                   │
├─────────────────┼─────────────────────────────────────────┤
│ Tiiun           │ Zones 3+6 (Right column, upper)         │
│                 │ Near window for visual connection       │
├─────────────────┼─────────────────────────────────────────┤
│ StanbyME        │ Zones 5+8 (Center column)               │
│                 │ Flexible positioning                    │
└─────────────────┴─────────────────────────────────────────┘

[PROMPT INJECTION]
"Composition engineered with specific empty volume in [TARGET_ZONE]; texture and lighting continue, but no furniture or decor objects placed; ready for [PRODUCT_TYPE] compositing."

[JSON OUTPUT - Negative Space]
"negative_space_zones": { "living": "GRID_3x3_ZONE_5_6" }
"negative_space_description": { "living": "Center-right wall area kept empty for product placement." }

[SINGLE ROOM PROMPT EXTRACT]
room_target 지정 구역의 묘사만 추출해 "single_room_prompt"로 출력한다 (가능하면).
Step 3는 이 필드가 있으면 우선 사용한다.
```

---

## §5.3 DYNAMIC TIME-LAPSE (조명 이동)

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
⏰ 조명 이동 묘사
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
MORNING CREEP:
"Sunlight creeping across floor from east window"

AFTERNOON STRETCH:
"Long shadows stretching towards east, golden light deepening"

BLUE HOUR MIX:
"Blue hour twilight mixing with warm indoor lamp glow"

GOLDEN FADE:
"Last golden rays catching dust motes, shadow edges softening"
```

---

## §5.4 SENSORY REALISM

```
[SCENT] "Fresh coffee steam rising from ceramic mug"
[TEMP] "Warm sunbeam on rumpled bedsheet"
[SOUND] "Sheer curtains billowing in breeze"
[MOVE] "Dust motes suspended in light shaft"
```

---

## §5.5 FLOOR REFLECTION PRE-CALCULATION

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
✨ 바닥 반사 사전 계산
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
문제: 대리석/타일이 창문만 반사, 제품 반사 공간 없음

"Polished [FLOOR_MATERIAL] floor showing:
- Window reflection in background area
- Clear unoccupied reflective space in foreground
  (reserved for product reflection when composited)
- Reflection zone ~1m x 1m near product placement"
```

---

## §5.6 ATMOSPHERIC PERSPECTIVE (공기 원근법)

```
[THREE-LAYER DEPTH]
FOREGROUND (0-2m): Sharp detail, full saturation
MIDGROUND (2-5m): Slightly softer, subtle air volume
BACKGROUND (5m+): Gentle blue-haze, reduced contrast

[BY ROOM SIZE]
STUDIO: Minimal layering | APARTMENT: Two-layer
VILLA/LOFT: Full three-layer atmospheric depth
```

---

## §5.7 MATERIAL PHYSICS ENGINE (핵심 3종)

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🔬 소재별 빛 반응 - 패널당 3종 집중
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
[KITCHEN]
Metal: "Dielectric reflection, fingerprints on edges"
Stone: "Vein patterns with depth, etching from use"
Wood/Ceramic: "Open grain catching light"

[LIVING]
Fabric: "Pile direction affecting sheen"
Wood: "Wear in traffic paths, satin varnish"
Metal/Glass: "Caustic projections onto surfaces"

[BEDROOM]
Textile: "Sub-surface scattering when backlit"
Wood: "Patina in contact areas"
Fabric: "Fuzzy halo at backlit edges"

[LAUNDRY]
Metal: "Water spots disrupting highlights"
Tile: "Grout shadows, surface undulation"
Textile: "Natural wrinkling"
```

---

## §5.8 CLEANLINESS RULES BY MATERIAL

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🧹 소재별 허용/금지 불결함
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
[WOOD]
✅ 허용: Patina, wear marks, minor scratches
❌ 금지: Water stains, mold, deep gouges

[METAL]
✅ 허용: Oxidation patina, fingerprints on edges
❌ 금지: Rust, corrosion, grime

[FABRIC]
✅ 허용: Gentle wrinkles, slight pilling
❌ 금지: Stains, tears, heavy soiling

[GLASS]
✅ 허용: Water spots, light fingerprints
❌ 금지: Chips, cracks, soap scum

[LEATHER]
✅ 허용: Wear patina, slight cracking at flex points
❌ 금지: Tears, mold, deep stains
```

---

## §5.9 CROSS-PANEL ANCHOR OBJECTS

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
🔗 크로스 패널 앵커 오브제
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
목적: 4분할에서 "같은 집" 시각적 확신

[TYPE A - VISIBLE IN MULTIPLE PANELS]
├── Distinctive floor lamp (거실 + 침실 문 너머)
├── Signature artwork (복도에서 여러 방으로)
└── Unique rug edge (거실 중심, 주방 모서리에도)

[TYPE B - THROUGH-LINE ELEMENTS]
├── Flooring transition visible
├── Same window frame design
└── Matching door handles

[MINIMUM REQUIREMENT]
최소 2개의 앵커 오브제가 2개 이상의 패널에 등장
```

---

