# AI-Powered Hiring System

> **Transforming Technical Hiring with Multi-Agent AI Architecture**

An intelligent hiring management system built with **LangChain/LangGraph** that automates resume screening, GitHub analysis, and interview coordination while keeping humans in control of final decisions.

---

## The Problem

Hiring for technical roles is **slow, inconsistent, and heavily dependent** on the bandwidth of a small number of recruiters and engineering reviewers.

### Pain Points:
- Manual resume screening cannot scale with application volume
- Resumes evaluated on self-reported claims, no systematic skill verification
- One-size-fits-all evaluation criteria for different roles
- Interview coordination consumes valuable recruiter time
- No consistent, auditable evaluation trail
- Strong candidates with non-traditional backgrounds filtered out

### Cost:
Extended time-to-hire, inconsistent candidate experience, lost strong candidates, and wasted recruiter time on repetitive screening work.

---

## The Solution

An **AI-Powered Hiring Management System** built around a **multi-agent architecture** using LangChain and LangGraph.

### Core Principles:

```
AI Assists, Humans Decide
   └─ AI provides recommendations, humans make final decisions

Evidence Over Assumption  
   └─ Every claim links to verifiable sources

Role-Aware Evaluation
   └─ Different roles = different evaluation criteria

Missing Information = Neutral
   └─ No GitHub profile? Mark unavailable, don't penalize
```

---

## Architecture Overview

```
┌─────────────────────────────────────────────────────────────┐
│                  AI-POWERED HIRING SYSTEM                    │
│                                                              │
│  CANDIDATE PANEL  →  APPLICATION API  ←  HR/ADMIN PANEL     │
│    (Next.js)            (FastAPI)          (Next.js)        │
│                             ↓                                │
│                   AI AGENT ORCHESTRATOR                      │
│                      (LangGraph)                             │
│                             ↓                                │
│         ┌───────────────────┼───────────────────┐           │
│         ↓                   ↓                   ↓           │
│  ROLE-SPECIFIC      EVALUATION           INTERVIEW          │
│   RAG STORES         AGENTS           COORDINATION          │
└─────────────────────────────────────────────────────────────┘
```

---

## Role-Specific Agents

The system uses **dedicated agents for each role domain**, each with customized evaluation criteria and role-specific knowledge bases.

### Available Agents:

#### 1. AI/ML Engineer Agent
```
Evaluates: Python, PyTorch/TensorFlow, ML projects, model training
GitHub Focus: ML repositories, Jupyter notebooks, data science code
Scoring: Skills 30% | Projects 25% | GitHub 20% | Experience 15% | Education 10%
```

#### 2. Full-Stack Developer Agent
```
Evaluates: Frontend + Backend skills, API design, database knowledge
GitHub Focus: Full-stack repositories, both FE and BE code
Scoring: Skills 30% | Projects 25% | GitHub 20% | Experience 15% | Education 10%
```

#### 3. Data Engineer Agent
```
Evaluates: SQL, ETL pipelines, data processing, cloud infrastructure
GitHub Focus: Data pipeline repos, SQL scripts, ETL code
Scoring: Skills 30% | Projects 25% | GitHub 20% | Experience 15% | Education 10%
```

#### 4. Frontend Developer Agent
```
Evaluates: JavaScript/TypeScript, React/Vue/Angular, responsive design
GitHub Focus: Frontend repos, UI implementation, modern JS
Scoring: Skills 30% | Projects 25% | GitHub 20% | Experience 15% | Education 10%
```

#### 5. UI/UX Designer Agent
```
Evaluates: Design tools, user research, design systems, portfolios
GitHub Focus: SKIPPED (not applicable)
Scoring: Portfolio 40% | Skills 25% | Projects 20% | Experience 10% | Education 5%
```

---

## How It Works

### For Candidates:

```
1. Browse Open Roles
         ↓
2. Submit Application
   • Upload Resume
   • Provide GitHub/Portfolio (optional)
         ↓
3. AI Evaluation (Automatic)
         ↓
4. Track Application Status
         ↓
5. Receive Interview Invitation
```

### For HR Teams:

