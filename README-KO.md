# Claude Code 치트 시트

> **Claude Code 마스터를 위한 완벽 가이드 - 몇 분 만에 초보에서 전문가로!**

Claude Code를 광범위하게 테스트한 후, 시간 낭비 없이 기본 사용자에서 고급 사용자로 나아갈 수 있는 포괄적인 치트 시트를 개발했습니다. Claude Code를 처음 접하는 분이든 고급 기능을 마스터하고 싶은 분이든, 이 가이드가 모든 것을 다룹니다.

## 빠른 시작

```bash
# Windows 사용자
wsl

# Claude Code 설치
npm install -g @anthropic-ai/claude-code

# 대화형 REPL 실행
claude

# 버전 확인
claude --version
```

## 📚 목차

- 🟢 **레벨 1: 기본 명령어**
- 🟡 **레벨 2: 중급 명령어**
- 🟠 **레벨 3: 고급 명령어**
- 🔴 **레벨 4: 전문가 명령어**
- 🔵 **레벨 5: 파워 유저 명령어**
- 🟣 **레벨 6: 마스터 명령어**
- 🟤 **레벨 7: 워크플로우 자동화**
- ⚫ **레벨 8: 통합 및 생태계**
- ⚪ **레벨 9: 성능 및 최적화**
- 🔘 **레벨 10: 엔터프라이즈 및 프로덕션**
- 🤝 **기여하기**
- 📄 **라이선스**

### 페이지

- 🤖 **[서브에이전트](subagents.md)** - 특정 개발 작업을 위한 전문화된 AI 에이전트

---

## 🟢 레벨 1: 기본 명령어

시작하기 위한 필수 명령어

### 설치 및 시작하기

```bash
# Claude Code 설치
curl -sL https://install.anthropic.com | sh

# 대화형 REPL 시작
claude

# 초기 프롬프트와 함께 시작
claude "이 프로젝트 요약해줘"

# 버전 확인
claude --version

# 최신 버전으로 업데이트
claude update
```

### 기본 탐색

```bash
/help                     # 도움말 및 사용 가능한 명령어 표시
/exit                     # REPL 종료
/clear                    # 대화 기록 지우기
/config                   # 구성 패널 열기
/doctor                   # Claude Code 설치 상태 확인
```

### 기본 파일 작업

```bash
# 출력 모드 (SDK) - 실행 후 종료
claude -p "이 함수 설명해줘"

# 파이프된 콘텐츠 처리
cat logs.txt | claude -p "설명해줘"

# 가장 최근 대화 계속하기
claude -c

# SDK를 통해 계속하기
claude -c -p "타입 에러 확인해줘"
```

### 세션 관리

```bash
# ID로 세션 재개
claude -r "abc123" "이 PR 완료해줘"

# 플래그로 재개
claude --resume abc123 "쿼리"

# 세션 계속하기
claude --continue
```

### 키보드 단축키

```bash
Ctrl+C                    # 현재 작업 취소
Ctrl+D                    # Claude Code 종료
Tab                       # 자동 완성
Up/Down                   # 명령어 기록 탐색
```

## 🟡 레벨 2: 중급 명령어

구성 및 모델 관리

### 모델 구성

```bash
# 모델 전환
claude --model sonnet                    # Sonnet 모델 사용
claude --model opus                      # Opus 모델 사용
claude --model claude-sonnet-4-20250514  # 특정 모델 버전 사용
```

### 디렉토리 관리

```bash
# 추가 작업 디렉토리 추가
claude --add-dir ../apps ../lib

# 디렉토리 경로 검증
claude --add-dir /path/to/project
```

### 출력 형식

```bash
# 다양한 출력 형식
claude -p "쿼리" --output-format json
claude -p "쿼리" --output-format text
claude -p "쿼리" --output-format stream-json

# 입력 형식
claude -p --input-format stream-json
```

### 세션 제어

