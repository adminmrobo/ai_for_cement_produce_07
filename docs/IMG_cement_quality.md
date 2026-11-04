# 「시멘트 품질, AI로 미리 본다」 이미지 제작 명세서

| 항목 | 내용 |
|---|---|
| 페이지 | cement_quality.html |
| 모드 / 주 앵커 | 교과서 / D 생활·현장: 시멘트 공장 품질실 (보조 B 연구실: 봉인한 시험지) |
| 분야 | 1 인공지능 · 제조업 적용 |
| 시즌 | 기본 |
| 대결 | 새 가마 K5·K6의 R² 약속 정직성 → 결과 F (초파리 승), 차이 0.066 vs 0.155 |
| 새로 그릴 그림 | P1 2장 · P2 3장 · P3 1장 (표지 별도: COVER_cement_quality.md) |
| 재사용 | 표정 15장 (기본 캐릭터 팩에서 이미 페이지에 넣음) |
| 그림이 없을 때 | 페이지는 대체 표지(CSS 가마 + 캐릭터 넷)와 캐릭터 팩 그림으로 이미 완성 상태 |

## 1. 그림체와 고정 외형
- 스타일: SKILL 18-3 (16비트 RPG 픽셀아트, 굵은 외곽선, 2~3단계 명암)
- 캐릭터 고정 외형: 캐릭터 팩 18-4 그대로
- 이 페이지 장소: 밤의 시멘트 공장 품질실 — 창밖의 회전 가마 불빛, 압축강도 시험기, 시편 선반
- 장소 영어 묘사: *a night-time quality control room inside a cement plant, a long rotary kiln glowing orange through the window, a compact compression testing press, shelves of small grey cement test cubes, rendered as part of the same night lab world, purple lab light spilling in from one side*

## 2. 필요한 그림 전체

| # | 키 | 판 | 크기 | 상태 | 우선 | 들어가는 곳 | 대신 쓰는 그림 |
|---|---|---|---|---|---|---|---|
| 0 | cover_cement | L | 1920×1080 | 새로 (COVER 지시문) | P1 | 맨 위 글 표지 | 대체 표지 (CSS 가마 + 캐릭터 넷) |
| 1 | bg_cement | F | 1920×720 | 새로 | P3 (표지 있음) | 히어로 배경 | 표지 자르기 |
| 2 | npc_owl | H→G | 192×192 투명 | 새로 | P1 | 등장인물 카드의 봉인관 | 캔버스로 그린 임시 부엉이 |
| 3 | cut_cement_lv2 | G | 960×540 | 새로 | P2 | ② 칸: 봉인관이 K5·K6 봉투를 지키는 컷 | 없음(컷 생략) |
| 4 | sc_cement_outro | E | 1200×800 | 새로 | P2 | 아웃트로 | 없음 |
| 5 | thumb_cement | I | 600×400 | 새로 (표지 3:2 자르기) | P2 | 목차 카드 | 색 카드 |
| 6 | og_cement | K | 1200×630 | 새로 (표지 자르기) | P3 | 공유 미리보기 | 없음 |
| — | doc_front·doc_think·doc_judge | A | 96 | 재사용 | — | 히어로, 판정, 아웃트로 | — |
| — | asst_smile·asst_firm·asst_report·asst_spark | B | 96 | 재사용 | — | 히어로, 발표, 아웃트로 | — |
| — | fly_clip·fly_point·fly_arms·fly_magnify | C | 96 | 재사용 (point·magnify는 좌우 뒤집어 씀) | — | 대결, 본문 말풍선 | — |
| — | robo_smile·robo_coin·robo_sigh·robo_chart | D | 96 | 재사용 | — | 대결, 4부, 아웃트로 | — |
| — | 1부 부스팅 실험·컨베이어·임계값 점 그림 | — | — | 코드 | — | 캔버스 | — |

## 3. 새로 그릴 그림 상세

