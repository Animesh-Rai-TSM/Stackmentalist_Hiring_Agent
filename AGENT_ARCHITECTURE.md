# AI-Powered Hiring System - Architecture Documentation

## 🎯 System Overview

The AI-Powered Hiring System is a multi-agent architecture built with LangChain/LangGraph that automates and enhances the technical hiring process while keeping humans in control of final decisions.

---

## 🏗️ High-Level System Architecture

```
┌─────────────────────────────────────────────────────────────────────────┐
│                        AI-POWERED HIRING SYSTEM                          │
│                                                                          │
│  ┌────────────────┐         ┌──────────────────┐      ┌──────────────┐ │
│  │   CANDIDATE    │         │   APPLICATION    │      │   HR/ADMIN   │ │
│  │     PANEL      │────────▶│   MANAGEMENT     │◀─────│     PANEL    │ │
│  │   (Next.js)    │         │   (FastAPI)      │      │  (Next.js)   │ │
│  └────────────────┘         └─────────┬────────┘      └──────────────┘ │
│                                       │                                  │
│                                       ▼                                  │
│                          ┌────────────────────────┐                     │
│                          │   AI AGENT             │                     │
│                          │   ORCHESTRATOR         │                     │
│                          │   (LangGraph)          │                     │
│                          └──────────┬─────────────┘                     │
│                                     │                                    │
│              ┌──────────────────────┼──────────────────────┐            │
│              │                      │                      │            │
│              ▼                      ▼                      ▼            │
│    ┌─────────────────┐   ┌──────────────────┐   ┌─────────────────┐   │
│    │  EVALUATION     │   │  ROLE-SPECIFIC   │   │   INTERVIEW     │   │
│    │    AGENTS       │   │   RAG STORES     │   │ COORDINATION    │   │
│    └─────────────────┘   └──────────────────┘   └─────────────────┘   │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

---

# Agent Architecture - Role-Specific Hiring Agents

Based on the AI-Powered Hiring System documentation, the system uses **role-specific agents** where each role domain has its own dedicated agent with customized evaluation criteria.

---

## 1. AI/ML Engineer Agent

```
╔═══════════════════════════════════════════════════════════════╗
║              AI/ML ENGINEER HIRING AGENT                       ║
╚═══════════════════════════════════════════════════════════════╝

INPUT:
┌─────────────────────────────────────────┐
│ • Candidate Application                 │
│ • Resume                                │
│ • GitHub Profile (optional)             │
│ • Portfolio Links (optional)            │
└──────────────────┬──────────────────────┘
                   │
                   ▼
┌─────────────────────────────────────────┐
│   ROLE-SPECIFIC RAG KNOWLEDGE BASE      │
├─────────────────────────────────────────┤
│ AI/ML Engineer Requirements:            │
│                                         │
│ • Required Skills:                      │
│   - Python                              │
│   - PyTorch/TensorFlow                  │
│   - Machine Learning                    │
│   - NLP/Computer Vision                 │
│   - Cloud (AWS/GCP/Azure)               │
│                                         │
│ • Preferred Skills:                     │
│   - MLOps                               │
│   - Kubernetes                          │
│   - Model Deployment                    │
│                                         │
│ • ML Project Expectations               │
│ • Technical Evaluation Rubric           │
│ • Scoring Criteria                      │
└──────────────────┬──────────────────────┘
                   │
                   ▼