```bash
# 대화 턴 제한
claude -p --max-turns 3 "쿼리"

# 상세 로깅
claude --verbose

# 세션 비용 및 기간
/cos                      # 총 비용 및 기간 표시
```

## 🟠 레벨 3: 고급 명령어

도구 및 권한 관리

### 도구 관리

```bash
# 프롬프트 없이 특정 도구 허용
claude --allowedTools "Bash(git log:*)" "Bash(git diff:*)" "Write"

# 특정 도구 비허용
claude --disallowedTools "Bash(rm:*)" "Bash(sudo:*)"

# 특정 도구 권한 프롬프트
claude -p --permission-prompt-tool mcp_auth_tool "쿼리"

# 모든 권한 프롬프트 건너뛰기 (위험)
claude --dangerously-skip-permissions
```

### 슬래시 명령어 - 세션 관리

```bash
/compact [지시사항]       # 선택적 지시사항으로 대화 요약
/clear                    # 대화 기록 및 컨텍스트 재설정
/exit                     # REPL 종료
/help                     # 사용 가능한 명령어 표시
/config                   # 구성 패널 열기
```

### 슬래시 명령어 - 시스템

```bash
/doctor                   # 설치 상태 확인
/cos                      # 현재 세션의 비용 및 기간 표시
/ide                      # IDE 통합 관리
```

## 🔴 레벨 4: 전문가 명령어

MCP 및 고급 통합

### 모델 컨텍스트 프로토콜 (MCP)

```bash
# MCP 서버 구성
claude --mcp

# MCP 서버 관리 (슬래시 명령어를 통해)
/mcp                      # MCP 기능 액세스
```

### 고급 파이핑

```bash
# 복잡한 파이핑 작업
git log --oneline | claude -p "이 커밋들 요약해줘"
cat error.log | claude -p "근본 원인 찾아줘"
ls -la | claude -p "이 디렉토리 구조 설명해줘"
```

### 프로그래밍 방식 사용

```bash
# 스크립팅을 위한 JSON 출력
claude -p "코드 분석" --output-format json

# 실시간 처리를 위한 스트림 JSON
claude -p "대규모 작업" --output-format stream-json

# 일괄 처리
claude -p --max-turns 1 "빠른 쿼리"
```

## 🔵 레벨 5: 파워 유저 명령어

고급 워크플로우 및 자동화

### 사용자 정의 슬래시 명령어

```bash
# .claude/commands/에 사용자 정의 명령어 생성
# 예: .claude/commands/debug.md
/debug                    # 사용자 정의 디버그 명령어 실행
/test                     # 사용자 정의 테스트 명령어 실행
/deploy                   # 사용자 정의 배포 명령어 실행
```

### 복잡한 도구 조합

```bash
# 고급 도구 권한
claude --allowedTools "Bash(git:*)" "Write" "Read" \
       --disallowedTools "Bash(rm:*)" "Bash(sudo:*)"

# 여러 디렉토리 액세스
claude --add-dir ../frontend ../backend ../shared
```

### 성능 최적화

```bash
# 성능을 위한 컨텍스트 제한
claude -p --max-turns 5 "집중 쿼리"

# 컨텍스트 자주 지우기
/clear                    # 작업 간 더 나은 성능을 위해 사용

# 대화 압축
/compact "중요한 부분만 유지"
```

## 🟣 레벨 6: 마스터 명령어

전문가 자동화 및 사용자 정의 워크플로우

### 고급 구성

```bash
# 복잡한 모델 및 도구 구성
claude --model claude-sonnet-4-20250514 \
       --add-dir ../apps ../lib ../tools \
       --allowedTools "Bash(git:*)" "Write" "Read" \
       --verbose \
       --output-format json
```

### 자동화 스크립트

```bash
# 스크립트화된 Claude 상호작용
#!/bin/bash
claude -p "코드베이스 분석" --output-format json > analysis.json
claude -p "테스트 생성" --max-turns 3 --output-format text > tests.txt
```

