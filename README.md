# Cynbit LeadIQ — AI-Powered Inquiry Intelligence & Lead Routing

## Overview
Cynbit LeadIQ is a proof of concept for an AI-assisted inquiry processing layer. It is designed to complement existing inquiry entry points such as Blueprint, service inquiries, product demo requests, and general contact.

The prototype classifies inquiry text, extracts available budget and timeline information, assigns an explainable priority score, recommends a team and next action, and drafts a follow-up message for human review.

**Scope:** Uses synthetic sample inquiries only. It is not connected to Cynbit's live website, CRM, email, or customer database. Priority is a rule-based heuristic, not a trained probability of lead conversion.

## Project structure
```text
Cynbit_LeadIQ_Colab_PoC/
├── Cynbit_LeadIQ_PoC.ipynb
├── README.md
├── requirements.txt
├── data/
│   └── sample_inquiries.csv
├── docs/
│   └── architecture.md
└── reports/
    └── Technical_Approach_Report.pdf
```

## Run in Google Colab
1. Download and extract the project ZIP.
2. Open https://colab.research.google.com/.
3. Select **File → Upload notebook** and upload `Cynbit_LeadIQ_PoC.ipynb`.
4. Run cells from top to bottom.
5. When prompted, upload `data/sample_inquiries.csv`.
6. The notebook loads `all-MiniLM-L6-v2`; if unavailable, it uses a TF-IDF fallback.
7. Run the Gradio cell to launch the interactive inquiry-analysis demo.
8. Run the final export cell to process the sample dataset and download `leadiq_analyzed_inquiries.csv`.

## What it demonstrates
- Semantic service/product classification using Sentence Transformers (`all-MiniLM-L6-v2`).
- Cosine similarity against predefined category descriptions.
- TF-IDF fallback.
- Regex-based budget and timeline extraction.
- Explainable rule-based priority scoring (High / Medium / Low).
- Predefined team routing and next-action recommendations.
- Template-based follow-up draft for human review.
- Individual inquiry analysis through Gradio.
- Batch CSV processing and analyzed CSV export.

## Input and output
Input: `sample_inquiries.csv` contains 16 synthetic inquiries with inquiry ID, source channel, inquiry text, provided category, industry, budget, timeline, and product.

Output: `leadiq_analyzed_inquiries.csv` adds predicted category, similarity score, extracted/provided details, priority score and level, scoring explanation, recommended team, next action, and follow-up draft.

**Note:** Gradio displays the analysis of an individual inquiry, but this version does not automatically append that inquiry to the batch output CSV.

## Technology
Python, Google Colab, Pandas, NumPy, Sentence Transformers, Scikit-learn, Regex, Gradio, Matplotlib, and CSV.

## Limitations
- Synthetic data, not actual Cynbit customer data.
- Pretrained model, not fine-tuned on Cynbit-specific examples.
- Source channel and industry are supplied as inputs.
- Budget and timeline extraction use basic patterns.
- Priority scoring and routing are rule-based.
- No live form, CRM, email, or database integration.
- No independent labeled test set or validated accuracy metrics.

## Future enhancements
Secure API/webhook integration, LLM-based requirement extraction, predictive lead scoring using sufficient historical outcomes, CRM integration after workflow discovery, duplicate detection, analytics, audit logs, and human-approved automation.

## Suggested demo
Show one Blueprint inquiry, one service inquiry with budget/timeline, one product demo request, explain the scoring and routing, then run batch processing and show the exported CSV.

## Author
Mohammed Ali Khan