┌─────────────────────────────────────────┐
│         EVALUATION PIPELINE             │
├─────────────────────────────────────────┤
│                                         │
│ 1. Resume Parsing                       │
│    └─ Extract: Skills, Projects, Exp    │
│                                         │
│ 2. Skill Matching (RAG-based)           │
│    └─ Match against AI/ML requirements  │
│                                         │
│ 3. GitHub Analysis (Technical)          │
│    └─ Analyze ML repositories           │
│    └─ Check: Python, Jupyter notebooks  │
│                                         │
│ 4. Open Source Verification             │
│    └─ Verify ML contributions           │
│                                         │
│ 5. Project Evaluation                   │
│    └─ Evaluate ML project depth         │
│    └─ Check model training evidence     │
│                                         │
│ 6. Scoring & Ranking                    │
│    └─ Weightage:                        │
│        • Skills: 30%                    │
│        • Projects: 25%                  │
│        • GitHub: 20%                    │
│        • Experience: 15%                │
│        • Education: 10%                 │
└──────────────────┬──────────────────────┘
                   │
                   ▼
OUTPUT:
┌─────────────────────────────────────────┐
│ • Overall Score: 84/100                 │
│ • Skill Match: Strong                   │
│ • GitHub Evidence: Available            │
│ • ML Project Quality: High              │
│ • Recommendation: STRONGLY CONSIDER     │
│ • Evidence Links                        │
└─────────────────────────────────────────┘
```

---

## 2. Full-Stack Developer Agent

```
╔═══════════════════════════════════════════════════════════════╗
║           FULL-STACK DEVELOPER HIRING AGENT                    ║
╚═══════════════════════════════════════════════════════════════╝

INPUT:
┌─────────────────────────────────────────┐
│ • Candidate Application                 │
│ • Resume                                │
│ • GitHub Profile (optional)             │
│ • Portfolio Links (optional)            │
└──────────────────┬──────────────────────┘
                   │
                   ▼
┌─────────────────────────────────────────┐
│   ROLE-SPECIFIC RAG KNOWLEDGE BASE      │
├─────────────────────────────────────────┤
│ Full-Stack Developer Requirements:      │
│                                         │
│ • Frontend Requirements:                │
│   - React/Angular/Vue                   │
│   - JavaScript/TypeScript               │
│   - HTML/CSS                            │
│                                         │
│ • Backend Requirements:                 │
│   - Node.js/Python/Java                 │
│   - REST APIs                           │
│   - Database (SQL/NoSQL)                │
│                                         │
│ • API Requirements                      │
│ • Database Requirements                 │
│ • Deployment Requirements               │
│ • Full-stack Evaluation Rubric          │
└──────────────────┬──────────────────────┘
                   │
                   ▼
┌─────────────────────────────────────────┐
│         EVALUATION PIPELINE             │
├─────────────────────────────────────────┤
│                                         │
│ 1. Resume Parsing                       │
│    └─ Extract: Skills, Projects, Exp    │
│                                         │
│ 2. Skill Matching (RAG-based)           │
│    └─ Match frontend + backend skills   │
│                                         │
│ 3. GitHub Analysis (Technical)          │
│    └─ Analyze full-stack repositories   │
│    └─ Check: Both FE and BE code        │
│                                         │
│ 4. Open Source Verification             │
│    └─ Verify full-stack contributions   │
│                                         │
│ 5. Project Evaluation                   │
│    └─ Evaluate full-stack projects      │
│    └─ Check: Frontend + Backend + DB    │
│    └─ Check deployment evidence         │
│                                         │
│ 6. Scoring & Ranking                    │
│    └─ Weightage:                        │
│        • Skills: 30%                    │
│        • Projects: 25%                  │
│        • GitHub: 20%                    │
│        • Experience: 15%                │
│        • Education: 10%                 │
└──────────────────┬──────────────────────┘
                   │
                   ▼
OUTPUT:
┌─────────────────────────────────────────┐
│ • Overall Score: XX/100                 │
│ • Frontend Skills: Strong/Weak          │
│ • Backend Skills: Strong/Weak           │
│ • Full-stack Project Quality: XX        │
│ • Recommendation: CONSIDER/REJECT       │
│ • Evidence Links                        │
└─────────────────────────────────────────┘
```

---

## 3. Data Engineer Agent

```
╔═══════════════════════════════════════════════════════════════╗
║              DATA ENGINEER HIRING AGENT                        ║
╚═══════════════════════════════════════════════════════════════╝

