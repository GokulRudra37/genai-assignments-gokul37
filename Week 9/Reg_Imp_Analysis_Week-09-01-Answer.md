# **AI-Powered Regression Impact Analysis & Regression Suite Recommendation Platform**

## **Version**

1.0

## **Domain**

Car Rental Mobile Application

## **Objective**

Design an enterprise-grade AI platform that analyzes merged GitHub PRs during a sprint and automatically identifies:

* Impacted Features  
* Impacted User Journeys  
* Existing Regression Test Cases to Execute  
* New Regression Test Cases to Add  
* Risk Areas  
* Historical Defect-Prone Areas

The platform leverages RAG (Retrieval Augmented Generation), MongoDB Vector Search, Mistral Embeddings, Hybrid Search, Reranking, Explainable AI, and Human Feedback Loops.

---

# **1\. High-Level Architecture**

\+-----------------------------------------------------------+  
|                    React Frontend                         |  
\+-----------------------------------------------------------+  
            |                    |  
            | REST APIs          |  
            v                    v

\+-----------------------------------------------------------+  
|              Node.js \+ TypeScript Backend                 |  
\+-----------------------------------------------------------+

       \+---------------------------+  
       | Sprint Analysis Engine    |  
       \+---------------------------+

                     |  
                     v

\+-----------------------------------------------------------+  
|                    Ingestion Layer                        |  
\+-----------------------------------------------------------+

 GitHub PRs  
 Jira User Stories  
 Jira Test Cases  
 Confluence  
 Defect Database  
 Technical Docs  
 GitHub Reports

                     |  
                     v

\+-----------------------------------------------------------+  
|              Embedding Generation Layer                   |  
|                Mistral Embedding Model                    |  
\+-----------------------------------------------------------+

                     |  
                     v

\+-----------------------------------------------------------+  
|                MongoDB Vector Database                    |  
\+-----------------------------------------------------------+

 stories\_embeddings  
 testcase\_embeddings  
 confluence\_embeddings  
 defect\_embeddings  
 github\_embeddings  
 technical\_doc\_embeddings

                     |  
                     v

\+-----------------------------------------------------------+  
|                Retrieval Pipeline                         |  
\+-----------------------------------------------------------+

 BM25 Search  
 Vector Search  
 Hybrid Search  
 Reranking  
 Deduplication  
 Summarization

                     |  
                     v

\+-----------------------------------------------------------+  
|                Prompt Builder Layer                       |  
\+-----------------------------------------------------------+

                     |  
                     v

\+-----------------------------------------------------------+  
|                         LLM                               |  
\+-----------------------------------------------------------+

                     |  
                     v

\+-----------------------------------------------------------+  
|               Validation Framework                        |  
\+-----------------------------------------------------------+

 Source Validation  
 Confidence Scoring  
 Coverage Analysis  
 Hallucination Detection  
 Traceability Validation

                     |  
                     v

\+-----------------------------------------------------------+  
|          Recommendation & Explainability Layer            |  
\+-----------------------------------------------------------+

 Impacted Features  
 Impacted Journeys  
 Existing Regression Cases  
 New Regression Cases

                     |  
                     v

\+-----------------------------------------------------------+  
|               Feedback Learning Layer                     |  
\+-----------------------------------------------------------+

 Approve  
 Reject  
 Edit

---

# **2\. Data Sources**

## **GitHub**

Input:

* PR Title  
* PR Description  
* Changed Files  
* Code Diff  
* Labels  
* Linked Jira IDs

## **Jira**

Input:

* User Stories  
* Acceptance Criteria  
* Test Cases

## **Confluence**

Input:

* Functional Documents  
* Business Flows  
* Architecture Documents

## **Defect Database**

Input:

* Production Defects  
* Escaped Defects  
* Root Cause Analysis

## **Technical Documentation**

Input:

* API Specs  
* Service Documentation  
* Design Documents

---

# **3\. Ingestion Pipeline**

## **Step 1**

Fetch Data

GitHub APIs  
Jira APIs  
Confluence APIs  
Defect APIs

## **Step 2**

Normalization

Convert all documents into:

{  
  "id": "",  
  "sourceType": "",  
  "feature": "",  
  "module": "",  
  "content": "",  
  "metadata": {}  
}

## **Step 3**

Chunking

Recommended:

Chunk Size \= 1000  
Overlap \= 200

## **Step 4**

Embedding Generation

Model:

Mistral Embedding Model

Generated Fields:

{  
  "embedding": \[\]  
}

---

# **4\. MongoDB Vector Database Design**

## **Collections**

### **user\_story\_embeddings**

{  
 "storyId":"",  
 "feature":"",  
 "journey":"",  
 "embedding":\[\]  
}

### **testcase\_embeddings**

{  
 "testCaseId":"",  
 "feature":"",  
 "journey":"",  
 "priority":"",  
 "embedding":\[\]  
}

### **confluence\_embeddings**

### **defect\_embeddings**

### **github\_embeddings**

### **technical\_doc\_embeddings**

---

# **5\. Sprint Analysis Flow**

QA User selects:

Sprint Number  
Release Number  
GitHub Repository

System fetches:

All merged PRs

System extracts:

Changed Files  
Changed APIs  
Changed Components  
Changed Services

---

# **6\. Retrieval Pipeline**

## **Stage 1**

Vector Search

MongoDB Vector Search

Top K:

50

## **Stage 2**

BM25 Search

Search:

Feature Names  
API Names  
Screen Names

Top K:

50

## **Stage 3**

Hybrid Merge

Formula:

Final Score \=  
0.6 \* Vector Score  
\+  
0.4 \* BM25 Score

---

# **7\. Reranking Layer**

Input:

Top 100 Documents

Output:

Top 20 Relevant Documents

Rerank Criteria:

* Feature Similarity  
* Journey Similarity  
* API Similarity  
* Historical Defect Similarity

---

# **8\. Deduplication Layer**

Purpose:

Remove:

* Duplicate Test Cases  
* Duplicate Stories  
* Duplicate Defects

Methods:

Cosine Similarity  
Metadata Matching

Threshold:

0.95

---

# **9\. Summarization Layer**

Generate:

Feature Summary  
Journey Summary  
Defect Summary  
Coverage Summary

Output becomes prompt context.

---

# **10\. Prompt Engineering Layer**

## **System Prompt**

You are a Senior QA Architect with 15 years of  
experience in Car Rental Mobile Applications.

Analyze merged PRs and identify:

1\. Impacted Features  
2\. Impacted User Journeys  
3\. Existing Regression Cases  
4\. New Regression Cases  
5\. Risk Areas  
6\. Historical Defect Patterns

Return explainable output.

---

# **11\. LLM Output**

Expected Output

{  
 "impactedFeatures":\[\],  
 "impactedJourneys":\[\],  
 "existingRegressionCases":\[\],  
 "newRegressionCases":\[\],  
 "riskAreas":\[\],  
 "confidenceScore":""  
}

---

# **12\. Validation Framework**

## **Layer 1**

Source Validation

Validate every recommendation against:

* Jira  
* Confluence  
* Defect DB

## **Layer 2**

Coverage Validation

Check:

Feature Coverage  
Journey Coverage  
API Coverage

## **Layer 3**

Hallucination Detection

Reject recommendations having:

No Source Attribution

## **Layer 4**

Confidence Score

Formula:

Retrieval Score  
\+  
Rerank Score  
\+  
Source Match Score

---

# **13\. Explainability Framework**

Each recommendation includes:

{  
 "feature":"Pay & Book",  
 "sourcePRs":\["PR-234"\],  
 "sourceStories":\["JIRA-123"\],  
 "sourceDefects":\["BUG-345"\],  
 "retrievalScore":0.91,  
 "rerankScore":0.95,  
 "confidenceScore":0.93,  
 "reason":"Payment API modified"  
}

---

# **14\. Feedback Learning Loop**

Actions:

Approve  
Reject  
Edit

Store:

{  
 "recommendationId":"",  
 "action":"",  
 "editedValue":""  
}

Uses:

* Improve prompts  
* Improve retrieval  
* Improve reranking

---

# **15\. REST API Design**

## **Analyze Sprint**

POST /api/v1/sprint/analyze

Request

{  
 "sprintId":"SPRINT-45"  
}

---

## **Get Analysis Result**

GET /api/v1/sprint/{id}/results

---

## **Get Impacted Features**

GET /api/v1/impacts/features

---

## **Get Impacted Journeys**

GET /api/v1/impacts/journeys

---

## **Get Existing Regression Cases**

GET /api/v1/regression/existing

---

## **Get New Regression Cases**

GET /api/v1/regression/new

---

## **Submit Feedback**

POST /api/v1/feedback

Request

{  
 "recommendationId":"123",  
 "action":"APPROVE"  
}

---

## **Export Excel**

GET /api/v1/export/excel

---

## **Export CSV**

GET /api/v1/export/csv

---

## **Export JSON**

GET /api/v1/export/json

---

# **16\. Frontend Architecture (React)**

src  
|  
\+-- pages  
|    \+-- Dashboard  
|    \+-- SprintAnalysis  
|    \+-- ImpactAnalysis  
|    \+-- Recommendations  
|  
\+-- components  
|    \+-- Tables  
|    \+-- Charts  
|    \+-- Filters  
|  
\+-- services  
|    \+-- api  
|  
\+-- hooks  
|  
\+-- store  
|  
\+-- utils

---

# **17\. Backend Architecture (Node.js \+ TypeScript)**

src  
|  
\+-- api  
|  
\+-- controllers  
|  
\+-- services  
|  
\+-- repositories  
|  
\+-- integrations  
|     \+-- github  
|     \+-- jira  
|     \+-- confluence  
|  
\+-- embeddings  
|  
\+-- retrieval  
|  
\+-- reranking  
|  
\+-- llm  
|  
\+-- validation  
|  
\+-- feedback  
|  
\+-- exports  
|  
\+-- models  
|  
\+-- middleware  
|  
\+-- configs

---

# **18\. Output Formats**

## **Excel**

Sheet 1

Impacted Features

Sheet 2

Existing Regression Cases

Sheet 3

New Regression Cases

Sheet 4

Risk Areas

---

## **CSV**

impacted\_features.csv  
existing\_regression.csv  
new\_regression.csv  
risk\_areas.csv

---

## **JSON**

{  
 "release":"R45",  
 "impactedFeatures":\[\],  
 "impactedJourneys":\[\],  
 "existingRegressionCases":\[\],  
 "newRegressionCases":\[\]  
}

---

# **19\. Enterprise Benefits**

* Explainable AI  
* Fully Auditable  
* Regression Suite Optimization  
* Reduced Manual Analysis Effort  
* Faster Weekly Releases  
* Improved Defect Prevention  
* Continuous Learning Platform  
* Enterprise Scalability

# **End of Document**

