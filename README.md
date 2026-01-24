# TruthGuard

TruthGuard is a Flask-based web application that helps users check whether a piece of text or a news article looks reliable, suspicious, or fake.  
It uses a mix of fast rule-based analysis and Google Gemini AI (if available) to give quick and useful feedback on online content.

The main goal of this project is to make misinformation detection simple, fast, and practical.

---

## What this project does

- Analyzes text or URLs for fake or misleading content
- Classifies content as **Reliable**, **Suspicious**, or **Fake**
- Shows confidence score, credibility, and sentiment
- Uses Gemini AI for deeper analysis and chat-based fact checking
- Works even without Gemini (fallback mode)
- Stores analysis history for logged-in users

---

## Features

- Fast fake news detection (instant results)
- Google Gemini AI integration for advanced analysis
- User login and registration system
- Dashboard with analysis history and stats
- Admin panel for user and content management
- AI chat assistant for misinformation-related questions
- URL content extraction and analysis
- Works fully offline from AI if API key is missing

---

## Tech Stack

- Python
- Flask
- SQLite (SQLAlchemy)
- Google Gemini API
- NLTK (sentiment analysis)
- HTML, CSS, Jinja2
- Flask-Login for authentication

---