### 고급 세션 관리

```bash
# 세션 ID 관리
SESSION_ID=$(claude -p "분석 시작" --output-format json | jq -r '.session_id')
claude -r "$SESSION_ID" "분석 계속"
```

### 복잡한 워크플로우

```bash
# 다단계 자동화
claude -p "프로젝트 구조 분석" | \
claude -p "개선 사항 제안" | \
claude -p "구현 계획 생성"
```

---

## 🟤 레벨 7: 워크플로우 자동화

고급 자동화 패턴 및 다단계 프로세스

### 자동화된 코드 리뷰 워크플로우

```bash
# 자동화된 PR 리뷰 프로세스
#!/bin/bash
git diff HEAD~1 | claude -p "이 PR의 보안 문제 검토" > security_review.md
git diff HEAD~1 | claude -p "성능 문제 확인" > performance_review.md
git diff HEAD~1 | claude -p "개선 사항 제안" > improvements.md
```

### 지속적 통합 통합

```bash
# CI/CD 파이프라인 통합
claude -p "테스트 커버리지 분석" --output-format json | jq '.coverage_percentage'
claude -p "커밋에서 릴리스 노트 생성" --max-turns 2 > RELEASE_NOTES.md
```

### 일괄 처리 워크플로우

```bash
# 여러 파일 처리
find . -name "*.js" -exec claude -p "이 파일의 버그 분석: {}" \; > bug_report.txt

# 자동화된 문서 생성
for file in src/*.py; do
    claude -p "$file의 독스트링 생성" --output-format text >> docs.md
done
```

---

## ⚫ 레벨 8: 통합 및 생태계

IDE 통합, Git 워크플로우 및 타사 도구 연결

### IDE 통합 명령어

```bash
# VS Code 통합
/ide vscode                # VS Code 통합 구성
/ide configure             # IDE 구성 설정

# 사용자 정의 IDE 명령어
claude --ide-mode "선택한 코드 설명"
claude --ide-mode "이 함수 리팩토링"
```

### Git 워크플로우 통합

```bash
# Git 훅 통합
claude -p "코드 품질을 위한 pre-commit 훅 생성" > .git/hooks/pre-commit

# 고급 Git 작업
git log --oneline -10 | claude -p "이 커밋들에서 변경로그 생성"
git diff --name-only | claude -p "이 커밋에서 변경된 내용 설명"
```

### 타사 도구 연결

```bash
# 데이터베이스 통합
mysql -e "SHOW TABLES" | claude -p "데이터베이스 구조 분석"

# Docker 통합
docker ps | claude -p "실행 중인 컨테이너 분석"
docker logs container_name | claude -p "로그에서 에러 찾기"
```

---

## ⚪ 레벨 9: 성능 및 최적화

고급 성능 튜닝, 리소스 관리 및 효율성 팁

### 메모리 및 리소스 관리

```bash
# 메모리 사용 최적화
claude -p --max-turns 1 "빠른 분석"      # 효율성을 위한 단일 턴
claude -p --compact-mode "최소 컨텍스트로 분석"

# 리소스 모니터링
/cos                       # 현재 세션 비용 확인
/doctor --performance      # 성능 진단
```

### 캐싱 및 최적화

```bash
# 효율적인 세션 재사용
claude -c "이전 분석 계속"                # 기존 컨텍스트 재사용
claude --cache-results "반복 작업"        # 일반 작업 캐시

# 병렬 처리
claude -p "작업 1" & claude -p "작업 2" & wait  # 병렬 실행
```

### 대규모 처리

```bash
# 대규모 코드베이스를 효율적으로 처리
claude --add-dir . --max-context 50000 "전체 프로젝트 분석"
claude --stream-output "대규모 데이터셋 처리" | head -100
```

---

## 🔘 레벨 10: 엔터프라이즈 및 프로덕션

