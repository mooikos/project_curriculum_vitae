# AGENTS.md — CV Tailoring & Maintenance Workflow

## Project Goal
Assist **Massimiliano De Vivo** in maintaining his master CV data (`../master_info.json`) and generating job-specific, ATS-parsable LaTeX resumes (`./adapted_master_info.tex`) and cover letters (`./anschreiben.tex` / `./anschreiben.md`) tailored to target job descriptions (`../target_job_ad.text`).

## Key Files & Paths
- `../master_info.json`: Single source of truth for personal details, work history, education, certifications, languages, and verified skills/competences.
- `../target_job_ad.text`: The current target job description (frequently replaced by the user between prompts).
- `./adapted_master_info.tex`: Output LaTeX resume using the `jakegut/resume` (`sb2nov/resume`) single-column template structure.
- `./anschreiben.tex` & `./anschreiben.md`: Optional LaTeX and Markdown cover letters when requested.
- `../README.md`: Prompt template and Docker build instructions.

## Core Rules for the Agent
1. **Always Re-Read Before Writing**: Always re-read `../master_info.json`, `../target_job_ad.text`, and `./adapted_master_info.tex` immediately before generating or editing files, as the user frequently updates them manually.
2. **Never Invent Experience**: Do not fabricate tools, frameworks, domains, or CEFR language levels. If a job ad mentions skills or responsibilities not yet in `../master_info.json`, ask concise multiple-choice questions (`ask_question`) to verify what the user has genuinely done.
3. **Persist & Condense in `../master_info.json`**:
   - When the user confirms new skills, tools, or responsibilities, persist them into `../master_info.json`.
   - Keep `../master_info.json` **concise, unified, and deduplicated**: use short, atomic competence keywords in `skills` and compact, non-redundant bullet points in `experience`. Avoid bloated or repetitive sentences.
4. **Tailoring & Formatting (`./adapted_master_info.tex`)**:
   - Select only the most relevant skills, tools, and experience bullets for the target job ad.
   - Subtly mirror the job ad's keywords and terminology while remaining 100% truthful.
   - Keep the resume concise (1–2 pages max) and use pure ASCII LaTeX (`---` for em-dash, escaped `\&`, `\%`, etc.) in the `jakegut/resume` template structure.
   - Default CV language is **English** and German level is **Intermediate** unless explicitly instructed otherwise.
5. **No Docker Execution Needed**: The user compiles the PDF themselves via Docker (`docker run --rm -i -v "$PWD":/data latex pdflatex adapted_master_info.tex`).