INPUT:
┌─────────────────────────────────────────┐
│ • Candidate Application                 │
│ • Resume                                │
│ • GitHub Profile (optional)             │
│ • Portfolio Links (optional)            │
└──────────────────┬──────────────────────┘
                   │
                   ▼
┌─────────────────────────────────────────┐
│   ROLE-SPECIFIC RAG KNOWLEDGE BASE      │
├─────────────────────────────────────────┤
│ Data Engineer Requirements:             │
│                                         │
│ • SQL Requirements                      │
│   - Complex queries                     │
│   - Database optimization               │
│                                         │
│ • Python Requirements                   │
│   - Data processing libraries           │
│   - Pandas, NumPy                       │
│                                         │
│ • ETL Requirements                      │
│   - Pipeline design                     │
│   - Data transformation                 │
│                                         │
│ • Data Pipeline Requirements            │
│ • Cloud/Data Infrastructure (AWS/GCP)   │
│ • Evaluation Rubric                     │
└──────────────────┬──────────────────────┘
                   │
                   ▼
┌─────────────────────────────────────────┐
│         EVALUATION PIPELINE             │
├─────────────────────────────────────────┤
│                                         │
│ 1. Resume Parsing                       │
│    └─ Extract: Skills, Projects, Exp    │
│                                         │
│ 2. Skill Matching (RAG-based)           │
│    └─ Match against data eng skills     │
│                                         │
│ 3. GitHub Analysis (Technical)          │
│    └─ Analyze data pipeline repos       │
│    └─ Check: SQL, Python, ETL code      │
│                                         │
│ 4. Open Source Verification             │
│    └─ Verify data engineering contribs  │
│                                         │
│ 5. Project Evaluation                   │
│    └─ Evaluate data pipeline projects   │
│    └─ Check ETL implementation          │
│    └─ Check data processing scale       │
│                                         │
│ 6. Scoring & Ranking                    │
│    └─ Weightage:                        │
│        • Skills: 30%                    │
│        • Projects: 25%                  │
│        • GitHub: 20%                    │
│        • Experience: 15%                │
│        • Education: 10%                 │
└──────────────────┬──────────────────────┘
                   │
                   ▼
OUTPUT:
┌─────────────────────────────────────────┐
│ • Overall Score: XX/100                 │
│ • SQL Proficiency: Strong/Weak          │
│ • ETL Experience: Strong/Weak           │
│ • Data Pipeline Quality: XX             │
│ • Recommendation: CONSIDER/REJECT       │
│ • Evidence Links                        │
└─────────────────────────────────────────┘
```

---

## 4. Frontend Developer Agent

```
╔═══════════════════════════════════════════════════════════════╗
║            FRONTEND DEVELOPER HIRING AGENT                     ║
╚═══════════════════════════════════════════════════════════════╝

INPUT:
┌─────────────────────────────────────────┐
│ • Candidate Application                 │
│ • Resume                                │
│ • GitHub Profile (optional)             │
│ • Portfolio Links (optional)            │
└──────────────────┬──────────────────────┘
                   │
                   ▼
┌─────────────────────────────────────────┐
│   ROLE-SPECIFIC RAG KNOWLEDGE BASE      │
├─────────────────────────────────────────┤
│ Frontend Developer Requirements:        │
│                                         │
│ • JavaScript/TypeScript                 │
│   - Modern ES6+ features                │
│   - Async programming                   │
│                                         │
│ • React/Angular/Vue                     │
│   - Component architecture              │
│   - State management                    │
│                                         │
│ • UI Implementation                     │
│   - HTML5/CSS3                          │
│   - Responsive design                   │
│                                         │
│ • Performance Optimization              │
│ • Responsive Design Principles          │
│ • Frontend Project Criteria             │
└──────────────────┬──────────────────────┘
                   │
                   ▼
