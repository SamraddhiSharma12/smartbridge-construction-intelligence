Multimodal Construction Intelligence Platform

Skill Wallet Capstone Project 1

A Streamlit web app that uses Google Gemini to audit construction-site photos, diagnose concrete cracks, estimate project cost and asset value, and answer daily site questions with weather-aware advice.

Disclaimer: AI-assisted output for screening and planning only. It does not replace inspection by a licensed structural engineer or certified safety officer.

Features
Tab	What it does
Site Safety & PPE Audit	Upload a site photo. Gemini returns a safety score, worker count, PPE status (helmet, vest, boots, harness) and a list of hazards with severity, the relevant standard (OSHA 1926 / IS 456) and a corrective action.
Crack Diagnostics	Upload a concrete or masonry image. Returns defect type, estimated crack width, severity, urgency, structural integrity score, root causes and recommended repairs (IS 456, IS 13935).
Planning & Valuation	Choose structure type, area, city tier and completion %. Calculates budget, capex incurred, current asset value, steel and cement requirements, milestone progress, and can generate a conceptual 3D render.
Daily Site Assistant	Pick today's weather and get a safety advisory. Chat with an engineering assistant that factors the weather into its answers.

Other details:

Demo mode: without an API key the app still runs and shows built-in sample output, with a banner so it is not mistaken for a real analysis.
JSON export: safety and crack reports can be downloaded as JSON.
Image preprocessing: EXIF orientation is fixed and images are resized to at most 1600 px before being sent to the model.
Tech Stack
Python 3.10+
Streamlit (UI)
Google Gemini via google-genai (model: gemini-2.5-flash)
Pillow (image processing)
Requests (concept render via Pollinations)

No database is used. All state lives in the Streamlit session.

How It Works
Upload image
   -> Pillow preprocessing (EXIF fix, resize)
   -> Gemini with a structured prompt, JSON-only response
   -> JSON parsed and validated
   -> Cards, scores, tables and downloadable report

The planning tab does not call the AI. It uses a rule-based cost model with the constants below.

// to run project
python -m streamlit run "path of folder" 
