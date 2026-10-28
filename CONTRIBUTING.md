# 견줘 Git 협업 규칙

v1.4 · 2026-10-28 · 팀 공통 규칙

적용 대상: `gyeonjwo_backend`, `gyeonjwo_frontend`

## 01. 필수 병합 원칙과 dev 보호

**작성자 외 최소 1명의 승인을 받고 dev에 병합한다.**

- 작업 브랜치에서 변경하고 PR을 통해 `dev`에 반영한다. dev에 직접 푸시하지 않는다.
- 승인은 해당 저장소에서 승인 권한이 있는 리뷰어의 GitHub **Approve**로 받는다. 댓글이나 구두 확인으로 대체하지 않는다.
- 승인 후 변경 내용이 달라지면 다시 승인받는다. 충돌과 필수 수정 의견을 해결한 뒤 병합한다.
- dev의 강제 푸시와 삭제를 금지하며, 관리자도 동일한 병합 원칙을 따른다.

### dev에 적용할 보호 설정

두 저장소의 dev 브랜치를 대상으로 다음 항목을 설정한다.

| 설정 항목 | 적용 값 |
| --- | --- |
| PR을 통한 병합 | 필수 |
| 필수 승인 수 | 최소 1명 |
| 변경 후 기존 승인 처리 | 기존 승인을 무효화하고 재승인 요구 |
| 관리자 등의 규칙 우회 | 허용하지 않음 · PR 우회 대상도 지정하지 않음 |
| 강제 푸시 | 허용하지 않음 |
| 브랜치 삭제 | 허용하지 않음 |

위 표는 설정 기준이다. 이 문서를 올리는 것만으로 GitHub 보호 설정이 적용되지는 않으므로 저장소 설정에서 별도로 적용한다.

## 02. 브랜치 이름

```text
<type>/<short-description>
```

- 설명은 영문 소문자로 작성하고, 단어는 하이픈으로 연결한다.
- 작업 내용을 알 수 있는 짧은 이름을 사용한다.
- 기존 브랜치 이름은 유지하고 새 브랜치부터 적용한다.

| 접두어 | 용도 | 예시 |
| --- | --- | --- |
| `feature/` | 기능 추가 | `feature/counter-offer` |
| `fix/` | 오류 수정 | `fix/mail-classification` |
| `refactor/` | 구조 개선 | `refactor/candidate-tools` |
| `docs/` | 문서 변경 | `docs/git-conventions` |
| `test/` | 테스트 변경 | `test/review-flow` |
| `chore/` | 환경·의존성 관리 | `chore/dependencies` |
| `ci/` | 자동화 설정 변경 | `ci/pr-checks` |

## 03. 커밋 메시지

```text
<type>: <변경 내용>
```

- type은 영문 소문자로, 변경 내용은 한국어로 작성한다. 고유명과 코드 식별자는 원래 표기를 유지한다.
- 콜론 뒤에 공백을 한 칸 둔다.
- “수정”, “완료” 대신 무엇을 바꿨는지 적는다.
- 추가 설명이 필요하면 제목 다음에 빈 줄을 두고 본문을 작성한다.

| type | 용도 |
| --- | --- |
| `feat` | 기능 추가 |
| `fix` | 오류 수정 |
| `refactor` | 외부 동작 변경 없는 구조 개선 |
| `docs` | 문서 변경 |
| `test` | 테스트 추가·수정 |
| `chore` | 환경·의존성 관리 |
| `ci` | 자동화 설정 변경 |
| `perf` | 성능 개선 |
| `revert` | 기존 변경 되돌리기 |

```text
feat: 역제안 초안 생성 추가
fix: 자동 응답을 견적 회신으로 처리하는 오류 수정
docs: Git 협업 규칙 추가
test: 검토 결과 조회 테스트 추가
```

기능 추가는 브랜치에서 `feature/`, 커밋에서 `feat:`를 사용한다. Git이 자동 생성하는 merge·revert 메시지는 그대로 사용할 수 있다.

## 04. 필수 보안 원칙

**실제 `.env`, 비밀키, 토큰, 인증서 개인키, 민감한 원본 자료를 커밋하지 않는다.**

- 해당 파일은 `.gitignore`로 제외하고 커밋 전 포함 여부를 확인한다. 소스·문서·로그에 값을 복사해 넣는 것도 금지한다.
- `.env.example`에는 실제 인증정보 대신 예시 값만 적는다.
- 이미 추적 중인 파일은 `.gitignore`에 추가해도 자동으로 제외되지 않는다.

---

설정 참고: [GitHub 브랜치 보호](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches) · [GitHub 파일 추적 제외](https://docs.github.com/en/get-started/git-basics/ignoring-files)
