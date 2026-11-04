# SKHH

현업 담당자의 요청을 받아 웹 서비스나 작은 도구를 만들 때, AI 코딩 에이전트와 함께 쓰는 개인 작업 규칙입니다. 특정 프로젝트의 코드는 들어 있지 않습니다.

## 구성

| 파일 | 역할 |
| --- | --- |
| `AGENTS.md` | 에이전트가 항상 지키는 작업 규칙. 아래쪽 '해커톤 대비'는 해커톤 환경에 맞춰 덧붙인 규칙 |
| `.agents/skills/next` | 막혔을 때: 확인된 것과 가정을 정리하고 다음 한 걸음 제안 |
| `.agents/skills/wrapup` | 마무리: 점검, 결과 문서, 결정 요약 |

## 적용 방법

작업 폴더에서 아래 명령을 실행합니다. 이 저장소를 작업 폴더 안에 폴더째 받으면 규칙을 불러오지 못하니, `AGENTS.md`와 `.agents`가 작업 폴더 바로 아래에 오게 합니다.

```bash
rm -rf /tmp/skhh && git clone --depth 1 https://github.com/ytm220/SKHH /tmp/skhh && cp -r /tmp/skhh/.agents . && printf '\n' >> AGENTS.md && cat /tmp/skhh/AGENTS.md >> AGENTS.md
```

규칙은 세션을 시작할 때 불러옵니다. 실행 중이던 Codex가 있으면 `/quit`으로 닫고 작업 폴더에서 `codex`를 다시 실행합니다. `/skills`에서 next와 wrapup을 확인합니다.

## 쓰는 법

- 평소처럼 대화하며 진행합니다.
- 막히면 `$next`
- 마무리할 때 `$wrapup`
