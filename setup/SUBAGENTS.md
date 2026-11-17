# 서브에이전트 설정법

서브에이전트는 **한 가지 일만 맡는 보조 AI**입니다. 메인 AI가 일을 하다가 "디자인 검수", "교육 내용 검토", "실행 테스트"를 따로 맡겨서, 자기 작업에 끌려가지 않은 독립된 눈으로 점검받게 합니다.

## 1. Claude Code
서브에이전트는 마크다운 파일 하나입니다.

| 넣는 곳 | 적용 범위 |
|---|---|
| `~/.claude/agents/이름.md` | 내 컴퓨터의 모든 프로젝트 |
| `프로젝트폴더/.claude/agents/이름.md` | 그 프로젝트에서만 |

### 파일 모양
```markdown
---
name: design-critic
description: 언제 이 에이전트를 부르는지 한두 문장. 메인 AI가 이 문장을 보고 맡길지 판단해요.
tools: Read, Grep, Glob, Bash
---

여기에 이 에이전트의 역할, 할 일, 돌려줄 형식을 씁니다.
```
- `tools`를 적으면 그 도구만 씁니다. 검수용 에이전트는 Edit·Write를 빼서 **파일을 못 고치게** 하면 안전해요.
- `model`을 적어 가벼운 모델로 돌릴 수도 있어요(예: `model: haiku`). 비우면 메인과 같은 모델을 씁니다.

### 부르는 법
- 자연스럽게: "design-critic 에이전트로 이 화면 검수해 줘"
- 메인 AI가 description을 보고 알아서 맡기기도 해요.
- 터미널에서 `/agents`를 입력하면 목록을 보고 만들고 고칠 수 있어요.

### 무무 메이커 키트의 3종
| 에이전트 | 하는 일 |
|---|---|
| `design-critic` | 화면을 띄워 스크린샷으로 10개 항목 디테일 검수 |
| `edu-reviewer` | 학습 위계·문맥·정답·오답 보기·초등 언어 검토 |
| `qa-tester` | 실제로 눌러 보며 버그·사라진 기능 찾기 |

플러그인으로 설치하면 자동으로 들어가고, 하나씩 받을 때는 아래처럼 받습니다.
```bash
curl -fsSL --create-dirs -o ~/.claude/agents/design-critic.md https://raw.githubusercontent.com/reinhardt7177-lab/mumuclass-skills/main/plugins/mumu-maker-kit/agents/design-critic.md
```

## 2. Codex
Codex는 `~/.codex/agents/이름.toml` 파일을 서브에이전트로 씁니다. 모양은 이렇습니다.

```toml
name = "design-critic"
description = "언제 이 에이전트를 부르는지 한두 문장"
developer_instructions = """
여기에 역할, 할 일, 돌려줄 형식을 씁니다.
"""
```

무무 메이커 키트의 3종은 Codex용 `.toml`도 함께 들어 있습니다.
```bash
curl -fsSL --create-dirs -o ~/.codex/agents/design-critic.toml https://raw.githubusercontent.com/reinhardt7177-lab/mumuclass-skills/main/plugins/mumu-maker-kit/codex-agents/design-critic.toml
```
(Codex 버전에 따라 서브에이전트 지원 방식이 다를 수 있어요. 목록에 안 보이면 `~/.codex/AGENTS.md`에 "화면을 보여 주기 전에 design-critic 역할로 검수한다"처럼 적어 두면 같은 효과를 낼 수 있어요.)

## 3. 잘 쓰는 요령
- 에이전트는 **좁고 분명하게**. "다 해 주는 에이전트"보다 "한 가지를 깐깐하게 보는 에이전트"가 낫습니다.
- 검수 에이전트는 문제 목록만 돌려주고, 고치는 건 메인이 하게 하세요. 누가 무엇을 바꿨는지 헷갈리지 않습니다.
- 병렬로 너무 많이 띄우면 사용량 한도에 금방 걸립니다. 3~4개 이내를 권장해요.