```
1. Post Job Opening
   • Define role requirements
   • Set evaluation weightage
         ↓
2. Review AI-Generated Reports
   • Evidence-backed scores
   • Ranked candidates
         ↓
3. Shortlist/Reject Candidates
         ↓
4. Coordinate Interviews (AI-Assisted)
         ↓
5. Make Final Hiring Decision
```

---

## Evaluation Pipeline

Each role-specific agent runs candidates through this pipeline:

```
┌─────────────────────────┐
│  1. RESUME PARSING      │
│  Extract: Skills,       │
│  Projects, Experience   │
└──────────┬──────────────┘
           ↓
┌─────────────────────────┐
│  2. SKILL MATCHING      │
│  Semantic matching      │
│  against role RAG       │
└──────────┬──────────────┘
           ↓
┌─────────────────────────┐
│  3. GITHUB ANALYSIS*    │
│  Repository quality,    │
│  commit history,        │
│  role relevance         │
└──────────┬──────────────┘
           ↓
┌─────────────────────────┐
│  4. OPEN SOURCE         │
│     VERIFICATION        │
│  Verify claimed         │
│  contributions          │
└──────────┬──────────────┘
           ↓
┌─────────────────────────┐
│  5. PROJECT EVALUATION  │
│  Assess project depth,  │
│  completeness, quality  │
└──────────┬──────────────┘
           ↓
┌─────────────────────────┐
│  6. SCORING & RANKING   │
│  Deterministic score    │
│  calculation with       │
│  role-specific weights  │
└──────────┬──────────────┘
           ↓
┌─────────────────────────┐
│  7. EVALUATION REPORT   │
│  Evidence-backed        │
│  recommendation         │
└─────────────────────────┘

*Conditional: Runs for technical roles only
```

---

## Technology Stack

### Frontend
- **Next.js** - Candidate & HR/Admin Panels
- Modern React with TypeScript

### Backend
- **FastAPI** - REST API (Modular Monolith)
  - Applications Module
  - Roles Module
  - Candidates Module
  - Agents Module
  - RAG Module
  - Evaluations Module
  - Notifications Module
  - Interviews Module
  - Audit Module

### AI/ML Stack
- **LangChain** - Agent building blocks
  - LLM calls
  - Prompt templates
  - Retrievers
  - Tools
  - Structured output parsers
- **LangGraph** - Agent orchestration
  - State machine
  - Conditional routing
  - Retry logic
  - Human-in-the-loop nodes

### Data & Storage
- **PostgreSQL** - Relational data
- **Vector Database** (Pinecone/Chroma) - RAG embeddings
- **Cloud Storage** (S3/GCS) - Resume files

### Integrations
- **GitHub API** - Repository analysis
- **Calendar API** - Interview scheduling
- **Email Service** - Notifications
- **LLM Provider** - OpenAI/Anthropic

---

## Security & Compliance

```
Layer 1: Authentication & Authorization
├─ OAuth2 + JWT
├─ Role-Based Access Control (RBAC)
└─ Candidates: Own applications only
   HR: Assigned roles only

Layer 2: Data Encryption
├─ TLS 1.3 (in transit)
├─ AES-256 (at rest)
└─ Encrypted file storage

Layer 3: Secret Management
├─ AWS Secrets Manager / Vault
├─ No credentials in code
└─ API key rotation

Layer 4: Audit & Compliance
├─ Full audit trail
├─ Data retention policies
├─ Secure deletion
└─ Compliance logging
```

---

## Role-Specific RAG System

Each role has its own knowledge base containing:

```
┌────────────────────────────────┐
│     COMPANY REQUIREMENTS       │
│  (Job Descriptions, Rubrics)   │
└────────────┬───────────────────┘
             ↓
    ┌────────────────────┐
    │  Document Loader   │
    │  Text Processing   │
    │  Chunking          │
    │  Embedding         │
    └────────┬───────────┘
             ↓
    ┌────────────────────┐
    │   Vector Storage   │
    └────────┬───────────┘
             ↓
┌────────────┼────────────┐
│            │            │
↓            ↓            ↓
AI/ML      FULL-STACK   DATA
ENGINEER   DEVELOPER    ENGINEER
RAG        RAG          RAG
```

