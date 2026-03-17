# Study Consultant

> [Claude Code](https://claude.com/claude-code)용 근거 기반 학습 컨설턴트. 실시간으로 학습 방향을 교정합니다.

**[English README](README.md)**

## 왜 필요한가

많은 사람들이 수동적 학습 방법에 의존한다 — 노트 다시 읽기, 자료 정리, 요약 작성. 생산적인 느낌이 들지만 인지적으로 얕은 처리다. 학습과학에서는 이를 **유창성 착각(illusion of fluency)**이라 한다: 정보를 재인식하는 것이 아는 것처럼 느껴지지만, 시험은 *인출(recall)*과 *전이(transfer)*를 요구한다.

Study Consultant는 Claude Code 스킬과 규칙 세트로, 엄격한 근거 기반 학습 코치 역할을 한다. 세 가지 학습과학 원칙에 기반해 공부 방향을 교정한다:

1. **인출 연습 (Retrieval Practice)** — 자기 테스트는 다시 읽기보다 2-3배 효과적
2. **바람직한 어려움 (Desirable Difficulty)** — 공부가 쉽게 느껴지면 학습이 안 되고 있을 가능성
3. **전이 적절 처리 (Transfer-Appropriate Processing)** — 시험 방식대로 공부해야 한다

## 사용법

### 스킬

| 스킬 | 용도 |
|------|------|
| `/study` | 메인 진입점. 공부 중 상시 컨설턴트. |
| `/diagnose` | 3단계 이해도 진단: 인출 → 연결 → 응용 |
| `/study-plan` | 시험 일정 + 이해도 기반 주간 계획 |
| `/study-review` | 주간 리뷰 + 패턴 감지 + 메타인지 피드백 |

### 자동 규칙

시스템이 자동으로:
- 세션 시작 시 학습 계획과 복습 큐 확인
- 인출 연습이 선행되어야 할 때 자료 생성 차단
- 현재 학습 단계에 제안된 활동이 적절한지 판단
- 주간 리뷰가 밀렸으면 알림
- 계획이 없으면 감지 후 리다이렉트

### 학습 사이클

구조화된 학습 사이클 + 언어 전환 지원 (영어로 수업받는 비영어권 학생용):

```
1. 첫 노출      → 모국어로 읽기/이해
2. 모국어 인출   → 모국어로 개념 인출 (통과 필수)
3. 영어 인출     → 영어로 개념 인출 (통과 필수)
4. 응용         → 영어로 문제 풀이
5. 시험 준비     → 영어 인출 + 문제만
```

### 간격 반복

주제별 자동 추적: D+1 → D+3 → D+7 → D+14 → D+30. 진단 결과에 따라 일정 조정 (실패 = 리셋, 강한 통과 = 스킵).

## 설치

### 필수 조건

- [Claude Code](https://claude.com/claude-code) 설치

### 설치 방법

1. 이 레포를 학습 프로젝트 디렉토리에 클론:

```bash
git clone https://github.com/TheoLee021/study-consultant.git
cd study-consultant
```

2. Claude Code 세션을 시작하고 실행:

```
/study
```

끝. 첫 실행(Cold Start)이 감지되면 모든 것을 자동으로 안내:
- 과목과 시험 일정 수집 (`CLAUDE.md`에 자동 저장)
- 목표 설정
- 과목별 현재 수준 자가 진단
- 첫 번째 진단 테스트
- 첫 주간 계획 수립

### 커스터마이징

**과목 설정:** `CLAUDE.md`에 과목명, 시험 일정, 과목별 메모를 입력. 각 과목의 목차 파일을 생성 (예: `CourseName/CourseName_TableOfContents.md`).

## 설계 문서

전체 시스템 설계: [docs/design-spec.md](docs/design-spec.md)

## 라이선스

MIT
