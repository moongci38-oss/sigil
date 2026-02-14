# Business Workspace - AI Assistant Instructions

> 1인 기업 전체 업무를 위한 AI 워크스페이스. 개발 외 시장조사, 기획, 디자인, 마케팅, 콘텐츠 업무를 커버한다.

---

## Workspace Context

이 워크스페이스는 **비개발 업무** 중심이다. 코드 작성보다 **리서치, 기획, 글쓰기, 분석**이 주요 작업.

**소유자**: 1인 기업 운영자 (풀스택 개발자 겸 사업가)
**개발 프로젝트**: `~/mywsl_workspace/portfolio-project/` (별도 워크스페이스)

---

## Folder Structure

| 폴더 | 용도 | 주요 작업 |
|------|------|----------|
| `01-research/` | 시장조사 & 분석 | 경쟁사 분석, 트렌드 리서치, 데이터 수집 |
| `02-strategy/` | 사업기획 & 전략 | 사업계획서, 가격 모델, 린 캔버스 |
| `03-design/` | 디자인 에셋 | UI 목업, 브랜드 에셋, 생성 이미지 |
| `04-marketing/` | 마케팅 & 그로스 | 캠페인, 이메일, SNS, SEO |
| `05-content/` | 콘텐츠 제작 | 블로그, 문서, 뉴스레터 |
| `06-dev-tools/` | 개발 도구 & 스킬 | 스킬 라이브러리, 자동화, 프롬프트 |
| `07-operations/` | 운영/관리 | 재무, 법무, 프로세스 |

---

## Golden Rules

### Do's
- 리서치 결과는 출처(URL, 날짜)를 반드시 포함
- 문서 작성 시 한국어 기본, 전문 용어는 영어 병기
- 파일명은 kebab-case + 날짜 prefix 권장 (`2026-02-13-market-analysis.md`)
- 민감 자료(재무, 법무)는 `07-operations/` 하위에만 저장
- 스킬 활성화/비활성화는 `scripts/manage-skills.sh` 사용

### Don'ts
- 이 워크스페이스에서 코드 프로젝트 개발 금지 (개발은 portfolio-project에서)
- `07-operations/finances/`, `07-operations/legal/` 내용을 외부 공유/출력 금지
- 검증 없는 시장 데이터를 사실로 단정 금지
- 스킬 라이브러리 원본 직접 수정 금지 (심링크로 활성화만)

---

## Skill System

### 활성 스킬
`.claude/skills/` 디렉토리의 스킬이 자동 로드됨.

### 스킬 관리
```bash
# 전체 스킬 목록 + 활성 상태
bash scripts/manage-skills.sh list

# 스킬 활성화 (skills-library → .claude/skills/ 심링크)
bash scripts/manage-skills.sh enable aitmpl/business-marketing/product-strategist

# 스킬 비활성화
bash scripts/manage-skills.sh disable product-strategist

# 다른 프로젝트에 개발 스킬 심링크
bash scripts/manage-skills.sh sync ~/mywsl_workspace/portfolio-project
```

### 스킬 라이브러리 구조
```
06-dev-tools/skills-library/
├── aitmpl/              ← aitmpl.com 스킬
│   ├── development/     ← 개발 스킬 (NestJS, Next.js 등)
│   ├── business-marketing/ ← 비즈니스/마케팅 스킬
│   ├── security/        ← 보안 스킬
│   └── ai-research/     ← AI 연구 스킬
├── marketingskills/     ← coreyhaines31 마케팅 스킬
└── community/           ← 기타 커뮤니티 스킬
```

---

## Task Patterns by Business Area

### 시장조사 (01-research)
```
"경쟁사 X 분석해줘" → 01-research/competitors/에 결과 저장
"Y 시장 트렌드 조사" → 01-research/trends/에 결과 저장
```

### 사업기획 (02-strategy)
```
"린 캔버스 작성해줘" → 02-strategy/lean-canvas/에 저장
"가격 모델 비교" → 02-strategy/pricing-models/에 저장
```

### 마케팅 (04-marketing)
```
"이메일 시퀀스 작성" → 04-marketing/email-sequences/에 저장
"SEO 키워드 분석" → 04-marketing/seo/에 저장
```

### 콘텐츠 (05-content)
```
"블로그 포스트 초안" → 05-content/blog-posts/에 저장
"뉴스레터 작성" → 05-content/newsletters/에 저장
```

---

## File Naming Convention

```
{YYYY-MM-DD}-{description}.{ext}

예시:
2026-02-13-competitor-analysis-saas.md
2026-02-13-pricing-model-v2.xlsx
2026-Q1-marketing-report.md
```

---

## Output Preferences

- **문서**: Markdown 기본. 필요 시 DOCX/PDF 변환
- **스프레드시트**: CSV 또는 XLSX
- **프레젠테이션**: PPTX (pitch-decks)
- **언어**: 한국어 기본, 해외 대상 자료는 영어

---

*Last Updated: 2026-02-13*
