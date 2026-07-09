# Level 1 Job-Application Workflow

A simple, safe, repeatable workflow for tracking job applications and generating
tailored CVs and cover letters with an AI assistant — without leaking any personal data.

This guide is generic. Anyone can follow it. Replace every `[placeholder]` with your own
information as you go.

---

## 1. What this workflow gives you

- A private folder per application with your fit assessment, strategy, questions, and cover letter.
- One tracker file (CSV) with a row per application.
- A repeatable process: paste a job description → get an honest fit review → tailor materials → track it.

## 2. The two-layer idea (public vs private)

| Layer | Examples | Committed to Git? |
|-------|----------|-------------------|
| **Templates / docs** (this folder, `templates/`) | `*.example.md`, `*.example.csv` | ✅ Yes — safe to share, no personal data |
| **Your real data** | `applications/`, `jds/`, `cv.md`, `job-applications-tracker.csv` | ❌ No — git-ignored, stays on your machine |

The rule: **templates are public, your filled-in copies are private.** Keep it that way and
your name, email, phone, and application history never reach a public repository.

## 3. First-time setup

1. Copy the tracker template to a private working file:
   ```bash
   cp templates/job-applications-tracker.example.csv job-applications-tracker.csv
   ```
2. Make sure these paths are in `.gitignore` (so your data stays private):
   ```gitignore
   applications/
   jds/*
   cv.md
   config/profile.yml
   job-applications-tracker.csv
   job-applications-tracker.xlsx
   ```
3. Create your CV as `cv.md` and your profile at `config/profile.yml` (see the project's
   onboarding). These are private.

## 4. Per-application folder

For each job, create a folder under `applications/` named `company-role` (lowercase, hyphenated):

```
applications/
  [company]-[role]/
    jd.md                 # the raw job description
    fit-assessment.md     # honest HR fit assessment + score 0–100
    tailoring-strategy.md # how the CV/cover letter are tailored to this JD
    questions.md          # questions to answer before tailoring, plus your answers
    cover-letter.md       # tailored cover-letter draft
    notes.md              # recruiter contacts, deadlines, follow-ups
```

Starter versions of each file live in `templates/application-folder-template/`. Copy them
and drop the `.example` from the name.

## 5. The 9-step workflow (every time you paste a JD)

1. **Paste the JD** (text or URL) to the AI.
2. AI **reads** your `cv.md` and profile files.
3. AI gives an **honest HR fit assessment** — strengths, gaps, realism (not just positives).
4. AI gives a **realistic score from 0 to 100** with reasoning.
5. AI tells you **what you're missing** and **which CV bullets are weak or too vague**.
6. AI asks the **questions** it needs before tailoring.
7. You answer → AI drafts a **tailored CV + cover letter** and shows them for your approval.
8. On approval, materials are saved to `applications/[company]-[role]/` and the JD to `jds/`.
9. AI adds/updates a row in `job-applications-tracker.csv`.

**Safety:** Nothing is ever submitted to an employer automatically. The final "Submit" on any
application is always your own click.

## 6. Tracker columns (21)

Company, Role, Location, Work model, Job type, Source, Date found, Date applied, Status,
Fit score, Main strengths, Main gaps, CV generated, Cover letter generated, Interview date,
Rejection date, Accepted date, Follow-up date, Short description, Notes, Application folder path.

## 7. Allowed statuses (use exactly one)

`Interested` · `JD saved` · `Fit assessed` · `Questions pending` · `CV generated` ·
`Cover letter generated` · `Applied` · `Interview` · `Rejected` · `Accepted` · `Withdrawn`

## 8. Conventions

- Dates as `YYYY-MM-DD`; leave empty until they happen.
- Fit score is a number 0–100.
- Quote free-text CSV fields (strengths, gaps, notes, description) so commas don't break the file.
- Never put fabricated skills, metrics, or language levels in a CV — reformulate and emphasize,
  but only what is true and backed by your own CV or things you have stated.

## 9. Honesty note (read this)

An AI can make a weak application *sound* strong, but that backfires in interviews. Use this
workflow to present your real profile in its best, truthful light — and to decide honestly
which roles are worth applying to. A focused application to a good-fit role beats a generic
blast to fifty.
