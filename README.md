# 시멘트 품질, AI로 미리 본다

> 28일을 기다리지 않고, 오늘 만든 시멘트의 강도를 믿을 만한 숫자로 말할 수 있을까?

회귀·분류 모델로 시멘트 **28일 압축강도**와 **불량**을 예측하는 4단계 실습입니다. 생성 AI에 프롬프트를 주고, 받은 코드를 Google Colab에서 실행하고, 결과를 공정 엔지니어의 눈으로 읽습니다. 박사 · 조수 · 초파리 연구원 · 주판봇이 진행하는 연구실 해설 대시보드 형식입니다.

**▶ 바로 보기:** https://adminmrobo.github.io/cement_quality_ai/

글 · 안상선 ((주)M-Robo 대표)

---

## v1.1 쉬운 풀어쓰기판 (2026-11-09)

시멘트도 AI 모델도 처음 보는 수강생을 위해 본문을 풀어 썼습니다.

- **0-1 시멘트 첫걸음 · 0-2 AI 모델 첫걸음** — 새 준비 칸 두 개
- **여기서 잠깐!** — 시멘트 이야기(정의·역사·원료·굽기·클링커 4형제·석고·수화·28일 강도·분말도·슬래그·유리석회 등)와 AI 이야기
- **조수(하루)의 수식 이야기** — RMSE·R²·표준편차·재현율·SHAP·원가 함수·안전 여유를 숫자 예시와 이야기로 풀이
- 각 칸 앞뒤의 캐릭터 대화, "스스로 확인" 문제, 용어 한 장 정리
- 본문 삽화 7장 자리(`img/F01~F07`) — 그림 지시문은 `docs/IMG_easy_cement_quality.md`

## 목차

