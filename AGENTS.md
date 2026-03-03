# AGENTS.md

## Purpose
This file is the operating guide for AI agents working in this repository. It captures assignment context, technical constraints, grading priorities, and quality guardrails so every task is executed with clear scope and consistent standards.

## Project Assignment Overview
This project is the CS205 Final Project: AI-Assisted Feature Development.  
You are extending a starter Mood Tracking web app into a broader health and wellness platform by collaborating with AI coding agents.

Core objective:
- Plan, build, and ship meaningful new features on top of the base app.
- Demonstrate effective AI collaboration, not blind code generation.
- Deliver working software that is polished, testable, and demo-ready.

## Submission Requirements
Use `README.md` as source of truth. Required deliverables:
- Push final code to GitHub and add `@Patchwork53` as a collaborator.
- Include an AI usage summary (for example `AI_USAGE.md`) that states:
  - Which AI tools were used.
  - How they were used (planning, coding, debugging, etc.).
  - Limitations/issues encountered.
- Prepare an in-person presentation with a live demo.
- Follow due date in the course syllabus.

## Grading Rubric (What to Optimize For)
Prioritize work against these exact weights:
- Feature Depth: 30%
- Feature Breadth: 25%
- Presentation & Demo: 20%
- Code Quality & Security: 15%
- AI Tool Usage: 10%

Bonus opportunities:
- Mobile App (Android): +10%
- Mobile App (iOS): +10%
- Deployed/Hosted: +5%

## Codebase Overview
Primary app structure:

```text
src/
├── App.jsx                           # Top-level layout and tab navigation
├── main.jsx                          # React entrypoint
├── index.css                         # Tailwind + global styles
├── context/
│   └── HealthDataContext.jsx         # Central state/actions for mood data
├── modules/
│   └── MoodTracker.jsx               # Mood entry input/list/delete UI
├── components/
│   ├── DailyGraph.jsx                # Today's mood line chart
│   ├── WeeklyGraph.jsx               # Last 7 days average mood bar chart
│   ├── HistoryView.jsx               # Grouped mood history by date
│   └── FileManager.jsx               # Import/export/auto-save file controls
└── utils/
    ├── helpers.js                    # Date formatting helpers
    ├── storage.js                    # localStorage persistence
    └── fileOperations.js             # File System Access API wrappers
```

Key non-src files:
- `README.md`: assignment details and rubric (source of truth).
- `package.json`: scripts and dependencies.
- `example-data.json`: sample import shape.

## Current App Features
The starter app currently provides:
- Mood logging on a 1-5 scale with automatic date/time timestamps.
- Daily mood chart for current day entries.
- Weekly chart for last 7 days average mood.
- Full history view organized by date.
- Data management via JSON import/export.
- Local persistence via browser `localStorage`.
- Optional file-based save/load using File System Access API.

## Data Model and Storage
Primary persisted shape:

```json
{
  "moodEntries": [
    {
      "id": 1705320000000,
      "mood": 4,
      "timestamp": "2024-01-15T12:00:00.000Z",
      "time": "12:00 PM",
      "date": "1/15/2024"
    }
  ]
}
```

Storage behavior:
- Local storage key: `healthTrackingData`.
- File handle info key: `healthTrackingFileHandle`.
- Data is loaded on startup and auto-saved when entries change.

## Tech Stack and Commands
Stack:
- React 18
- Vite 5
- Tailwind CSS 3
- Recharts 2

Standard commands:
- `npm install` - install dependencies.
- `npm run dev` - run local development server.
- `npm run build` - create production build.

## AI Agent Working Rules (Balanced)
For every task:
- Keep changes minimal, focused, and scoped to the request.
- Do not delete or overwrite unrelated code.
- Prefer small diffs over broad rewrites.
- State assumptions explicitly before implementing when needed.
- Validate with build/tests/manual checks appropriate to the change.
- Do not hardcode secrets or API keys in source.

Required task output contract (for each completed task):
- Scope statement.
- Planned file touch list.
- Implementation summary.
- Validation summary.
- Rubric-aligned impact note.

## AI Shortcomings to Watch For
Convert common AI failure modes into explicit checks:

Over-engineering detection:
- Reject unnecessary abstractions/helpers used once.
- Prefer direct, readable code over layered architecture.

Unnecessary defensive code:
- Validate at real boundaries (user input, API/file input).
- Avoid excessive guard clauses for impossible internal states.

Destructive edit risk:
- Never remove existing features unless explicitly requested.
- Review diffs to ensure no unrelated behavior regressions.

Outdated dependency/API risk:
- Verify new package/API recommendations against official docs.
- Avoid deprecated patterns and stale package advice.

Secret leakage risk:
- Never commit API keys, tokens, or private credentials.
- Use environment variables and keep secret files out of version control.

## Security and Safety Checklist
Before finalizing changes:
- No secrets committed.
- User/file inputs are validated at boundaries.
- No obvious XSS/injection vectors introduced.
- No destructive commands run unless explicitly requested.
- Existing functionality still works after edits.

## Task Definition of Done
A task is done only when all applicable items are satisfied:

Feature Depth (30%):
- Feature works end-to-end and handles realistic edge cases.

Feature Breadth (25%):
- Adds meaningful, non-trivial functionality (not cosmetic-only).

Presentation & Demo (20%):
- Change is demonstrable and easy to explain live.

Code Quality & Security (15%):
- Code is clear, maintainable, and free of obvious security issues.

AI Tool Usage (10%):
- AI assistance and human corrections are documented clearly.

## Session Logging Requirement
Every AI-assisted work block must be logged in [SESSIONS.md](./SESSIONS.md) using the required template fields.  
Logs must capture what was built and how AI was used so presentation prep is straightforward.

## Quick Start for Any New Task
1. Read `README.md`, this file, and relevant feature files before editing.
2. Define scope and list expected files to touch.
3. Implement smallest useful increment.
4. Validate (`npm run build`, plus targeted manual checks).
5. Summarize rubric impact and limitations.
6. Add/update session entry in [SESSIONS.md](./SESSIONS.md).
