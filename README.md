# Job Application Tracker — Automated with Make & Groq AI

A simple but powerful automation I built to track every job I apply to and automatically generate a follow-up email for each one — without doing anything manually after submitting the form.

---

## What It Does

1. I fill out a Google Form with the company name, job title, date applied, and job posting URL
2. The form response automatically saves to Google Sheets
3. Make (formerly Integromat) detects the new row
4. It calls the Groq AI API to generate a personalized follow-up email
5. The email gets written directly into column F of the same row — ready to send

No manual work after step 1.

---

## Tools Used

- **Google Forms** — to collect job application details
- **Google Sheets** — to store and organize all applications
- **Make (Integromat)** — to connect everything and run the automation
- **Groq AI API** — to generate the follow-up email (free tier)
- **HTTP Module** — to connect Make to the Groq API

---

## How the Make Workflow Works

```
Google Sheets (Watch New Rows)
        ↓
HTTP Request → Groq AI API (generates follow-up email)
        ↓
Google Sheets (Update a Cell → writes email to column F)
```

Every time a new row is added to the sheet (via the Google Form), Make picks it up, sends the job details to Groq AI, and writes the generated email back into the spreadsheet automatically.

---

## Google Sheet Structure

| Column | Field |
|--------|-------|
| A | Timestamp |
| B | Company Name |
| C | Job Title |
| D | Date Applied |
| E | Job Posting URL |
| F | AI-Generated Follow-up Email ← written automatically |

---

## Screenshots

### Make Automation Canvas
<img width="956" height="987" alt="image" src="https://github.com/user-attachments/assets/e03a51ab-7475-4c55-b0f0-8f90b17e485b" />

### Google Sheet with Auto-Generated Emails
<img width="1337" height="786" alt="image" src="https://github.com/user-attachments/assets/5b9ee4c8-b435-465a-b0a3-93570fd49116" />

---

## What I Learned Building This

- How to connect multiple apps using Make (no-code automation)
- How to make HTTP requests to an external AI API from within a workflow
- How to map variables between different steps in an automation
- How to read from and write to specific cells in Google Sheets automatically
- Debugging workflow errors (row number mapping, API authentication, model deprecation)

---

## How to Set This Up Yourself

1. Create a Google Form with fields: Company Name, Job Title, Date Applied, Job Posting URL
2. Link the form to a Google Sheet
3. Create a free account at [make.com](https://make.com)
4. Create a free Groq API key at [console.groq.com](https://console.groq.com)
5. Build the 3-step scenario in Make:
   - **Step 1:** Google Sheets — Watch New Rows
   - **Step 2:** HTTP — POST request to `https://api.groq.com/openai/v1/chat/completions`
   - **Step 3:** Google Sheets — Update a Cell (write to column F)
6. Turn on the scenario and submit a test form response

---

## Author

**Adarsh Thoppil Shibu**  
Red Deer, AB  
[github.com/Adarshthoppilshibu](https://github.com/Adarshthoppilshibu)