프로덕션 준비 구성, 팀 워크플로우 및 엔터프라이즈 기능

### 팀 협업

```bash
# 공유 팀 구성
claude --config-file team-config.json "표준화된 분석"

# 팀 세션 공유
claude -r "team-session-id" "팀 토론 계속"
```

### 프로덕션 환경 설정

```bash
# 프로덕션 준비 구성
claude --production-mode \
       --security-enabled \
       --audit-logging \
       --max-turns 10 \
       "프로덕션 분석"
```

### 엔터프라이즈 보안

```bash
# 보안 중심 작업
claude --disallowedTools "Bash(rm:*)" "Bash(sudo:*)" "Bash(chmod:*)" \
       --audit-mode \
       --no-external-calls \
       "보안 코드 리뷰"
```

### 모니터링 및 규정 준수

```bash
# 감사 및 규정 준수
claude --audit-log /var/log/claude-audit.log "규정 준수 확인"
claude --compliance-mode "보안 규정 준수 분석"
```

## 명령어 참조 테이블

### CLI 명령어

| 명령어 | 설명 | 예제 |
|---------|-------------|---------|
| `claude` | 대화형 REPL 시작 | `claude` |
| `claude "쿼리"` | 프롬프트와 함께 REPL 시작 | `claude "이 프로젝트 설명해줘"` |
| `claude -p "쿼리"` | 출력 모드, 실행 후 종료 | `claude -p "함수 설명"` |
| `claude -c` | 최근 대화 계속하기 | `claude -c` |
| `claude -r "id" "쿼리"` | ID로 세션 재개 | `claude -r "abc123" "PR 완료"` |
| `claude update` | 최신 버전으로 업데이트 | `claude update` |
| `claude mcp` | MCP 서버 구성 | `claude mcp` |

### CLI 플래그

| 플래그 | 설명 | 예제 |
|------|-------------|---------|
| `--model` | 모델 지정 | `--model sonnet` |
| `--add-dir` | 작업 디렉토리 추가 | `--add-dir ../apps ../lib` |
| `--allowedTools` | 프롬프트 없이 도구 허용 | `--allowedTools "Bash(git:*)"` |
| `--disallowedTools` | 특정 도구 비허용 | `--disallowedTools "Bash(rm:*)"` |
| `--output-format` | 출력 형식 설정 | `--output-format json` |
| `--input-format` | 입력 형식 설정 | `--input-format stream-json` |
| `--max-turns` | 대화 턴 제한 | `--max-turns 3` |
| `--verbose` | 상세 로깅 활성화 | `--verbose` |
| `--continue` | 세션 계속하기 | `--continue` |
| `--resume` | 세션 재개 | `--resume abc123` |
| `--dangerously-skip-permissions` | 모든 권한 프롬프트 건너뛰기 | `--dangerously-skip-permissions` |

### 슬래시 명령어

| 명령어 | 설명 |
|---------|-------------|
| `/help` | 도움말 및 사용 가능한 명령어 표시 |
| `/exit` | REPL 종료 |
| `/clear` | 대화 기록 지우기 |
| `/config` | 구성 패널 열기 |
| `/doctor` | 설치 상태 확인 |
| `/cos` | 비용 및 기간 표시 |
| `/ide` | IDE 통합 관리 |
| `/compact [지시사항]` | 대화 요약 |
| `/mcp` | MCP 기능 액세스 |

### 키보드 단축키

| 단축키 | 작업 |
|----------|--------|
| `Ctrl+C` | 현재 작업 취소 |
| `Ctrl+D` | Claude Code 종료 |
| `Tab` | 자동 완성 |
| `Up/Down` | 명령어 기록 탐색 |

## 모범 사례

### 성능 팁

- 작업 간에 `/clear`를 자주 사용하세요
- `--max-turns`로 컨텍스트 제한하세요
- 긴 대화에는 `/compact` 사용하세요
- `--allowedTools`로 정확한 도구 지정하세요

