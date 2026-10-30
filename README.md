# SKHH

현업 담당자의 요청을 받아 웹 서비스나 작은 도구를 만들 때, AI 코딩 에이전트와 함께 쓰는 개인 작업 규칙과 절차입니다. 요구가 덜 정해진 상태에서 시작해 담당자와 주고받으며 좁혀 가는 일에 맞춰 두었습니다. 특정 프로젝트의 코드는 들어 있지 않습니다.

## 구성

| 파일 | 역할 |
| --- | --- |
| `AGENTS.md` | 에이전트가 항상 지키는 작업 규칙. 아래쪽 '해커톤 대비'는 해커톤 환경에 맞춰 덧붙인 규칙 |
| `.agents/skills/next` | 막혔을 때: 확인된 것과 가정을 정리하고, 담당자에게 확인할 것과 다음 한 걸음 제안 |
| `.agents/skills/loop` | 반복: 담당자 답이나 확인 결과를 한 단계씩 반영 |
| `.agents/skills/handoff` | 위임·이어가기: 현재 상태를 HANDOFF.md 한 장으로 정리 |
| `.agents/skills/wrapup` | 마무리: 범위 점검, 결과 문서, 결정 요약 |

## 적용 방법

```bash
git clone --depth 1 https://github.com/ytm220/SKHH /tmp/skhh
cp -r /tmp/skhh/.agents .
# 작업 폴더에 AGENTS.md가 이미 있으면 덧붙이고, 없으면 복사한다
if [ -f AGENTS.md ]; then printf '\n' >> AGENTS.md; cat /tmp/skhh/AGENTS.md >> AGENTS.md; else cp /tmp/skhh/AGENTS.md .; fi
```

작업 폴더 밖에 clone하고 필요한 파일만 복사합니다. 작업 폴더의 git에는 이 저장소 주소가 연결되지 않습니다. 복사한 뒤 `codex`를 실행하고 `/skills`에서 스킬 4개가 보이는지 확인합니다.

## 쓰는 법

평소처럼 대화하며 진행한다. 결정을 표로 남기고 다음 후보를 따로 적어 두던 습관을 규칙으로 옮겨 두었다.

- 무엇부터 할지, 다음에 뭘 할지 막히면 `$next`
- 담당자 답이나 화면에서 본 문제는 그대로 붙여 넣는다 (loop)
- 에이전트가 위임을 제안하면 승인한다 (handoff)
- 마무리할 때 `$wrapup`

추론 강도는 `/model`에서 단계별로 고른다: 구조를 정하는 시작 단계와 원인을 찾기 어려운 버그는 높게, 작은 반복은 기본값으로.
