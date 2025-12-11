# Resume-screening-for-HR-round
The HR Interview Screening Chatbot is a cloud-based intelligent system that automates the initial stages of recruitment.
It simulates a real-world hiring workflow used by companies:

"Resume + Application → ATS Filter → Assessment Link → Assessment Scoring → HR Shortlist"

The system uses Streamlit + Python for the applicant interface,
Snowflake as the data warehouse,
Azure for deployment & email automation,
and Power BI for recruiter dashboards.

The goal of the project is to reduce recruiter workload and shortlist the most relevant candidates using a transparent and explainable AI scoring system.

Key Features :

1. Candidate Application Portal (Streamlit)
   .Candidate fills an application form
   .Uploads PDF resume
   .Stores submission in Snowflake
   .Shows message: "Assessment link will be emailed if your resume passes ATS filter

2. ATS Resume Filtering (Python + NLP)
   .Keywords and skill extraction
   .Semantic similarity scoring
   .Computes ATS Score (0–100)
   .If ATS score ≥ threshold → Assessment link is emailed

3. Assessment Workflow
   .Candidate receives secure link via email
   .Takes the MCQ/coding assessment
   .System auto-grades and stores the result
   .Assessment score compared with threshold

4. Final Composite Scoring
   .Only candidates who pass both gates are evaluated further:
   .Resume Score
   .Application Form Answer Score
   .Assessment Score
   .All three combined to calculate a composite AI score.

5. Recruiter Dashboard (Power BI)
   .View top candidates
   .Filter by ATS, Assessment, Final Score
   .View resume + answer summaries
   .Transparent score breakdown 

Why This Project Is Useful?
Recruiters handle thousands of applications.
Manually checking resumes → giving tests → filtering answers is slow.

This system automates:
.Resume screening
.Assessment distribution
.Scoring
.Shortlisting
.Candidate ranking
.It reduces workload by 70–80% and improves fairness & consistency.

Process Flow:
1.Candidate Submission:
   Candidate visits the Streamlit app and:
   .Fills personal details
   .Uploads resume (PDF only)
   .Answers basic application questions
   .Data is stored in Snowflake.

2.ATS Scoring:
  .Backend extracts resume text → matches:
  .Skills
  .Keywords
  .Role requirements
  .Basic semantic similarity
  .If ATS Score ≥ ATS_MIN, candidate moves forward.
  .Else → application ends here.

3.Assessment Link Generation:
   If ATS passes:
  .System generates secure assessment token
  .Sends assessment link to candidate via email

4.Candidate Completes Assessment:
   Candidate opens link → takes assessment:
   .MCQs
   .Optional coding tasks
   .Auto-graded by Python backend
   .the assessment score is stored in Snowflake.

5.Assessment Gate:
  .If Assessment Score ≥ ASSESSMENT_MIN, proceed to HR evaluation.
  .Else → candidate rejected.

6.Composite AI Scoring:
  .For candidates who pass both gates:
   final_score = 0.4 * resume_score + 0.3 * application_answer_score + 0.3 * assessment_score

7.Recruiter Shortlist
  .Power BI dashboard shows:
  .Final Score
  .ATS Score
  .Assessment Score
  .Resume keywords
  .Application answers
  .HR recommendation
  .Recruiter reviews only shortlisted profiles.

System Architecture:
       Streamlit UI (Resume + Form)
        ↓
      Python Backend (ATS + Scoring)
        ↓
      Snowflake (Store all data)
        ↓
      Assessment Engine (MCQ/Coding)
        ↓
      Final Scoring Logic
        ↓
      Power BI Dashboard

Azure handles:
   .Deployment
   .Storage of resumes 
   .Email sending
   .Key Vault for secrets

Tech Stack:
  .Frontend : Streamlit
  .Backend : Python
             NLP 
             ATS scoring logic
  .Database / DW : Snowflake
  .Cloud : Azure App Service 
           Azure Blob Storage
           Azure Key Vault
           Azure Function (email sending)
  .Visualization : Power BI


  