┌─────────────────────────────────────────┐
│         EVALUATION PIPELINE             │
├─────────────────────────────────────────┤
│                                         │
│ 1. Resume Parsing                       │
│    └─ Extract: Skills, Projects, Exp    │
│                                         │
│ 2. Skill Matching (RAG-based)           │
│    └─ Match against frontend skills     │
│                                         │
│ 3. GitHub Analysis (Technical)          │
│    └─ Analyze frontend repositories     │
│    └─ Check: JS/TS, React, CSS code     │
│                                         │
│ 4. Open Source Verification             │
│    └─ Verify frontend contributions     │
│                                         │
│ 5. Project Evaluation                   │
│    └─ Evaluate UI/UX projects           │
│    └─ Check responsive design           │
│    └─ Check live demos                  │
│                                         │
│ 6. Scoring & Ranking                    │
│    └─ Weightage:                        │
│        • Skills: 30%                    │
│        • Projects: 25%                  │
│        • GitHub: 20%                    │
│        • Experience: 15%                │
│        • Education: 10%                 │
└──────────────────┬──────────────────────┘
                   │
                   ▼
OUTPUT:
┌─────────────────────────────────────────┐
│ • Overall Score: XX/100                 │
│ • JavaScript Skills: Strong/Weak        │
│ • Framework Proficiency: Strong/Weak    │
│ • UI/UX Quality: XX                     │
│ • Recommendation: CONSIDER/REJECT       │
│ • Evidence Links                        │
└─────────────────────────────────────────┘
```

---

## Additional Role: UI/UX Designer Agent

```
╔═══════════════════════════════════════════════════════════════╗
║              UI/UX DESIGNER HIRING AGENT                       ║
╚═══════════════════════════════════════════════════════════════╝

INPUT:
┌─────────────────────────────────────────┐
│ • Candidate Application                 │
│ • Resume                                │
│ • Portfolio (required)                  │
│ • Figma/Design Links                    │
└──────────────────┬──────────────────────┘
                   │
                   ▼
┌─────────────────────────────────────────┐
│   ROLE-SPECIFIC RAG KNOWLEDGE BASE      │
├─────────────────────────────────────────┤
│ UI/UX Designer Requirements:            │
│                                         │
│ • UX Requirements                       │
│   - User research                       │
│   - Wireframing                         │
│   - User flows                          │
│                                         │
│ • UI Requirements                       │
│   - Visual design                       │
│   - Design systems                      │
│   - Prototyping                         │
│                                         │
│ • Research Expectations                 │
│ • Design Systems Knowledge              │
│ • Portfolio Evaluation Criteria         │
└──────────────────┬──────────────────────┘
                   │
                   ▼
┌─────────────────────────────────────────┐
│         EVALUATION PIPELINE             │
├─────────────────────────────────────────┤
│                                         │
│ 1. Resume Parsing                       │
│    └─ Extract: Skills, Projects, Exp    │
│                                         │
│ 2. Skill Matching (RAG-based)           │
│    └─ Match against UX/UI skills        │
│                                         │
│ 3. GitHub Analysis (NOT APPLICABLE)     │
│    └─ Skipped for non-technical role    │
│                                         │
│ 4. Open Source Verification             │
│    └─ Skipped (not relevant)            │
│                                         │
│ 5. Portfolio Evaluation                 │
│    └─ Evaluate design projects          │
│    └─ Check Figma/design tool work      │
│    └─ Assess UX research evidence       │
│                                         │
│ 6. Scoring & Ranking                    │
│    └─ Weightage (Adjusted):             │
│        • Portfolio: 40%                 │
│        • Skills: 25%                    │
│        • Projects: 20%                  │
│        • Experience: 10%                │
│        • Education: 5%                  │
└──────────────────┬──────────────────────┘
                   │
                   ▼
