# AI-Powered Regression Impact Analysis & Regression Suite Recommendation Platform

## Version
1.0

## Domain
Car Rental Mobile Application

## Objective
Design an enterprise-grade AI platform that analyzes merged GitHub PRs during a sprint and automatically identifies:
- Impacted Features
- Impacted User Journeys
- Existing Regression Test Cases to Execute
- New Regression Test Cases to Add
- Risk Areas
- Historical Defect-Prone Areas

## Technology Stack
- Frontend: React.js
- Backend: Node.js + TypeScript
- Vector DB: MongoDB Vector Search
- Embeddings: Mistral AI
- Retrieval: Hybrid Search + Reranking
- Feedback: Approve / Reject / Edit

## High-Level Flow
1. Ingest GitHub PRs, Jira, Confluence, Defects, Technical Docs
2. Generate embeddings using Mistral
3. Store in MongoDB Vector DB
4. Perform Hybrid Search (Vector + BM25)
5. Rerank Results
6. Deduplicate
7. Summarize Context
8. Generate Impact Analysis using LLM
9. Validate Output
10. Collect User Feedback

## Core APIs

POST /api/v1/sprint/analyze
GET /api/v1/sprint/{id}/results
GET /api/v1/impacts/features
GET /api/v1/impacts/journeys
GET /api/v1/regression/existing
GET /api/v1/regression/new
POST /api/v1/feedback
GET /api/v1/export/excel
GET /api/v1/export/csv
GET /api/v1/export/json

## Enterprise Folder Structure

src/
├── api/
├── controllers/
├── services/
├── repositories/
├── integrations/
│   ├── github/
│   ├── jira/
│   └── confluence/
├── embeddings/
├── retrieval/
├── reranking/
├── llm/
├── validation/
├── feedback/
├── exports/
├── models/
├── middleware/
└── configs/

## Outputs
- Impacted Features
- Impacted User Journeys
- Existing Regression Cases
- New Regression Cases
- Risk Areas
- Explainability Scores
- Excel/CSV/JSON Exports