### 3-1. `npc_owl` — 봉인관 (안경 쓴 부엉이)
| 항목 | 내용 |
|---|---|
| 판 · 크기 | 아이콘·카드용 192×192 (2배 384 가능) |
| 배경 | 투명 |
| 구도 | 정면, 날개로 봉인된 봉투 하나를 가슴 앞에 안고 있음 |
| 표정·몸짓 | 근엄하지만 친근, 둥근 금테 안경 |
| 피할 것 | 글자, 실존 마스코트와 닮은 디자인 |
| 대신 쓰는 그림 | 페이지 안 캔버스 부엉이 |

```
16-bit RPG style pixel art, bold dark outline, 2–3 tone shading, small highlights, consistent with the reference images, cozy night laboratory mood, purple light, single character, transparent background, centered with a small margin, facing front, full body, a small brown owl wearing round gold-rimmed glasses, holding a sealed envelope with a red wax seal against its chest with both wings, dignified but friendly expression, no text, no letters, no numbers, no logos, no weapons, no cigarettes, no alcohol, no blood, no real brands
```

### 3-2. `cut_cement_lv2` — 봉인한 시험지
| 항목 | 내용 |
|---|---|
| 판 · 크기 | G · 960×540 |
| 구도 | 가운데 봉인관이 봉투 두 개(K5·K6를 뜻함, 글자 없이 노란 봉투)를 금고 앞에서 지킴. 왼쪽 초파리가 오른쪽을 보며 봉투를 가리킴, 오른쪽 주판봇이 왼쪽을 보며 봉투를 힐끔 봄 |
| 소품 | 작은 원형 금고, 봉투 두 개, 줄무늬 서류 더미 |
| 피할 것 | 승패 암시, 글자 |
| 대체 글 | 봉인관 부엉이가 금고 앞에서 노란 봉투 두 개를 지키고 초파리 연구원과 주판봇이 양쪽에서 바라보는 장면 |

```
16-bit RPG style pixel art, bold dark outline, 2–3 tone shading, small highlights, consistent with the reference images, cozy night laboratory mood, purple light, soft magenta and green fluorescent accents, 16:9 illustration panel, a small brown owl with round gold glasses standing in front of a small round vault guarding two sealed yellow envelopes, on the left an anthropomorphic fruit fly researcher with big red compound eyes, a blue helmet with a gold stripe, white lab coat over a black vest, black gloves, facing right and pointing at the envelopes, on the right JUPANBOT (AbaBot), the boxy beige retro CRT-monitor robot with a dark green screen face with mint pixel eyes and mouth, a short antenna topped with a red-brown abacus bead, gray segmented arms and two small tank treads facing left glancing at the envelopes curiously, stacks of papers with blank striped pages, no text, no letters, no numbers, no logos, no weapons, no cigarettes, no alcohol, no blood, no real brands, no white round robot head, no yellow or golden eyes, no floating robot, no gold coins
```

### 3-3. `sc_cement_outro` — 아웃트로 (결과 F)
| 항목 | 내용 |
|---|---|
| 판 · 크기 | E · 1200×800 |
| 구도 | 승자 초파리가 앞 왼쪽에서 팔짱, 주판봇은 뒤 오른쪽에서 머쓱하게 나무 주판을 옆구리에 끼는 몸짓(조롱 없음), 박사 가운데 뒤에서 엄지, 조수가 시험 생산 일정표(빈 칸 격자)를 들고 있음. 창밖 가마 불빛 |
| 대체 글 | 대결이 끝난 뒤 품질실에서 초파리 연구원이 팔짱을 끼고 주판봇이 머쓱해하며 조수가 시험 생산 일정표를 든 장면 |

```
16-bit RPG style pixel art, bold dark outline, 2–3 tone shading, small highlights, consistent with the reference images, cozy night laboratory mood, purple light, warm orange kiln glow through a window, 3:2 landscape scene, medium brightness, a night-time quality control room inside a cement plant, in front on the left an anthropomorphic fruit fly researcher with big red compound eyes and a blue helmet with a gold stripe, white lab coat over a black vest, arms crossed with a satisfied look, behind on the right JUPANBOT (AbaBot), the boxy beige retro CRT-monitor robot with a dark green screen face with mint pixel eyes and mouth, a short antenna topped with a red-brown abacus bead, gray segmented arms and two small tank treads shrugging and tucking its wooden abacus under one arm, good-natured, a chibi scientist with thin teal rectangular glasses, black hair with one white streak and a short ponytail, white lab coat over black vest and tie, at the back center giving a thumbs up, a girl researcher with long pink hair in two round buns and a navy streak holding a blank grid schedule board, shelves of grey cement test cubes, no text, no letters, no numbers, no logos, no weapons, no cigarettes, no alcohol, no blood, no real brands, no white round robot head, no yellow or golden eyes, no floating robot, no gold coins
```