Each RAG namespace contains:
- ✅ Required skills
- ✅ Preferred skills
- ✅ Evaluation rubric
- ✅ Scoring weightage
- ✅ Project expectations
- ✅ GitHub relevance criteria

---

## 🔄 Application Lifecycle

```
APPLIED
  ↓
PROCESSING
  ↓
AI_EVALUATION
  ↓
├─ AI_COMPLETED
└─ AI_NEEDS_REVIEW (low confidence)
  ↓
HR_REVIEW ←──── HUMAN CHECKPOINT
  ↓
├─ SHORTLISTED
└─ REJECTED
  ↓
INTERVIEW_SCHEDULED
  ↓
INTERVIEW_COMPLETED
  ↓
FINAL_REVIEW ←──── HUMAN DECISION
  ↓
├─ SELECTED
└─ REJECTED
```

---

## Development Timeline (4 Weeks)

### Week 1: Foundation & Core Setup
- Authentication system (OAuth2 + JWT)
- Basic frontend panels (Candidate & HR)
- FastAPI backend skeleton
- PostgreSQL database setup
- Application management API
- Resume upload & storage (Cloud Storage)
- Role management system

### Week 2: AI Agent Pipeline - Part 1
- RAG system setup (Vector DB + Embeddings)
- LangChain/LangGraph orchestrator
- Resume Parsing Agent
- Skill Matching Agent
- Role-specific RAG knowledge bases
- Basic evaluation workflow

### Week 3: AI Agent Pipeline - Part 2
- GitHub API integration
- GitHub Analysis Agent
- Open Source Verification Agent
- Project Evaluation Agent
- Deterministic Scoring & Ranking Agent
- Evaluation Report Generation

### Week 4: Integration & Interview Automation
- Email integration (SendGrid/SES)
- Calendar integration (Google/Outlook)
- Interview Coordination Agent
- Notifications system
- Complete workflow testing
- HR dashboard refinement
- Documentation & deployment

---

## 📈 Success Metrics

### Efficiency Metrics
```
Manual Screening Time:    ↓ 80%
Recruiter Workload:       ↓ 60%
Candidate Processing:     ↓ 70%
Interview Scheduling:     ↓ 90%
```

### Quality Metrics
```
HR-AI Agreement:          ↑ 85%
Shortlist Quality:        ↑ 75%
Interview Conversion:     ↑ 40%
Selection Conversion:     ↑ 30%
```

### System Performance
```
AI Evaluation Latency:    < 2 minutes
Agent Failure Rate:       < 1%
API Success Rate:         > 99.5%
RAG Retrieval Quality:    > 90%
```

---

## 🎯 Why Multi-Agent Architecture?

### ❌ Single Large LLM Approach:
```
One prompt does everything
├─ Hard to debug
├─ Opaque results
├─ Difficult to improve
└─ No modular testing
```

### ✅ Multi-Agent Approach:
```
Specialized agents with specific purposes
├─ Easy to debug
├─ Clear evidence trail
├─ Modular improvements
├─ Independent testing
└─ Explainable results
```

---

## 🔍 Example: Candidate Evaluation

