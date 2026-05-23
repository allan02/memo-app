# 📋 나의 할 일

순수 HTML / CSS / JavaScript 로 만든 개인용 할 일 관리 웹앱입니다.
빌드 도구나 별도 서버 없이 브라우저에서 바로 실행되며, 데이터는 **Supabase PostgreSQL** 에 저장됩니다.

## 주요 기능

- 할 일 추가 / 수정(인라인 편집) / 삭제
- 완료 토글 (체크박스 + 취소선)
- 카테고리 분류: 업무 / 개인 / 공부 (색상 구분)
- 카테고리별 필터링 + 활성 필터 시각 표시
- 진행률 표시: 프로그레스 바 + `X / Y 완료 (Z%)` 텍스트
- 빈 상태 안내 메시지
- Supabase를 통한 데이터 영구 저장 및 기기 간 동기화
- 모바일(≤ 480px) 반응형 레이아웃

## 실행 방법

별도의 빌드나 패키지 설치가 필요 없습니다.

**방법 1 — 파일 직접 열기**

`index.html`을 파일 탐색기에서 더블클릭하거나, 브라우저 주소창에 파일 경로를 입력합니다.

**방법 2 — 로컬 서버 (권장)**

```bash
# Python 3
python3 -m http.server 8000

# Node.js
npx serve
```

이후 브라우저에서 `http://localhost:8000` 으로 접속.

## 데이터 저장

모든 할 일은 **Supabase PostgreSQL** 의 `todo` 테이블에 저장됩니다.

| 컬럼 | 타입 | 설명 |
|------|------|------|
| id | UUID | 기본 키 (자동 생성) |
| text | TEXT | 할 일 내용 |
| category | TEXT | 카테고리 (work / personal / study) |
| completed | BOOLEAN | 완료 여부 |
| created_at | TIMESTAMPTZ | 생성 시각 |

- 어떤 기기, 어떤 브라우저에서 열어도 동일한 데이터를 볼 수 있습니다.
- Supabase JS 클라이언트는 CDN으로 로드됩니다.

## 파일 구조

```
memo-app/
├── index.html   # DOM 골격 + Supabase CDN 로드
├── style.css    # 스타일 + 카테고리 색상 + 반응형
├── app.js       # 데이터(Supabase) / 렌더링 / 이벤트 / 초기화
└── README.md    # 본 문서
```
