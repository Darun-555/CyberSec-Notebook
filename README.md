# 🛡️ CyberSecNode — Agentic Cybersecurity Investigation Notebook

CyberSecNode is a single-page cybersecurity investigation prototype built with **HTML, CSS, and JavaScript**. It works like a lightweight, cybersecurity-focused notebook assistant where analysts can upload threat reports, logs, alerts, or sandbox outputs and use an AI agent to extract useful security intelligence.

The application uses the **Gemini API** to analyse uploaded evidence, generate an analyst summary, extract Indicators of Compromise, map behaviours to MITRE ATT&CK, generate detection rules, build an incident timeline, and support AI-powered investigation chat.

---

## 🚀 Project Overview

CyberSecNode is designed for SOC, DFIR, malware-analysis, and threat-intelligence workflows.

The system allows users to:

* 📂 Upload cybersecurity evidence files
* 🤖 Use an AI agent to analyse uploaded material
* 🧠 Ask questions about local evidence
* 🌐 Perform live threat-intelligence enrichment using Google Search grounding
* 🧾 Generate an analyst summary
* ⏱️ Build an incident timeline
* 🛡️ Extract Indicators of Compromise
* 🎯 Map behaviours to MITRE ATT&CK
* 🕸️ Visualise entity relationships
* ⚠️ Extract CVE intelligence
* 📜 Generate Sigma/YARA-style detection rules

---

## ✨ Key Features

### 📂 Evidence Upload

Users can upload multiple files into the local knowledge base.

Supported file types include:

```text
.txt
.json
.csv
.log
.md
.xml
.yml
.yaml
.rules
.conf
```

Uploaded evidence is read directly in the browser and added to the investigation workspace.

---

### 🧪 Built-in Demo Scenario

The app includes a sample incident report involving:

* A suspicious executable
* A SHA256 hash
* Registry persistence
* PowerShell execution
* Payload download
* External IP communication
* A CVE reference
* Detection-engineering notes

This makes the prototype easy to demonstrate without needing external files.

---

### 🤖 Agentic Cybersecurity Workspace

The chat tab works as an AI-powered investigation workspace.

Users can ask questions such as:

```text
Why is this incident high risk?
```

```text
What are the most important IOCs?
```

```text
Generate an executive summary.
```

```text
Which MITRE ATT&CK techniques are visible in the evidence?
```

The agent uses the uploaded source material as local evidence and can also perform live web-search enrichment when needed.

---

### 🌐 Live Web Search Enrichment

The agent workspace includes live Google Search grounding for threat-intelligence enrichment.

This is useful for:

* IOC investigation
* CVE research
* Threat actor attribution
* Campaign lookup
* MITRE technique enrichment
* Recent threat-intelligence context

Example agent task:

```text
Investigate this IOC and identify associated threat actors, campaigns, or technical analysis.
```

---

### 🧾 Analyst Summary

After extraction, CyberSecNode generates a high-level summary containing:

* Threat level
* Likely malware type
* Key behaviours
* Recommended action

This gives analysts and judges a quick overview of the incident.

---

### ⏱️ Incident Timeline

The application builds a chronological timeline from uploaded evidence.

Example timeline events may include:

* Initial exploitation
* Privilege escalation
* Persistence creation
* Payload drop
* PowerShell execution
* External network communication

Each timeline event can also be investigated further using the agent deep-dive button.

---

### 🛡️ IOC Extraction

CyberSecNode extracts Indicators of Compromise using a hybrid approach:

1. Regex-based extraction
2. AI-assisted enrichment and classification

Supported IOC types include:

* IP addresses
* URLs
* CVEs
* SHA256 hashes
* Registry keys
* Windows file paths

Example extracted IOC:

```text
Type: IP
Value: 185.199.108.153
Risk: High
Source: Regex extraction
```

---

### 🎯 MITRE ATT&CK Mapping

The AI maps observed behaviours to MITRE ATT&CK-style tactics and techniques.

Example mappings:

| Evidence                      | Tactic              | Technique                          |
| ----------------------------- | ------------------- | ---------------------------------- |
| Encoded PowerShell command    | Execution           | Command and Scripting Interpreter  |
| Registry Run key modification | Persistence         | Registry Run Keys / Startup Folder |
| External payload download     | Command and Control | Application Layer Protocol         |

Each mapped technique can be investigated using the built-in agent action.

---

### 🕸️ Investigation Entity Graph

CyberSecNode creates a relationship graph from the uploaded evidence.

Example relationships:

```text
invoice_update_v2.exe → drops → temp_svc.exe
PowerShell → downloads → payload.bin
payload.bin → communicates with → 185.199.108.153
Malware sample → modifies → Registry Run Key
```

This gives a visual overview of how entities are connected during the incident.

---

### ⚠️ CVE Intelligence

The app extracts CVEs mentioned in the evidence and displays:

* CVE ID
* Context status
* CISA KEV status
* Exploitation status
* Priority level

To avoid hallucinated vulnerability intelligence, the prompt instructs the AI not to guess KEV status. If verified KEV data is not available in the uploaded evidence, the result should be marked as unverified.

---

### 📜 Detection Rule Generation

CyberSecNode generates draft detection rules based on malicious behaviours found in the evidence.

Possible rule types include:

* Sigma
* YARA

Rules can be copied directly from the interface using the copy button.

> ⚠️ Generated rules are draft outputs and should be reviewed by a human analyst before operational use.

---

## 🧱 Tech Stack

| Component     | Technology                                              |
| ------------- | ------------------------------------------------------- |
| Frontend      | HTML                                                    |
| Styling       | Tailwind CSS CDN + custom CSS                           |
| Interactivity | Vanilla JavaScript                                      |
| Icons         | Lucide Icons                                            |
| AI Model API  | Gemini API                                              |
| AI Features   | Structured JSON extraction, chat, live search grounding |
| Deployment    | Static HTML file                                        |

---

## 📁 Project Structure

This prototype is contained in a single HTML file.

```text
CyberSecNode/
│
├── index.html
└── README.md
```

The `index.html` file includes:

* HTML layout
* Tailwind-based UI styling
* Custom CSS animations
* JavaScript application state
* Gemini API calls
* File upload handling
* Rendering functions
* IOC extraction logic
* Agent chat workflow
* Demo incident data

---

## 🔑 Requirements

To run the project, you need:

* A modern browser
* Internet connection
* Gemini API key
* Access to the Gemini API endpoint
* JavaScript enabled in the browser

No build system is required.

No React, TypeScript, Node.js, or backend server is required.

---

## ⚙️ How to Run

### 1. Download or clone the project

Save the main HTML file as:

```text
index.html
```

---

### 2. Open the file

Open `index.html` directly in a browser.

Recommended browsers:

* Google Chrome
* Microsoft Edge
* Firefox

---

### 3. Enter Gemini API Key

In the sidebar, enter your Gemini API key.

The key is required before running analysis or chat.

---

### 4. Select Model

The default model is:

```text
gemini-2.5-flash
```

Other selectable models may be available depending on your Gemini API access.

---

### 5. Load Demo or Upload Files

You can either:

* Click **Load Demo Scenario**
* Upload your own logs, reports, alerts, or sandbox files

---

### 6. Extract Intelligence

Click:

```text
Extract Intelligence
```

The app will generate:

* Analyst summary
* Timeline
* IOCs
* MITRE ATT&CK mappings
* Graph relationships
* Detection rules
* CVE intelligence

---

### 7. Use the Agent Workspace

Ask questions or trigger quick agent actions such as:

* ⚡ Top Risks
* 🔍 Attribution Search
* 📄 Draft Executive Report

---

## 🧪 Suggested Demo Flow

For a workshop presentation, use this flow:

1. Open the app
2. Enter Gemini API key
3. Click **Load Demo Scenario**
4. Click **Extract Intelligence**
5. Show the **Summary** tab
6. Show the **Timeline** tab
7. Show the **IOCs** tab
8. Show the **ATT&CK** tab
9. Show the **Investigation Graph**
10. Show generated **Detection Rules**
11. Ask the agent:

```text
Why is this incident high risk?
```

12. Click an IOC deep-dive button and show live enrichment

---

## 🧠 Agentic Workflow

CyberSecNode follows an agentic investigation workflow:

```text
Evidence Upload
      ↓
Source Ingestion
      ↓
Regex IOC Extraction
      ↓
AI Threat Analysis
      ↓
Timeline Construction
      ↓
MITRE ATT&CK Mapping
      ↓
CVE Identification
      ↓
Detection Rule Generation
      ↓
Agentic Q&A and Live Enrichment
```

This makes the prototype more than a simple chatbot. It behaves like an investigation assistant that performs multiple cybersecurity analysis steps.

---


### ✅ Functionality & Accuracy

CyberSecNode performs the intended cybersecurity investigation tasks by:

* Extracting IOCs
* Summarising incidents
* Mapping behaviours to ATT&CK
* Generating detection rules
* Producing timelines
* Supporting evidence-based Q&A

Regex extraction improves reliability for common indicators such as IPs, URLs, hashes, CVEs, registry keys, and Windows paths.

---

### ✅ Innovation & User Experience

The app provides a polished analyst-style interface with:

* Dark SOC dashboard design
* Sidebar knowledge base
* Tabbed investigation workspace
* Visual incident timeline
* Entity relationship graph
* Agent deep-dive buttons
* Quick action prompts
* Live-search enrichment

---

### ✅ Technical Implementation

The prototype demonstrates:

* Vanilla JavaScript state management
* Dynamic rendering
* FileReader API usage
* Gemini API integration
* Structured JSON output
* Live Google Search grounding
* Markdown-style response rendering
* IOC regex extraction
* Copy-to-clipboard functionality
* Single-file static deployment

---

## 🔐 Security Notes

This is a workshop prototype.

Important considerations:

* Do not upload sensitive or confidential logs unless permitted.
* Do not expose a permanent API key in public demos.
* Use a temporary API key with quota restrictions.
* Generated detections should be manually reviewed.
* AI-generated MITRE mappings and CVE interpretations should be validated before operational use.

---

## ⚠️ Limitations

CyberSecNode is a prototype and has some limitations:

* No backend authentication
* No persistent database
* No vector database or full RAG pipeline
* Browser-based API key entry
* No formal Sigma/YARA validation
* Large files may affect browser performance
* AI outputs may require analyst verification
* Live search depends on model and API support

---
## 📸 Screenshots
<img width="1535" height="727" alt="Screenshot 2026-06-23 181003" src="https://github.com/user-attachments/assets/87fbd174-294e-4445-b0ac-1d5abfc9cffd" />

<img width="1536" height="728" alt="image" src="https://github.com/user-attachments/assets/8cd58fe3-3451-4d19-b290-6acd06587c3e" />

---

## 🚧 Future Improvements

Possible improvements include:

* Add backend API proxy
* Store API key securely on server side
* Add source citations and line references
* Add vector search over uploaded evidence
* Validate Sigma/YARA syntax
* Integrate CISA KEV API
* Integrate NVD CVE API
* Add MITRE ATT&CK official dataset lookup
* Add interactive graph visualisation
* Add export to PDF or Markdown report
* Add project/session saving
* Add authentication for multi-user use

---

## 🧑‍💻 Author

Developed as a cybersecurity workshop prototype.

Project name:

```text
CyberSecNode
```

Tagline:

```text
An Agentic Cybersecurity Investigation Notebook
```

---

## 📄 License

This project is intended for educational and workshop demonstration purposes.

You may adapt and extend it for learning, prototyping, or security research demonstrations.

---

## ⭐ Summary

CyberSecNode turns raw cybersecurity evidence into structured intelligence.

It helps analysts move from:

```text
Unstructured reports and logs
```

to:

```text
Actionable investigation summary, IOCs, ATT&CK mappings, timelines, graphs, CVEs, rules, and AI-assisted briefings
```

All inside a lightweight browser-based investigation notebook.

🛡️ **CyberSecNode = Upload evidence. Extract intelligence. Investigate faster.**
