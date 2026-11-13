<!--
  ✏️ 팀 메모 (최종 제출 전 이 주석 삭제)
  - [팀이름], [GitHub ID], [레포 URL] 같은 대괄호 부분을 실제 값으로 바꾸세요.
  - "(예정)"이 붙은 항목은 구현되면 표시를 지우세요.
-->

# 🕵️ QueryCase — SQL로 사건을 푸는 추리 게임

![License: MIT](https://img.shields.io/badge/code-MIT-blue)
![License: CC BY 4.0](https://img.shields.io/badge/cases-CC%20BY%204.0-lightgrey)
![Cases](https://img.shields.io/badge/cases-1-green)

> 데이터베이스에 남은 흔적을 SQL로 추적해 범인을 찾아내세요.

**QueryCase**는 플레이어가 탐정이 되어 사건 데이터베이스에 직접 SQL을 입력하며 단서를 찾고 범인을 지목하는 브라우저 추리 게임입니다. 설치 없이 웹에서 바로 플레이할 수 있습니다.

🎮 **[지금 플레이하기]([레포 URL의 GitHub Pages 주소])** (예정)

---

## 📌 왜 만들었나요?

SQL 수업에서 `SELECT`, `JOIN`, `GROUP BY`를 배워도 "이걸 실제로 어디에 쓰지?"라는 감이 잘 오지 않습니다. 예제 테이블은 지루하고, 문법만 외우다 보면 금방 잊어버립니다.

QueryCase는 SQL을 **외워야 할 문법**이 아니라 **사건을 해결하는 도구**로 경험하게 합니다. 사건이 진행될수록 필요한 쿼리도 자연스럽게 어려워지도록 설계했습니다.

**대상 사용자:** SQL을 처음 배우거나 복습하고 싶은 대학생 (예: 데이터베이스 과목 수강생)

## ✨ 주요 기능

- **SQL 직접 입력**: 브라우저 안에서 실제 SQLite 쿼리를 실행하고 결과를 표로 확인
- **안전한 실행 환경**: `SELECT` 문만 허용하여 사건 데이터가 훼손되지 않음
- **스키마 보기**: 어떤 테이블과 컬럼이 있는지 언제든 확인 가능
- **범인 지목 및 정답 판정**
- **단계별 힌트** (예정): 막혔을 때 다음에 써볼 SQL 개념을 알려줌
- **난이도별 여러 사건** (예정)

## 🗂️ 사건 미리보기 — 사건 #001: ITM관 노트북 도난 사건

> 오후 3시경, ITM관 실습실에서 한 학생의 노트북이 사라졌다. 남아 있는 것은 출입 기록, 학내 카페 결제 내역, 그리고 몇몇 목격자의 진술뿐이다.

| 테이블 | 내용 |
|---|---|
| `students` | 학생 기본 정보 |
| `access_log` | 건물 출입 기록 |
| `card_payments` | 학내 카페 결제 내역 |
| `statements` | 목격자 진술 |

첫 단서는 이렇게 찾아보세요.

```sql
SELECT * FROM statements;
```

## 🚀 시작하기

### 바로 플레이하기
위의 플레이 링크로 접속하면 됩니다. 설치가 필요 없습니다.

### 로컬에서 실행하기 (개발자용)

```bash
# 1. 저장소 복제
git clone [레포 URL].git
cd querycase

# 2. 로컬 서버 실행 (사건 파일을 불러오기 위해 필요)
python -m http.server 8000

# 3. 브라우저에서 접속
# http://localhost:8000
```

### 테스트 실행하기 (예정)

모든 사건이 정답 쿼리로 실제 풀리는지 자동으로 검증합니다.

```bash
npm install
npm test
```

## 🏗️ 프로젝트 구조

```
querycase/
├── index.html              # 게임 화면
├── src/
│   ├── engine.js           # SQL 실행 (sql.js)
│   ├── validator.js        # SELECT 문만 허용하는 검사
│   └── ui.js               # 화면 렌더링
├── cases/
│   └── 001-itm-laptop/
│       ├── case.json       # 제목, 스토리, 난이도, 힌트, 정답
│       ├── schema.sql      # 테이블 정의
│       ├── data.sql        # 사건 데이터
│       └── solution.sql    # 정답 쿼리 (테스트용)
├── tests/                  # 사건 검증 테스트
├── .github/
│   ├── workflows/          # GitHub Actions CI
│   ├── ISSUE_TEMPLATE/
│   └── PULL_REQUEST_TEMPLATE.md
├── CONTRIBUTING.md
├── CODE_OF_CONDUCT.md
└── LICENSE
```

**기술 스택:** HTML · CSS · JavaScript · [sql.js](https://github.com/sql-js/sql.js) (브라우저용 SQLite) · GitHub Actions · GitHub Pages

## 🤝 기여하기

QueryCase는 누구나 기여할 수 있는 오픈소스 프로젝트입니다. 특히 **새로운 사건 만들기**는 코드를 몰라도 SQL과 이야기만으로 참여할 수 있습니다.

1. 기여하기 전에 [CONTRIBUTING.md](CONTRIBUTING.md)를 읽어주세요.
2. 버그나 아이디어는 [Issues]([레포 URL]/issues)에 템플릿에 맞춰 등록해주세요.
3. 처음이라면 `good first issue` 라벨이 붙은 이슈부터 시작해보세요.
4. 모든 변경은 Pull Request와 최소 1명의 리뷰를 거쳐 병합됩니다.

새 사건을 추가하려면 `cases/` 폴더에 위 구조대로 파일을 만들고 PR을 보내주세요. CI가 정답 쿼리로 범인이 정확히 한 명으로 좁혀지는지 자동으로 확인합니다.

모든 참여자는 [행동 강령](CODE_OF_CONDUCT.md)을 지켜주세요.

## 🗺️ 로드맵

- [ ] 사건 #001 플레이 가능 (MVP)
- [ ] `SELECT` 전용 검사기
- [ ] 사건 검증 CI 구축
- [ ] 단계별 힌트 시스템
- [ ] 사건 #002, #003 추가 (난이도: 중·상)
- [ ] 진행 상황 저장
- [ ] GitHub Pages 배포

## 👥 팀

서울과학기술대학교 산업공학과 ITM전공 · 오픈소스소프트웨어 팀 프로젝트

| 이름 | 역할 | GitHub |
|---|---|---|
| [이름] | 게임 엔진 (SQL 실행, 검사기, 정답 판정) | [@ID] |
| [이름] | 사건·데이터 (스토리, 스키마, 데이터 설계) | [@ID] |
| [이름] | UI · 인프라 (화면, 힌트, CI, 배포) | [@ID] |

## 🤖 AI 활용 방식

이 프로젝트는 개발 과정에서 AI 도구를 사용했으며, 그 과정을 투명하게 공개합니다.

| 맡긴 작업 | 검증 방법 | 결과 |
|---|---|---|
| [예: 사건 가상 데이터 생성] | [예: 정답 쿼리 테스트로 범인이 1명인지 확인] | [예: 범인이 2명 나오는 데이터를 직접 수정] |

## 💬 도움이 필요하면

- 사용 중 문제가 생기면 [Issues]([레포 URL]/issues)에 남겨주세요.
- 질문이나 제안은 [Discussions]([레포 URL]/discussions)를 이용해주세요. (예정)

## 📄 라이선스

- **소스 코드**: [MIT License](LICENSE) — 누구나 자유롭게 사용·수정·배포할 수 있도록 가장 간결하고 허용적인 라이선스를 선택했습니다.
- **사건 스토리와 데이터** (`cases/` 폴더): [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) — 코드가 아닌 창작물이므로 콘텐츠용 라이선스를 적용하고, 출처만 밝히면 수업 자료 등으로 재사용할 수 있게 했습니다.

## 🙏 참고 및 감사

- [SQL Murder Mystery](https://github.com/NUKnightLab/sql-mysteries) (Northwestern University Knight Lab) — SQL로 사건을 푼다는 아이디어에서 영감을 받았습니다. QueryCase는 한국어 사용자, 캠퍼스 배경 사건, 단계별 학습 설계, 커뮤니티 사건 기여 구조에 초점을 둡니다.
- [sql.js](https://github.com/sql-js/sql.js) — 브라우저에서 SQLite를 실행할 수 있게 해준 프로젝트
