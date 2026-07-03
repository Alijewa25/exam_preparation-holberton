# 📋 Exam Preparation — Study Guide

**Scope:** Linux Shell · Git/GitHub · Python (Basics → OOP) · Backend · REST API · Flask · SQL · Database
**Based on:** Mentor session — topic categorization by learning source
**Repository files referenced:** `001` – `014`

---

## 🎯 Exam Scope

### ✅ In scope
All topics listed in the source breakdown below (Sections 1–3).

### ❌ Out of scope
| Topic | Status | Note |
|---|---|---|
| Python — Test Driven Development (TDD) | **Excluded** | Confirmed directly by mentor: *"Python test driven development olmayacaq."* No TDD-specific preparation needed for this exam. |

> Keep this section updated if the mentor confirms additional exclusions or inclusions.

---

## 🗂️ Source Breakdown

Topics are grouped by **where/how they were learned**, since each source implies a different preparation method (see [Preparation Method](#-preparation-method-by-source) below).

### 1️⃣ Holberton Tasks
*Learned through hands-on platform tasks.*

| Topic | Notes File |
|---|---|
| Linux Shell | `001-linux-shell.md` |
| Git / GitHub | `002-git-basics.md` |
| Python (Basics → OOP) | `003`–`009` (conditionals & loops, functions, lists, dictionaries, error handling, OOP basics, OOP advanced) |

### 2️⃣ Intranet Reading
*Theoretical material — read from Holberton intranet, no hands-on task attached.*

| Topic | Notes File |
|---|---|
| Backend — General Knowledge, Paradigms | `013-Extra-topics.md` (Backend section) |
| API — Paradigms | `011-RestAPI.md` |
| Flask API — Building an API with Flask | `012-Flask.md` |

### 3️⃣ Discord Tasks
*Practical exercises solved as a group, mentor-led, on Discord.*

| Topic | Notes File |
|---|---|
| REST | `011-RestAPI.md` |
| SQL — Queries | `010-sql-database.md` |
| Database — Concepts | `010-sql-database.md` |

---

## 📖 Preparation Method by Source

| Source | Method |
|---|---|
| **Holberton Tasks** | Complete the task hands-on on the platform first. Then self-test using the matching `.md` file — don't skip straight to Q&A. |
| **Intranet Reading** | Read the full intranet page, write a 2–3 sentence summary in your own words, then answer the matching `.md` file's questions. Reading alone is not sufficient — the exam expects "explain this" style answers. |
| **Discord Tasks** | These were already solved once. The goal now is explaining **why** the solution works, not recalling the exact code. Review the relevant sections of `014-code-analysis-questions.md` closely. |

---

## 🔁 Standard Study Workflow

Apply this 4-step process to every topic, in order:

1. **Prepare per source** — complete the Holberton task / read the intranet page / revisit the Discord task.
2. **Open the matching notes file** (`001`–`014`) — attempt each question yourself before checking the written answer.
3. **Hand-write code examples** — no copy-pasting, especially from `014-code-analysis-questions.md`.
4. **Flag uncertain questions** — revisit flagged questions the day before the exam.

---

## ⏱️ Priority Order (if time is limited)

1. **Python (incl. OOP)** — highest weight; both syntax and code-reading questions come from here.
2. **Flask API** — theoretical + practical (routing, request/response) questions likely.
3. **SQL / Database** — query-writing and concept questions combined.
4. **Git / GitHub** — command sequences and conceptual questions.
5. **Linux Shell** — usually short, direct-answer questions.
6. **Backend (general/paradigms)** — theoretical, typically definition/comparison questions.

---

## ✅ Final Review Checklist

- [ ] Reviewed every question in `001`–`014` at least once
- [ ] All Holberton tasks show **"passed"** status
- [ ] Written personal summaries exist for all Intranet Reading topics
- [ ] Can explain every code snippet in `014-code-analysis-questions.md` (what it does, why)
- [ ] Can explain the `app.py` / `service.py` / `models.py` separation in Flask
- [ ] Can read a combined `JOIN` + `GROUP BY` + `HAVING` SQL query fluently
- [ ] Confirmed with mentor: no further scope changes since last update

---

*Maintained as the master reference for exam preparation. Update the Exam Scope section whenever the mentor confirms new inclusions/exclusions.*