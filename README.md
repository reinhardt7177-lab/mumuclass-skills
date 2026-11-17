# 무무 교사 스킬 (mumuclass-skills)

교사를 위한 **바이브코딩 실전 스킬** 모음입니다. 각 스킬은 `SKILL.md` 하나로 되어 있어, **긁어서 Claude나 Codex에 넣으면 바로 작동**합니다.

> 만든 곳: [무궁무진클래스](https://www.mumuclass.kr) · 모든 스킬은 실제 test-run으로 검증했습니다.

## 스킬 목록 (9종)

| 스킬 | 하는 일 | 분야 |
|---|---|---|
| `class-brain` | 우리 반 서브 브레인(CLAUDE.md/AGENTS.md) 셋업 | 기본 세팅 |
| `worksheet-maker` | 수준별 학습지(문제+정답+해설) | 수업 준비 |
| `lesson-planner` | 수업지도안(목표·활동·평가) | 수업 준비 |
| `quiz-maker` | 형성평가 퀴즈(OX·객관식) | 수업 준비 |
| `rubric-maker` | 평가 루브릭(요소·수준·배점) | 평가 |
| `grading-helper` | 루브릭 기반 채점 + 성장 피드백 | 평가 |
| `feedback-writer` | 개별 피드백(칭찬+조언) | 평가·소통 |
| `record-writer` | 생기부 세특·행발 문구(사실 기반) | 평가·기록 |
| `newsletter-writer` | 가정통신문·안내문 | 소통 |

## 설치 방법

### 방법 1. 붙여넣기 (가장 쉬움 · 비개발자용)
원하는 스킬 폴더의 `SKILL.md` 내용을 복사해서 Claude나 Codex에 붙여넣고 **"이걸 스킬로 설치해줘"**라고 하세요. AI가 알아서 파일을 만들어 설치합니다.

### 방법 2. 명령어로 긁어오기
**Claude Code** — `~/.claude/skills/`에 저장, `/이름`으로 호출
```bash
curl -fsSL --create-dirs -o ~/.claude/skills/worksheet-maker/SKILL.md \
  https://raw.githubusercontent.com/reinhardt7177-lab/mumuclass-skills/main/skills/worksheet-maker/SKILL.md
```

**Codex CLI** — `~/.agents/skills/`에 저장, `$이름`으로 호출
```bash
curl -fsSL --create-dirs -o ~/.agents/skills/worksheet-maker/SKILL.md \
  https://raw.githubusercontent.com/reinhardt7177-lab/mumuclass-skills/main/skills/worksheet-maker/SKILL.md
```
(다른 스킬은 `worksheet-maker` 부분만 원하는 스킬 이름으로 바꾸면 됩니다.)

### 방법 3. 마켓플레이스로 한 번에 (Claude Code)
```
/plugin marketplace add reinhardt7177-lab/mumuclass-skills
/plugin install mumu-teacher-skills@mumuclass-skills
```

## 메이커 키트 (해커톤·앱 제작) — `plugins/mumu-maker-kit`

앱·게임을 직접 만드는 선생님을 위한 꾸러미입니다. 스킬 5종 + 서브에이전트 3종.

| 종류 | 이름 | 하는 일 |
|---|---|---|
| 스킬 | `craft-consult` | 만들기 전 상담: 사례 조사 → 구조가 다른 방향 2~3개 → 시안 → 승인 |
| 스킬 | `detail-qa` | 보여 주기 전 10개 항목 디테일 검수 |
| 스킬 | `ship-check` | 깃허브 → 배포 → 운영 주소에서 최신 버전 확인 → 주소 전달 |
| 스킬 | `hackathon-kickoff` | 주제 좁히기 → 스택 고르기 → 2시간 안 첫 배포 → 시연·발표 준비 |
| 스킬 | `edu-content-writer` | 교육용 글·문제: 설계표 → 한 번에 쓰기 → 통째로 다시 읽기, 학습 위계 |
| 에이전트 | `design-critic` | 스크린샷 기반 디자인 검수 (파일 수정 안 함) |
| 에이전트 | `edu-reviewer` | 학습 위계·문맥·정답·초등 언어 검토 (파일 수정 안 함) |
| 에이전트 | `qa-tester` | 실제로 눌러 보며 버그·회귀 찾기 (파일 수정 안 함) |

```
/plugin marketplace add reinhardt7177-lab/mumuclass-skills
/plugin install mumu-maker-kit@mumuclass-skills
```

## 기본 세팅 — `setup/`
- [`setup/CLAUDE.md`](setup/CLAUDE.md): 전역 지침 틀. Claude는 `~/.claude/CLAUDE.md`, Codex는 `~/.codex/AGENTS.md`에 넣습니다. `[ ]` 칸은 내 정보로 바꾸세요. 기존 파일이 있으면 덮어쓰지 말고 합치세요.
- [`setup/SUBAGENTS.md`](setup/SUBAGENTS.md): 서브에이전트 설정법 (Claude·Codex)

## 안전 안내
- 이 스킬들은 교사 업무를 돕는 **지침**입니다. `record-writer`(생기부)처럼 민감한 스킬은 **사실 날조를 막는 안전장치**를 넣었지만, **최종본은 반드시 교사가 사실을 확인한 뒤** 사용하세요.
- 학생 개인정보(실명·연락처·진단·가정사 등)는 AI 대화창에 입력하지 않는 것을 권장합니다. 실명 대신 번호·이니셜을 쓰세요.
- 커스텀 스킬을 설치한다는 것은 그 지침을 내 AI가 실행한다는 뜻입니다. 내용을 확인한 뒤 설치하세요.

## 라이선스
MIT
