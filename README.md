# AcademicGuard

AcademicGuard is an academic integrity risk detection platform that combines machine learning, behavioral analysis, and an interactive review dashboard for suspicious submissions.

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=for-the-badge&logo=fastapi&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=for-the-badge&logo=scikitlearn&logoColor=white)
![SHAP](https://img.shields.io/badge/SHAP-ff6b6b?style=for-the-badge)
![React](https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)

## Setup

### Run the ML service

```bash
cd backend
python -m venv .venv
.venv\Scripts\activate
pip install -r requirements-render.txt
python -m spacy download en_core_web_sm
python main.py
```

The API starts on `http://127.0.0.1:8000`.

### Run the client

```bash
cd frontend
npm install
npm run dev
```

The client starts on `http://127.0.0.1:5173`.

## Features

AcademicGuard analyzes submissions across 4 signal domains:

1. Writing stylometry
2. Submission timing behavior
3. Performance deviation
4. Risk scoring and explainability

The current prototype highlights 20 core features/signals:

1. `avg_sentence_length`
2. `type_token_ratio`
3. `avg_word_length`
4. `punctuation_density`
5. `passive_voice_rate`
6. `noun_ratio`
7. `verb_ratio`
8. `adj_ratio`
9. `flesch_reading_ease`
10. `stopword_ratio`
11. `hours_before_deadline`
12. `days_before_deadline`
13. `submission_hour`
14. `is_night_submission`
15. `weekend_submission`
16. `timing_z_score`
17. `pattern_shift`
18. `z_score`
19. `grade_jump`
20. `vs_class_delta`

The model layer uses Isolation Forest for anomaly detection and SHAP-style contribution views to explain why a submission looks risky.

## Demo

The demo includes 5 sample student flows for judge walkthroughs:

1. Low-risk consistent writer
2. Sudden style-shift case
3. Timing anomaly submission
4. High-risk baseline deviation
5. Strong vocabulary jump case
