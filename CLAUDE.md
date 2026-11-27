# CLAUDE.md

정세영의 개발 포트폴리오 정적 사이트(https://ar2723.github.io). 빌드 없이 HTML·CSS만 쓴다. 공통 지침은 전역 `~/.claude/CLAUDE.md`, 개인 맥락(경력, 진행 중인 일)은 이 프로젝트의 메모리에 있다.

## 지켜야 할 것

- **public 저장소이고 `main` push가 곧 공개다.** push 전에 사용자에게 확인하고, push 후 `gh run list -R ar2723/ar2723.github.io --limit 1`로 Pages 배포 성공을 본다.
- **가림 기준**: 회사명은 공개해도 된다. 고객사 코드, 회원번호·CI 같은 개인 식별값, 사람 실명·닉네임, 회사 내부 주소(Canvas·레드마인 등), 사용자 ID·이메일, 서버 IP·포트·계정 이름은 넣지 않는다. 아직 고치지 않은 보안 취약점은 절대 쓰지 않는다.
- **재직 중인 회사(메트라이프)**: 사내 코드·고객 데이터·내부 시스템 이름은 다루지 않는다. 사용자가 직접 요약한 업무 설명만 쓴다.
- **문구**: 쉬운 말로 쓴다. 장애 사례는 원인 → 대응 → 남긴 것 순서, 수치 박스는 최소화. 남 탓으로 읽히지 않게 "그래서 무엇을 바꿨는지"를 함께 쓴다.

## 구조

| 파일 | 내용 |
|---|---|
| `index.html` | 머리말(약력), 경력 타임라인, "발자취"(회사별 사례 카드), 목차(1100px 이상은 왼쪽 고정 사이드바, 좁으면 상단 메뉴) |
| `cases/<slug>.html` | 사례 상세. `article.case` 안에 `case-meta`, `h3`, `p.lead`, `dl.steps`(dt/dd) |
| `styles.css` | 공통 스타일. 휴대폰(~600px)·태블릿(~1024px)·데스크톱 대응, 다크 모드 |
| `images/` | 흐름도·화면 캡처 |

## 수정 규칙

- **사례를 추가·삭제하거나 제목을 바꾸면 세 곳을 함께 고친다**: `cases/<slug>.html`, `index.html`의 회사별 카드(`div.group#g-...`), 사이드바 `div.side-cases`의 `details` 안 링크.
- **`styles.css`를 고치면 모든 HTML의 `styles.css?v=` 값을 올린다**(브라우저 캐시 때문에 안 바뀌어 보임).
- 한국어 줄바꿈은 `word-break: keep-all`이 전역에 걸려 있다. 긴 코드는 `.code` 블록(가로 스크롤)에 넣는다.
- 화면 확인: `jwebserver`(JDK 포함)로 로컬에 띄우고 Chrome에서 iframe 폭(390/820px)을 바꿔 본다. 창 크기 조절은 최대화 상태라 안 먹을 수 있다.

## 원본 자료 위치

- Google Drive: Obsidian 업무 일지(2024.03~11), 검진정산 흐름도 PDF, 라이너스 SSO Confluence PDF, 이력서·경력기술서
- Notion: "개발자 이직 대비 생각 정리", "개발자 재활 일지"
- Coda(Superhuman Docs) 워크스페이스: 로그인 필요, Chrome 연결(`/chrome`)로 접근
- Velog: https://velog.io/@ar2723/posts (KCP 서명 글만 사용)

## 보류 중인 것

- 숨겨 둔 "운영 원칙" 섹션(`index.html`의 `section[hidden]`): 사용자가 보류 결정.
- 메트라이프 개발·유지보수 건, 보안 취약점 조치: 사용자가 먼저 리스트로 정리한 뒤 사례로 추가한다.
- 미니PC 서버 보안 조치 4~6번은 북메이트 저장소 작업이다. 고친 뒤 `cases/minipc-game-server.html`의 보안 조치 목록에 추가한다.
