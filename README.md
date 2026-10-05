# TruthGuard: Fake News Detection & Content Verification

A full-stack web application that checks whether a news article or claim looks **reliable, suspicious or fake**, explains why, and lets users ask follow-up questions to **TruthBot**, an AI assistant. Built during my **Python internship at Infosys Springboard (Internship 6.0)**, December 2025 – February 2026, and delivered across four milestones.

## Features
- **Paste text or a URL:** articles are fetched and cleaned with Requests + BeautifulSoup.
- **Credibility verdict:** `RELIABLE`, `SUSPICIOUS` or `FAKE`, with a confidence score and the key findings behind it.
- **NLP signals:** sentiment (NLTK VADER), sensationalism (exclamation marks, ALL-CAPS words, clickbait phrases) and credibility indicators (sourcing such as "according to", official reports, studies).
- **TruthBot:** a Google Gemini chatbot that answers questions about the content and about spotting misinformation. Without an API key it falls back to built-in answers.
- **Accounts and history:** sign-up/login, a personal dashboard, past analyses and a detail view for each.
- **Admin panel** (Milestone 4): manage users and roles, activate/deactivate accounts, review all analyses.
- **Fast responses:** results are cached and saved to the database in a background thread.

## How the verdict is calculated
Each text gets three scores on a 0–10 scale:

| Signal | Raises it | Lowers it |
|---|---|---|
| Sensationalism | `!!!`, ALL-CAPS words, clickbait phrases | calm, factual wording |
| Credibility | named sources, reports, studies, officials | no attribution, strong emotional tone |
| Sentiment | | extreme positive/negative tone (VADER compound score) |

They are combined into a single score from 0 to 1: **≥ 0.7 → RELIABLE**, **0.4 – 0.7 → SUSPICIOUS**, **< 0.4 → FAKE**.

| Example input | Verdict | Sensationalism | Credibility |
|---|---|---|---|
| "SHOCKING!!! Doctors HATE this one trick, they don't want you to know the TRUTH…" | SUSPICIOUS (64%) | 3.0 | 4.5 |
| "According to a report published by the World Health Organization… officials said, citing peer-reviewed research." | RELIABLE (78%) | 0.0 | 8.8 |

> TruthGuard is a rule-based NLP assistant for spotting warning signs, not a fact-checking service. Always verify important claims with trusted sources.

## Milestones
| Milestone | What was delivered |
|---|---|
| 1 | Flask app skeleton, user registration and login, database models |
| 2 | Analysis engine, dashboard, analysis history, profile, about and contact pages |
| 3 | Analysis detail view and the first admin dashboard |
| 4 | Full admin panel (users, roles, analyses), TruthBot improvements, Gemini integration |

Each folder is a complete, runnable snapshot of the app at that milestone. **Milestone 4 is the final version.**

## Run locally
```bash
cd "Milestone 4"
pip install -r requirements.txt
copy .env.example .env      # macOS/Linux: cp .env.example .env, then edit the values
python app.py               # open http://127.0.0.1:5000
```
- On first start an admin account `admin@truthguard.com` is created with `ADMIN_PASSWORD` from `.env` (or a random password printed in the terminal).
- `GEMINI_API_KEY` is optional; without it TruthBot uses its built-in answers.
- Set `FLASK_DEBUG=1` only while developing. The server listens on `127.0.0.1` unless you set `HOST`.

## Tech stack
Python · Flask · Flask-SQLAlchemy · Flask-Login · SQLite · NLTK (VADER) · Requests · BeautifulSoup · Google Gemini API · Bootstrap · Jinja2 · HTML/CSS/JavaScript

## Project structure
```
Milestone 1 … Milestone 4/
  app.py              Flask app: models, detector, TruthBot, routes
  templates/          Jinja2 pages (admin/ in Milestones 3–4)
Milestone 4/
  requirements.txt    Python dependencies
  .env.example        settings template (copy to .env)
```

---
**Krish Mehta** · [krishmehta.xyz](https://www.krishmehta.xyz) · [LinkedIn](https://www.linkedin.com/in/-krish-mehta-01-05-/) · MIT License