### 보안 팁

- `--dangerously-skip-permissions` 사용을 피하세요
- 위험한 명령어에는 `--disallowedTools` 사용하세요
- 도구 권한을 정기적으로 검토하세요
- Claude Code를 최신 상태로 유지하세요

### 워크플로우 팁

- `.claude/commands/`에 사용자 정의 슬래시 명령어를 생성하세요
- 자동화에는 `--output-format json` 사용하세요
- 복잡한 워크플로우에는 명령어 파이핑을 사용하세요
- 장기 실행 작업에는 세션 ID를 사용하세요

## 레벨별 모범 사례

### 초급 모범 사례 (레벨 1-3)

- 기본 명령어로 시작하여 점진적으로 진행하세요
- `/help`를 자주 사용하여 새 기능을 발견하세요
- 복잡한 쿼리 전에 간단한 쿼리로 연습하세요
- 작업 간에 `/clear`로 세션을 집중하세요

### 중급 모범 사례 (레벨 4-6)

- 보안을 위해 도구 권한을 마스터하세요
- 자동화 스크립트에 JSON 출력을 사용하세요
- 고급 통합을 위해 MCP를 배우세요
- 반복 작업을 위한 사용자 정의 슬래시 명령어를 생성하세요

### 고급 모범 사례 (레벨 7-10)

- 반복 작업을 위한 자동화 워크플로우를 구현하세요
- 팀 협업을 위한 엔터프라이즈 기능을 사용하세요
- 성능을 모니터링하고 리소스 사용을 최적화하세요
- 프로덕션에서 보안 모범 사례를 따르세요

## 프로 팁 및 트릭

### 효율성 팁

- `Ctrl+C`를 사용하여 오래 실행되는 작업을 취소하세요
- 복잡한 구성을 위해 여러 플래그를 결합하세요
- 다단계 데이터 처리에 파이핑을 사용하세요
- 더 나은 성능을 위해 일반 작업을 캐시하세요

### 보안 프로 팁

- 위험한 명령어에는 항상 `--disallowedTools`를 사용하세요
- 프로덕션 환경에서 감사 로깅을 활성화하세요
- 도구 권한을 정기적으로 검토하세요
- 민감한 작업에는 `--security-enabled`를 사용하세요

### 워크플로우 프로 팁

- 일반적인 자동화 패턴을 위한 템플릿을 생성하세요
- 장기 실행 협업 작업에는 세션 ID를 사용하세요
- 자동화 스크립트에 적절한 에러 처리를 구현하세요
- 팀 공유를 위해 사용자 정의 워크플로우를 문서화하세요

## 일반적인 문제 해결

### 설치 문제

```bash
# 설치 확인
claude --version
claude /doctor

# 필요한 경우 재설치
npm uninstall -g @anthropic-ai/claude-code
npm install -g @anthropic-ai/claude-code
```

### 성능 문제

```bash
# 더 나은 성능을 위해 컨텍스트 지우기
/clear

# 컨텍스트 크기 제한
claude -p --max-turns 3 "집중 쿼리"

# 압축 모드 사용
/compact "필수 사항만 유지"
```

### 권한 문제

```bash
# 현재 권한 확인
claude --list-permissions

# 권한 재설정
claude --reset-permissions

# 특정 권한 구성
claude --allowedTools "Bash(git:*)" --disallowedTools "Bash(rm:*)"
```


## 리소스 및 추가 학습

더 많은 Claude Code 리소스는 Anthropic 공식 문서를 방문하세요

- [공식 Claude Code 문서](https://docs.anthropic.com/en/docs/claude-code)
- [Claude Code GitHub 저장소](https://github.com/anthropic-ai/claude-code)
- [Anthropic API 문서](https://docs.anthropic.com)
- [MCP 문서](https://docs.anthropic.com/en/docs/build-with-claude/mcp)
