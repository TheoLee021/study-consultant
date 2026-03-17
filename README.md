# Study Consultant

> An evidence-based learning consultant for [Claude Code](https://claude.com/claude-code) that corrects study direction in real-time.

**[한국어 README](README.ko.md)**

## Why

Many people default to passive study methods — re-reading notes, organizing materials, making summaries. These feel productive but are cognitively shallow. Research calls this the **illusion of fluency**: recognizing information feels like knowing it, but exams require *recall* and *transfer*.

Study Consultant is a set of Claude Code skills and rules that act as a strict, evidence-based learning coach. It corrects study direction based on three learning science principles:

1. **Retrieval Practice** — Testing yourself is 2-3x more effective than re-reading
2. **Desirable Difficulty** — If studying feels easy, learning probably isn't happening
3. **Transfer-Appropriate Processing** — Study the way you'll be tested

## How It Works

### Skills

| Skill | Purpose |
|-------|---------|
| `/study` | Main entry point. Always-on consultant during study sessions. |
| `/diagnose` | 3-level understanding test: Retrieval → Connection → Application |
| `/study-plan` | Weekly study plan based on exam schedule and mastery levels |
| `/study-review` | Weekly review with pattern detection and metacognition feedback |

### Automatic Rules

The system automatically:
- Checks your study plan and review queue at session start
- Blocks material creation when retrieval practice should come first
- Judges whether your proposed activity matches your current learning stage
- Alerts you when weekly review is overdue
- Detects missing plans and redirects you

### Learning Cycle

The system enforces a structured learning cycle with language transition support (for non-native English speakers studying in English):

```
1. First Exposure    → Read/understand in native language
2. Native Retrieval  → Recall concepts in native language (must pass)
3. English Retrieval → Recall concepts in English (must pass)
4. Application       → Problem solving in English
5. Exam Prep         → English retrieval + problems only
```

### Spaced Repetition

Topics are automatically tracked with intervals: D+1 → D+3 → D+7 → D+14 → D+30. Diagnosis results adjust the schedule (fail = reset, strong pass = skip ahead).

## Setup

### Prerequisites

- [Claude Code](https://claude.com/claude-code) installed

### Installation

1. Clone this repo into your study project directory:

```bash
git clone https://github.com/TheoLee021/study-consultant.git
cd study-consultant
```

2. Start a Claude Code session and run:

```
/study
```

That's it. The system will detect it's the first run (Cold Start) and walk you through everything:
- Collecting your courses and exam dates (auto-saved to `CLAUDE.md`)
- Setting your goals
- Self-assessing your current level per course
- Running your first diagnostic test
- Creating your first weekly plan

### Customization

**For your courses:** Edit `CLAUDE.md` with your course names, exam dates, and any course-specific notes. Create a Table of Contents file for each course (e.g., `CourseName/CourseName_TableOfContents.md`) listing all topics.

## State Files

All state is stored as plain markdown in `study-consultant/`:

| File | Purpose | Updated By |
|------|---------|------------|
| `goals.md` | Annual/quarterly/monthly goals | `/study-plan`, Cold Start |
| `study-plan.md` | Weekly plan with expiry date | `/study-plan`, `/study-review` |
| `mastery.md` | Per-topic understanding level | `/diagnose` |
| `spaced-queue.md` | Spaced repetition schedule | `/study`, `/diagnose` |
| `study-log/YYYY-MM-DD.md` | Daily session logs | `/study` |
| `feedback/YYYY-MM.md` | Weekly + monthly feedback | `/study-review` |

## Design

See [docs/design-spec.md](docs/design-spec.md) for the full system design specification.

## License

MIT