### 3-4. `bg_cement` (P3) — 히어로 배경
```
16-bit RPG style pixel art, bold dark outline, 2–3 tone shading, small highlights, consistent with the reference images, cozy night laboratory mood, purple light, warm orange kiln glow, wide 8:3 background, left side simple and calm for title text, details on the right, a cement plant at night with a long rotary kiln glowing orange, a tall preheater tower and silos, faint green and magenta data-like light bars rising in the sky like a chart without numbers, no characters, no text, no letters, no numbers, no logos, no weapons, no cigarettes, no alcohol, no blood, no real brands
```

`thumb_cement`, `og_cement`는 표지를 3:2, 1200×630으로 잘라 만든다.

## 4. 일관성 지침
- 참고 이미지: 캐릭터 팩 설정샷 k02~k05, k12
- 같은 캐릭터는 같은 세션에서. 표정만 바꿀 때: *same character, same size and position, only change the facial expression and pose to ...*
- 투명 배경이 안 되면: *solid flat #00ff00 background*

## 5. 넘겨받은 뒤 처리
1. 크기·투명 배경 확인 → 2. WebP로 줄이기 → 3. 64px로 줄여 기존 표정과 비교 → 4. `data-img` 자리에 넣고 그림 합계 600 KB(표지 포함) 확인 → 5. 표지는 SKILL 18-15.

## 6. 매니페스트
```json
{
  "page": "cement_quality",
  "anchor": "D:cement-qc-room",
  "season": "default",
  "duel": {"result": "F", "gap": 0.089},
  "images": [
    {"key":"cover_cement","plate":"L","size":[1920,1080],"status":"new","priority":"P1","slot":"cover","fallback":"css-kiln-four","alt":"밤의 시멘트 공장 품질실에서 네 캐릭터가 굳어 가는 시편 줄과 그 위에 미리 떠오른 예측 막대를 바라보는 표지"},
    {"key":"npc_owl","plate":"H","size":[192,192],"status":"new","priority":"P1","slot":"cast-card","fallback":"canvas-owl","alt":""},
    {"key":"cut_cement_lv2","plate":"G","size":[960,540],"status":"new","priority":"P2","slot":"lv2","fallback":null,"alt":"봉인관 부엉이가 금고 앞에서 노란 봉투 두 개를 지키는 장면"},
    {"key":"sc_cement_outro","plate":"E","size":[1200,800],"status":"new","priority":"P2","slot":"outro","fallback":null,"alt":"대결이 끝난 뒤 품질실의 네 캐릭터"},
    {"key":"thumb_cement","plate":"I","size":[600,400],"status":"new","priority":"P2","slot":"index-card","fallback":"color-card","alt":"시멘트 품질 페이지 썸네일"},
    {"key":"bg_cement","plate":"F","size":[1920,720],"status":"new","priority":"P3","slot":"hero-bg","fallback":"cover_cement","alt":"밤의 시멘트 공장과 가마 불빛"},
    {"key":"og_cement","plate":"K","size":[1200,630],"status":"new","priority":"P3","slot":"og","fallback":null,"alt":""},
    {"key":"fly_point","plate":"C","size":[96,96],"status":"reuse","slot":"duel-before"},
    {"key":"fly_arms","plate":"C","size":[96,96],"status":"reuse","slot":"duel-after"},
    {"key":"robo_sigh","plate":"D","size":[96,96],"status":"reuse","slot":"duel-after"},
    {"key":"doc_judge","plate":"A","size":[96,96],"status":"reuse","slot":"verdict"}
  ]
}
```
