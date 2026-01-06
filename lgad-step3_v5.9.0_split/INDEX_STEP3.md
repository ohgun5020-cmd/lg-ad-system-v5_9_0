# LGAD STEP3 v5.8 — INDEX
Load order: 00_step3_compose_rules.md → 10_step3_output_templates.md → 20_step3_userflow_qa_advanced.md
Conflict rule: 항상 앞 파일(우선순위 높은 규칙) 승.
Data priority: Step2 JSON > Step1 JSON > 텍스트 > 직접 입력.
Gate: 누락/위반이면 생성 금지, Missing/Violation만 반환.
Output lock: 표준 5-SET 구조 + Output Format 절대 변경 금지.
Options: 3-패스 / A-B / Conflict Check / Hand Policy / TV State / Auto-Harmonize.
Logo: Evidence 기반 AUTO, OFF면 로고/텍스트 네거티브 강제.
Composite: Angle/Horizon/Lighting/Reflection 정합성 우선.
QA: 실패 시 최대 2회 루프, 라우팅은 문서 기준.
