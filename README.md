# S.A.F.E.: Smart AI Framework for Emergencies

**S.A.F.E.** is a multimodal AI emergency-response copilot designed to connect people in crisis with emergency responders. It transforms voice reports, local-language input, and images into structured, actionable triage information using Google's **Gemma 4**.

Built for the **"Build with Gemma" Hackathon**.

## The Problem

During disasters, victims may not have the time, connectivity, or ability to complete traditional text-based emergency forms. Responders, meanwhile, often receive fragmented and unstructured reports, making it difficult to determine which incidents require immediate attention.

S.A.F.E. reduces this communication gap by allowing people to report emergencies naturally while automatically converting their reports into structured information for responders.

## Key Features

* **Panic Mode:** A simplified victim interface designed for fast emergency reporting with minimal typing.
* **Multimodal Reporting:** Accepts voice recordings, images, and natural-language descriptions.
* **Local Language Support:** Designed to handle languages and dialects commonly used in Nigeria, including English, Nigerian Pidgin, Hausa, Yoruba, and Igbo.
* **AI-Powered Triage:** Uses Gemma 4 to identify incident types, hazards, casualty estimates, and urgency.
* **Responder Dashboard:** Provides a centralized view of incoming incidents with filtering and prioritization.
* **Structured Incident Data:** Converts unstructured reports into consistent JSON records for reliable processing and storage.

## Gemma 4 Integration

Gemma 4 acts as the core intelligence layer of S.A.F.E. Instead of using the model only for conversational responses, the system leverages its multimodal capabilities and function-calling workflow to analyze emergency inputs and generate structured incident records.

Example output:

```json id="n4hr0x"
{
  "incident_type": "FLOODING",
  "triage_priority": "CRITICAL",
  "casualty_count_estimate": 3,
  "hazards_detected": [
    "ELECTRICAL_HAZARD",
    "RISING_WATER"
  ]
}
```

The structured information is stored in a local SQLite database and made available to the responder dashboard for filtering, prioritization, and incident monitoring.

## Tech Stack

**Python 3.12 | Streamlit | SQLite | Google GenAI SDK | Gemma 4 | Plotly**

## Repository Structure

```text id="h6y1r3"
├── src/
│   ├── core/
│   │   ├── llm_provider.py
│   │   ├── database.py
│   │   └── function_executor.py
│   └── utils/
│       ├── image_processor.py
│       └── audio_processor.py
├── .env.example
├── .gitignore
├── requirements.txt
├── responder_dashboard.py
└── victim_interface.py
```

The SQLite database is generated dynamically during runtime and is intentionally excluded from version control.

## Local Setup

### 1. Clone the repository

```bash id="1k0s8m"
git clone https://github.com/YourUsername/SAFE-Deploy.git
cd SAFE-Deploy
```

### 2. Create a virtual environment

```bash id="a2j4b6"
python -m venv venv
venv\Scripts\activate
```

For macOS/Linux:

```bash id="7j4r2n"
source venv/bin/activate
```

### 3. Install dependencies

```bash id="f6w9k2"
pip install -r requirements.txt
```

### 4. Configure environment variables

Create a `.env` file using `.env.example` as a template:

```env id="x7c4p1"
GOOGLE_API_KEY=your_actual_key_here
GEMMA_MODEL=gemma-4-26b-a4b-it
```

### 5. Run the applications

Start the victim interface:

```bash id="v1s8q3"
streamlit run victim_interface.py
```

Then, in a second terminal, start the responder dashboard:

```bash id="k3n6w2"
streamlit run responder_dashboard.py
```

## Why S.A.F.E.?

S.A.F.E. is designed around the reality that emergency infrastructure may fail precisely when it is needed most. By reducing dependence on complex reporting workflows and turning natural human input into structured emergency data, the system can help responders process incidents more efficiently.

The project also provides a foundation for adapting AI-powered emergency tools to regions where connectivity, infrastructure, language, and access to centralized emergency services remain significant challenges.

## Future Roadmap

The current MVP uses Streamlit and the Gemma API to demonstrate the complete emergency-reporting workflow. Future iterations will focus on **offline-first and edge deployment**, using quantized Gemma models on local hardware.

Planned improvements include local inference, offline maps, store-and-forward synchronization, low-power deployments, and community-based emergency hubs. These improvements aim to keep critical functionality available even during network and infrastructure outages.

## Built For

**GDG UNN — Build with Gemma Hackathon**

Built with **Python, Streamlit, SQLite, Google GenAI, and Gemma 4**.
