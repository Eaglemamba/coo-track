# COO-Track Personal Operating System

A private, single-user operating system for an Operations Director transitioning to COO within five years. Built for clarity, not productivity theater.

This system is designed for David — Operations Director at a pharmaceutical CDMO specializing in aseptic fill-finish operations, with a decade of experience in injectable biologics, monoclonal antibodies, vaccines, and QS-21 adjuvant systems.

---

## How This System Works

This is not software. It is a set of structured rituals, frameworks, and reflection tools stored as plain text. You interact with it by opening files, writing in them, and letting the patterns compound over time.

The system operates on five cadences. Each builds on the last.

### Daily — 5 minutes

1. Open `reviews/daily/` and create a new file: `YYYY-MM-DD.md`
2. Copy the template from the existing `_template.md` in that folder
3. Fill in: energy level, one operational win, one leadership moment, one thing to delegate, tomorrow's priority, and any content-worthy insight
4. Done. Do not overthink this.

### Weekly — 30 minutes

1. Open `reviews/weekly/` and create a new file: `YYYY-Www.md` (e.g., `2026-W08.md`)
2. Review the week's daily check-ins before starting
3. Work through the weekly template: signal vs. noise, cross-functional touchpoints, stakeholder investments, time leaks, strategic insights, content pipeline
4. Update `tracking/stakeholder_map.md` if any relationships shifted
5. Update `tracking/content_pipeline.md` if any ideas matured

### Monthly — 1 hour

1. Open `reviews/monthly/` and create: `YYYY-MM.md`
2. Review that month's weekly reviews
3. Work through: cross-functional competency development, delegation progress, commercial learning, key decisions and outcomes, Tooling Layer progress
4. Update `tracking/delegation_log.md` and `tracking/commercial_learning.md`
5. Update `frameworks/cross_functional_competency.md` with any movement
6. Check `frameworks/coo_readiness_assessment.md` — note any gaps that closed or widened

### Quarterly — Half day

1. Open `reviews/quarterly/` and create: `YYYY-Qq.md`
2. Review all monthly reviews from the quarter
3. Deep work session: goal progress, COO-readiness gap analysis, energy vs. impact analysis, course corrections
4. Review AIAudit data for AI leverage patterns
5. Run one interview script from `interviews/` (rotate quarterly)
6. Update `goals/1_year.md` and `goals/5_year_coo.md`
7. Update `tracking/decision_journal.md` with the quarter's significant decisions

### Annually — Full day

1. Block a full day. No meetings. No email.
2. Open `reviews/annual/` and create: `YYYY.md`
3. Run the full annual review framework from `frameworks/annual_review.md`
4. Run `interviews/past_year_reflection.md` and `interviews/future_self_interview.md`
5. Update `frameworks/vivid_vision.md`, `frameworks/ideal_life_costing.md`, `frameworks/life_map.md`
6. Honest COO-readiness assessment
7. Write the ten-year letter
8. Set clear intent for the year ahead
9. Update `goals/` files for the new year
10. Update `north_star.md` if your direction has evolved

---

## Personalizing This System (Under 15 Minutes)

1. **Open `north_star.md`** — Replace placeholder text with your actual current vision. 3 minutes.
2. **Open `goals/1_year.md`** — Fill in your actual goals for this year. 3 minutes.
3. **Open `tracking/stakeholder_map.md`** — Add your actual key stakeholders. 3 minutes.
4. **Open `frameworks/cross_functional_competency.md`** — Self-assess your current levels. 3 minutes.
5. **Open `tracking/content_pipeline.md`** — Add any ideas already in your queue. 3 minutes.

Everything else can be personalized as you use it. The system improves through use, not configuration.

---

## Uploading Past Documents

Place documents in the appropriate `uploads/` subfolder:
- `uploads/performance_reviews/` — Annual or mid-year reviews
- `uploads/project_retrospectives/` — Project post-mortems, lessons learned
- `uploads/leadership_feedback/` — 360 feedback, peer reviews, skip-level notes
- `uploads/notes/` — Anything else relevant

Then use Claude to extract patterns:

> "Read the documents in uploads/performance_reviews/ and summarize: repeated strengths, recurring blind spots, development themes, and leadership gaps. Store the synthesis in memory.md."

The system will reference `memory.md` in future check-ins and reviews.

---

## File Map

| File | Purpose |
|------|---------|
| `principles.md` | Non-negotiable operating principles |
| `north_star.md` | Current direction and purpose |
| `mental_models.md` | Thinking frameworks that guide decisions |
| `memory.md` | Accumulated insights from reflections and uploads |
| `frameworks/` | Structured frameworks for deep reflection |
| `interviews/` | Self-interview scripts for leadership development |
| `reviews/` | Templates for all five cadences |
| `goals/` | 1-year, 3-year, and 5-year goal documents |
| `tracking/` | Ongoing logs for decisions, stakeholders, delegation, learning, content |
| `uploads/` | Storage for past documents to be analyzed |

---

## Design Assumptions

This system was built with these assumptions. Adjust as needed:

- You have 5 minutes per day, 30 minutes per week, 1 hour per month, half a day per quarter, and one full day per year for reflection
- You operate in a GMP-regulated pharmaceutical environment where decisions carry compliance implications
- You are building toward COO within 5 years, which requires cross-functional breadth beyond manufacturing operations
- You produce bilingual content (English and Traditional Chinese) for LinkedIn and Substack
- You use Claude as a primary AI tool alongside Gemini for specific workflows
- Your existing tools (AIAudit, Articulator, dual-AI deviation system) will evolve alongside this system
- You value capturing thinking in motion over polished summaries
- You believe timing matters as much as logic in organizational change

---

## Philosophy

This system exists to create structured extraction discipline for leadership insights. Left unstructured, operational leaders optimize for execution at the expense of reflection. The cadences are forcing functions — they exist because the work will always feel more urgent than the thinking.

The 50% output rule applies here: time saved through AI and automation flows into creation (reflection, strategy, development), not consumption. This system is how you enforce that.

*"The value isn't in AI generating answers. It's in AI providing structured feedback on your answers."*
