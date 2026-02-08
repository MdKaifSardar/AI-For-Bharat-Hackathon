# 📝 Project Requirements: ResumeBro

**Hackathon**: Amazon AI for Bharat
**Theme**: AI-driven Employment & Productivity
**Version**: 1.0 (MVP)

---

## 1. Problem Statement

In the competitive Indian job market, candidates often struggle to get their resumes noticed by Applicant Tracking Systems (ATS). Generic resumes fail to highlight relevant skills for specific job descriptions (JDs), leading to high rejection rates. Manually tailoring a resume for every application is time-consuming and error-prone.

## 2. Value Proposition

**ResumeBro** is an intelligent, privacy-focused AI agent that automates the customization of resumes. It parses a user's existing resume and a target job description, maps the skills gap, and regenerates a perfectly tailored resume that maximizes the ATS match score while maintaining the candidate's authentic voice.

## 3. Core Functional Requirements

### 3.1 Resume Parsing Module (Step 1)

- **Input**: PDF upload (Candidate's active resume).
- **Processing**:
  - Extract raw text from PDF.
  - Segment text into 13 specific section types.
  - **AI Task**: Parse unstructured text into a structured JSON object.
  - **Token Deduction**: Tokens are deducted **per section** parsed.
- **Output**: JSON representation containing:
  - `Candidate Info`
  - `Education`
  - `Experience`
  - `Projects`
  - `Academic Projects`
  - `Skills`
  - `Certifications`
  - `Languages`
  - `Research`
  - `Extracurricular`
  - `Hobbies`
  - `Achievements`
  - `Summary`

### 3.2 Job Description Parsing Module (Step 3)

- **Input**: Text paste or URL (Target Job Description).
- **Processing**:
  - Segment JD text into 6 key areas.
  - **Token Deduction**: A single **bulk deduction** is made for the total calculated cost of analyzing all segments.
- **Output**: Structured Analysis containing:
  - `Job Details`
  - `Overview`
  - `Requirements`
  - `Responsibilities`
  - `Eligibility`
  - `Selection Process`

### 3.3 Tailored Generation Engine (Step 5)

- **Input**: Parsed Resume JSON + Parsed JD Analysis.
- **AI Task**:
  - **Match**: Compare Candidate Skills vs. JD Requirements.
  - **Rewrite**: Context-aware rephrasing of narrative sections.
  - **Token Deduction**: Tokens are deducted **only** for the following 5 generated sections:
    1. `Summary`
    2. `Experience`
    3. `Projects`
    4. `Academic Projects`
    5. `Skills`
  - _Note_: Other sections (Education, Certifications, etc.) are copied statically and do not incur AI costs.
- **Output**: A new, tailored resume object.

### 3.4 PDF Rendering & Download

- **Feature**: Real-time preview of the generated resume.
- **Output**: Downloadable, ATS-friendly PDF.

### 3.5 User Dashboard

- **Features**:
  - View "Token/Credit" balance.
  - Track usage history (Resumes parsed, JDs parsed).
  - Save and manage multiple versions of tailored resumes.

## 4. Non-Functional Requirements

### 4.1 Performance

- **Latency**: Parsing steps should take < 5 seconds. Full generation should take < 30 seconds.
- **Feedback**: Real-time progress indicators for all AI operations.

### 4.2 Security & Privacy

- **Data Handling**: Resume data handling must be secure.
- **Authentication**: Usage protected via User Authentication (Firebase).

### 4.3 Reliability

- **Fallback**: The tailored resume must never hallucinate fake experiences. It strictly rephrases _existing_ facts.
- **Error Handling**: Graceful degradation if AI services are unavailable.

## 5. Technology constraints

- **Frontend**: Next.js (React 19)
- **Styling**: Tailwind CSS (Responsive Design)
- **State Management**: Redux Toolkit (Complex Multi-step Wizard)
- **AI Model**: LLM integration (OpenAI/AWS Bedrock compatible)
- **Database/Auth**: Firebase

---

_Generated for Amazon AI for Bharat Hackathon - Phase 1_
