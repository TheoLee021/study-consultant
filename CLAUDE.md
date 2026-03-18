# Study Consultant - Project Context

## Course Schedule

<!-- Fill in your own courses and exam dates -->

| Course | Exam | Date | Notes |
|--------|------|------|-------|
| Example 101 | Final | YYYY-MM-DD | Example Course |

## Study Consultant System

An evidence-based learning consultant that corrects study direction in real-time.

**Skills:**
- `/study` — Always-on consultant mode (main entry point)
- `/diagnose` — 3-level understanding diagnosis
- `/study-plan` — Weekly study plan creation
- `/study-review` — Weekly review + feedback

**State Files:** `study-consultant/`
- `goals.md` — Annual/quarterly/monthly goals
- `study-plan.md` — Weekly plan
- `mastery.md` — Per-topic understanding level (single source of truth)
- `spaced-queue.md` — Spaced repetition queue
- `study-log/` — Daily session logs
- `feedback/` — Weekly + monthly feedback

**Rules:** `.claude/rules/learning-consultant.md` (always active)

**Design Spec:** `docs/design-spec.md`

## 워크플로우
- main에 직접 push 금지. 브랜치를 만들어서 PR로 보낼 것. 사용자가 직접 리뷰하고 머지.