```
Candidate: John Doe
Role: AI/ML Engineer

─────────────────────────────────────
RESUME PARSING
✓ Skills: [Python, TensorFlow, PyTorch, ML, NLP, AWS]
✓ Experience: 4 years
✓ Education: MS Computer Science
✓ Projects: 3 ML projects
✓ Confidence: 95%

─────────────────────────────────────
SKILL MATCHING
✓ Python → Python (exact match)
✓ TensorFlow → PyTorch/TF requirement (match)
✓ NLP → NLP (exact match)
✓ AWS → Cloud requirement (semantic match)
✗ Missing: Kubernetes (preferred)
Score: 90%

─────────────────────────────────────
GITHUB ANALYSIS
✓ 15 repositories found
✓ Primary languages: Python (60%), Jupyter (30%)
✓ Notable repos:
  • sentiment-analysis (150 stars)
  • object-detection-yolo
  • ml-pipeline
✓ 300+ commits in last year
Score: 85%

─────────────────────────────────────
OPEN SOURCE VERIFICATION
Claim: "Contributed to TensorFlow"
✓ Found 2 PRs merged
✓ Author email matches
Status: VERIFIED

─────────────────────────────────────
PROJECT EVALUATION
Project: Sentiment Analysis
✓ Completeness: 90%
✓ Documentation: Strong
✓ Live Demo: Available
Score: 88%

Overall Project Depth: 85%

─────────────────────────────────────
FINAL SCORE
• Skills: 90% × 0.30 = 27.00
• Projects: 85% × 0.25 = 21.25
• GitHub: 85% × 0.20 = 17.00
• Experience: 80% × 0.15 = 12.00
• Education: 90% × 0.10 = 9.00

COMPOSITE SCORE: 86/100
RANKING: #8 out of 100 applicants
RECOMMENDATION: STRONGLY CONSIDER

─────────────────────────────────────
STRENGTHS
✓ Strong Python & ML framework experience
✓ Verified TensorFlow open-source contributions
✓ High-quality personal projects with documentation
✓ Active GitHub presence

POTENTIAL GAPS
⚠ Limited Kubernetes/MLOps experience

EVIDENCE
• GitHub: github.com/john
• Project: github.com/john/sentiment-analysis
• TensorFlow PR: github.com/tensorflow/pr/12345
```

---

## 🎓 Key Features

### 1. Role-Specific Evaluation
Each role has customized criteria, weightage, and evaluation pipelines.

### 2. Evidence-Based Reports
Every claim links to verifiable sources (resume, GitHub, projects).

### 3. Human-in-the-Loop
AI provides recommendations, humans make final decisions.

### 4. Deterministic Scoring
Scores calculated using transparent weighted formulas, not LLM guesses.

### 5. Conditional Execution
GitHub analysis runs for technical roles, skipped for others.

### 6. Semantic Skill Matching
React.js ≈ React ≈ ReactJS recognized as same skill.

### 7. Interview Automation
AI-assisted scheduling with calendar integration.

### 8. Complete Audit Trail
Every action logged for compliance and review.

---

## 📋 Requirements from Company

Before implementation, the company must provide:

### Data & Content
- ✅ Standardized job description templates
- ✅ Required & preferred skills per role
- ✅ Evaluation weightage per role
- ✅ Agreement from hiring managers on scoring approach
- ✅ HR policies for candidate data handling

### Access & Integrations
- ✅ GitHub organization/API access (if needed)
- ✅ Email/calendar platform credentials
- ✅ Cloud storage account
- ✅ LLM provider API access
- ✅ Approved API budget and rate limits

### Approvals & Decisions
- ✅ Evaluation criteria per role
- ✅ Data retention and deletion policy
- ✅ Who can override AI-generated scores
- ✅ HR/hiring-manager approval workflow
- ✅ Infrastructure budget

### People
- ✅ One HR point of contact
- ✅ One engineering leadership point of contact

---

## 🎯 Final Objective

Transform hiring from:

```
Manual Screening
     ↓
AI-Assisted Evidence-Based Evaluation

Manual Interview Coordination
     ↓
Automated Interview Scheduling

Opaque Decisions
     ↓
Auditable, Explainable Process
```

While maintaining:
- **Human Control** - Final decisions with authorized humans
- **Explainability** - Clear evidence for every recommendation
- **Auditability** - Complete trail of AI and human actions
- **Role-Specific Evaluation** - Customized criteria per role

---

## 📄 Documentation

- 🤖 [Role-Specific Agents](./AGENT_ARCHITECTURE.md)

---

## 🤝 Guiding Principle

**The system becomes an intelligent hiring assistant for HR and engineering teams, not an autonomous hiring decision-maker.**

```
Role-Specific Requirements 
     → RAG 
     → Specialized Agents 
     → Evidence 
     → Deterministic Scoring 
     → Explainable Report 
     → Human Review 
     → Interview 
     → Human Final Decision
```

---

**Built with ❤️ using LangChain, LangGraph, FastAPI, and Next.js**
