# InterviewMate 🤖
### An NLP-Based Chatbot for Practicing Interview Answers with Automated Feedback

InterviewMate is a mini NLP project that asks users interview-style questions (HR, technical,
and behavioral), takes their typed answer, and gives automated feedback by comparing it to a
model answer using **TF-IDF cosine similarity** and **keyword coverage checking**.

## Problem
Students preparing for interviews rarely have a way to self-evaluate their spoken/typed answers
before the real interview. InterviewMate lets them practice independently and get instant,
structured feedback on relevance and completeness.

## How it works
```
User Answer → Preprocessing → TF-IDF Similarity + Keyword Coverage → Score + Feedback
```
1. A question is picked from a bank of 50 curated Q&A pairs (`dataset/interview_qa.csv`).
2. The user types an answer.
3. The answer is compared against a model answer using TF-IDF cosine similarity.
4. Key concepts expected in a good answer are checked for coverage.
5. A combined score (0–100) and readable feedback (missing concepts, filler words) is returned.

## Tech stack
- Python
- pandas
- scikit-learn (TfidfVectorizer, cosine_similarity)

## Project structure
```
InterviewMate/
├── README.md
├── source_code.py
├── dataset/
│   └── interview_qa.csv
├── screenshots/
├── report/
│   └── project_report.md
└── requirements.txt
```

## How to run
**Option 1 — Google Colab**
1. Upload `interview_qa.csv` to Colab.
2. Paste the sections of `source_code.py` into cells (marked SECTION 0–6).
3. Run `run_chatbot(dataset)` for a live demo, or `run_batch_evaluation(...)` for evaluation.

**Option 2 — Local**
```bash
pip install -r requirements.txt
python source_code.py
```

## Evaluation
The scoring pipeline was tested against a small manually-labeled set of sample answers
(good/average/poor) to check agreement between the automated score and human judgement.
See `report/project_report.md` for full results.

## Limitations
- TF-IDF only captures surface-level word overlap, not paraphrasing or deeper semantic meaning.
- Cannot verify factual correctness of an answer, only relevance/coverage.
- Small, self-curated dataset (50 Q&A pairs), English only.

## Future scope
- Add Sentence-BERT embeddings for semantic (not just lexical) similarity.
- Larger, more diverse question bank across more domains.
- Voice input with speech-to-text for a more realistic mock-interview experience.