| 단계 | 질문 | 배우는 것 | 핵심 숫자 |
|---|---|---|---|
| [1. 첫 예측 모델](https://adminmrobo.github.io/cement_quality_ai/cement_quality.html#lv1) | 28일을 기다리지 않고 강도를 알 수 있을까? | 입력·출력 변수, 부스팅 트리, RMSE·R² | RMSE 2.33 MPa, R² 0.77 |
| [2. 이걸 믿어도 되나](https://adminmrobo.github.io/cement_quality_ai/cement_quality.html#lv2) | 좋은 점수는 진짜인가? | 분할, 과적합, 데이터 누수, 그룹 분할, 분류와 임계값 | 무작위 0.86 → 새 가마 0.68 |
| [3. 무엇이 강도를 정하나](https://adminmrobo.github.io/cement_quality_ai/cement_quality.html#lv3) | 모델은 왜 그렇게 맞혔나? | SHAP 기여도, 워터폴, 파생 변수, 중요도 ≠ 인과 | 분말도·슬래그·유리석회 |
| [4. 값을 붙이면 답이 달라진다](https://adminmrobo.github.io/cement_quality_ai/cement_quality.html#lv4) | 목표 강도를 지키는 가장 싼 배합은? | 목적함수, 제약 조건, 안전 여유 | 67,400 → 63,000원/t (예시값) |
| [대결](https://adminmrobo.github.io/cement_quality_ai/cement_quality.html#duel) | 새 가마의 성적을 누가 정직하게 약속했나? | 평가 방식과 보고 숫자 | 초파리 승 |

## 파일 구성

```
cement_quality_ai/
├── index.html              # 목차 (GitHub Pages 첫 화면)
├── cement_quality.html     # 해설 대시보드 본문 (단일 파일, 설치 없음)
├── data/
│   └── cement_process.csv  # 실습 데이터 3,000행 × 14열
├── docs/
│   ├── COVER_cement_quality.md  # 표지 그림 생성 지시문 (Genspark 등)
│   └── IMG_cement_quality.md    # 이미지 제작 명세서
├── .nojekyll
└── README.md
```

## 실습 데이터

`data/cement_process.csv` — 가마 6기(K1~K6) × 로트 500개 = 3,000행, 14열. 실제 공정 경향(분말도↑ 강도↑, 유리석회↑ 강도↓ 등)을 흉내 낸 **교육용 가상 데이터**입니다(numpy 난수 시드 42).

| 열 | 뜻 | 쓰임 |
|---|---|---|
| `lot_id`, `kiln_id`, `prod_date` | 로트 번호, 가마 번호, 생산 일시 | 입력 아님 |
| `limestone_pct`, `kiln_temp`, `c3s_pct`, `c3a_pct`, `free_lime_pct`, `gypsum_pct`, `blaine`, `slag_pct` | 석회석, 소성 온도, C₃S, C₃A, 유리석회, 석고, 분말도, 슬래그 | 입력 8개 |
| `strength_7d` | 7일 강도 | 입력 금지 (데이터 누수) |
| `strength_28d` | 28일 강도, 평균 48.0 MPa | 출력 · 회귀 |
| `defect` | 불량 여부, 불량률 14.3 % | 출력 · 분류 |

## 실습 방법

1. [Google Colab](https://colab.research.google.com)에 접속합니다.
2. 해설 페이지 각 단계의 "실습 프롬프트"를 생성 AI에 붙여 넣습니다.
3. 받은 코드를 Colab 셀에 붙여 넣고 실행합니다. 오류가 나면 오류 메시지 전체를 다시 AI에게 줍니다.
4. 결과 숫자를 보고 "공정적으로 말이 되나?"를 묻습니다.

생성 AI는 같은 프롬프트에도 다른 코드를 낼 수 있습니다. 페이지의 숫자와 똑같이 맞추려면 페이지에 접어 둔 "실제로 사용한 코드"를 쓰거나 `data/cement_process.csv`를 업로드해 씁니다. 페이지의 모든 수치는 scikit-learn 1.9.1, shap 0.54.1로 다시 실행해 확인했습니다.

## GitHub Pages로 공개하기

1. 이 폴더의 파일을 저장소 맨 위에 올립니다.
2. 저장소 **Settings → Pages**에서 Source를 **Deploy from a branch**, Branch를 `main` / `/ (root)`로 정합니다.
3. 몇 분 뒤 `https://<계정>.github.io/<저장소 이름>/`에서 열립니다. 저장소 이름을 바꾸면 이 README의 링크도 함께 바꿉니다.

외부 라이브러리와 서버가 필요 없습니다. 외부 요청은 Google Fonts 글꼴 하나뿐이며, 글꼴을 못 받아도 시스템 글꼴로 보입니다.

## 참고문헌

- Friedman, J. H. (2001). Greedy function approximation: A gradient boosting machine. *The Annals of Statistics*, 29(5), 1189–1232.
- Lundberg, S. M., & Lee, S.-I. (2017). A unified approach to interpreting model predictions. *Advances in Neural Information Processing Systems*, 30.
- Lundberg, S. M., et al. (2020). From local explanations to global understanding with explainable AI for trees. *Nature Machine Intelligence*, 2.
- Pedregosa, F., et al. (2011). Scikit-learn: Machine learning in Python. *Journal of Machine Learning Research*, 12, 2825–2830.
- Kaufman, S., Rosset, S., Perlich, C., et al. (2012). Leakage in data mining: Formulation, detection, and avoidance. *ACM Transactions on Knowledge Discovery from Data*, 6(4).
- Shapley, L. S. (1953). A value for n-person games. *Contributions to the Theory of Games II*.

전체 서지(CSL-JSON, BibTeX, RIS)와 온톨로지(JSON-LD, Turtle, CSV)는 해설 페이지 맨 아래 "온톨로지·서지 꾸러미"에서 ZIP으로 내려받을 수 있습니다.

## 인용

```
안상선 (2026). 시멘트 품질, AI로 미리 본다. 연구실 해설 대시보드 · 제조 AI, v1.0.
```

## 저작권

- 글·실습 구성: 안상선 ((주)M-Robo)
- 캐릭터(박사, 조수, 초파리 연구원, 주판봇)의 이름·설정·그림: 저작권 안상선. 허락 없이 쓸 수 없습니다. 원본: [fruitfly-lab-expressions](https://github.com/adminmrobo/fruitfly-lab-expressions)
- 데이터와 원가 단가는 교육용 가상값이며 실제 공장의 수치가 아닙니다.