OUTPUT:
┌─────────────────────────────────────────┐
│ • Overall Score: XX/100                 │
│ • UX Research Skills: Strong/Weak       │
│ • Visual Design Skills: Strong/Weak     │
│ • Portfolio Quality: XX                 │
│ • Recommendation: CONSIDER/REJECT       │
│ • Evidence Links                        │
└─────────────────────────────────────────┘
```

---

## Key Differences Between Role Agents

### 1. Role-Specific RAG Knowledge Base
Each agent loads different requirements from its own RAG namespace:
- AI/ML Engineer: ML frameworks, model training
- Full-Stack: Frontend + Backend + Databases
- Data Engineer: SQL, ETL, data pipelines
- Frontend: JavaScript frameworks, UI/UX
- UI/UX Designer: Design tools, research methods

### 2. Conditional Pipeline Execution
```
┌─────────────────────────────────────────┐
│ GitHub Analysis Agent                   │
├─────────────────────────────────────────┤
│ • AI/ML Engineer:        ✓ RUNS         │
│ • Full-Stack Developer:  ✓ RUNS         │
│ • Data Engineer:         ✓ RUNS         │
│ • Frontend Developer:    ✓ RUNS         │
│ • UI/UX Designer:        ✗ SKIPPED      │
└─────────────────────────────────────────┘
```

### 3. Different Scoring Weightage
```
AI/ML Engineer:
├─ Skills: 30%
├─ Projects: 25%
├─ GitHub: 20%
├─ Experience: 15%
└─ Education: 10%

UI/UX Designer:
├─ Portfolio: 40%
├─ Skills: 25%
├─ Projects: 20%
├─ Experience: 10%
└─ Education: 5%
```

### 4. Role-Specific Evaluation Criteria
```
AI/ML Engineer:
└─ Projects evaluated for:
   ├─ Model training evidence
   ├─ Dataset handling
   └─ ML framework usage

Frontend Developer:
└─ Projects evaluated for:
   ├─ Responsive design
   ├─ UI implementation
   └─ Live demo quality

Data Engineer:
└─ Projects evaluated for:
   ├─ Pipeline architecture
   ├─ Data processing scale
   └─ ETL implementation
```

---

## Agent Orchestrator Logic

```
╔═══════════════════════════════════════════════════════════════╗
║              AI AGENT ORCHESTRATOR                             ║
╚═══════════════════════════════════════════════════════════════╝

APPLICATION RECEIVED
        │
        ▼
┌─────────────────────┐
│ Identify Role       │
├─────────────────────┤
│ • AI/ML Engineer?   │
│ • Full-Stack Dev?   │
│ • Data Engineer?    │
│ • Frontend Dev?     │
│ • UI/UX Designer?   │
└─────────┬───────────┘
          │
          ▼
┌──────────────────────────────────────┐
│ Load Role-Specific Agent Pipeline    │
├──────────────────────────────────────┤
│ IF role = "AI/ML Engineer":          │
│    └─ Load AI/ML RAG                 │
│    └─ Enable GitHub Analysis         │
│    └─ Use ML evaluation rubric       │
│                                      │
│ IF role = "UI/UX Designer":          │
│    └─ Load Design RAG                │
│    └─ Skip GitHub Analysis           │
│    └─ Prioritize Portfolio           │
└──────────────────────────────────────┘
```

---

## Summary

The system uses **4 primary role-specific agents**:

1. **AI/ML Engineer Agent** - ML-focused evaluation
2. **Full-Stack Developer Agent** - Frontend + Backend evaluation
3. **Data Engineer Agent** - Data pipeline focused evaluation
4. **Frontend Developer Agent** - UI-focused evaluation

Plus additional agents as needed:
- **UI/UX Designer Agent** - Design portfolio focused

Each agent:
- Uses its own RAG knowledge base
- Has customized evaluation criteria
- Applies role-specific scoring weightage
- Conditionally executes pipeline components
- Generates evidence-backed recommendations
