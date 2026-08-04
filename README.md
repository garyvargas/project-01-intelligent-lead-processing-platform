# 🚀 Project 01 — Intelligent Lead Processing Platform

> AI-powered lead qualification and routing system built with n8n, OpenAI, Google Calendar, and Google Sheets.

![n8n](https://img.shields.io/badge/n8n-Automation-orange)
![OpenAI](https://img.shields.io/badge/OpenAI-Artificial%20Intelligence-green)
![Google Calendar](https://img.shields.io/badge/Google%20Calendar-Integration-blue)
![Google Sheets](https://img.shields.io/badge/Google%20Sheets-Data%20Storage-brightgreen)
![Webhook](https://img.shields.io/badge/Webhook-API-purple)
![JavaScript](https://img.shields.io/badge/JavaScript-Logic-yellow)

<img width="1148" height="488" alt="Project 1" src="https://github.com/user-attachments/assets/ed26516b-3c88-4a05-9b14-3b58b23f31d5" />

---

# 📌 Project Overview

The **Intelligent Lead Processing Platform** is an AI-powered automation system designed to help businesses automatically qualify, analyze, and route incoming leads.

The platform receives lead information through a webhook endpoint, validates and normalizes the incoming data, and uses OpenAI to evaluate the lead based on business criteria.

The AI model generates:

- Lead Score
- Priority Level
- Business Reasoning
- Recommended Next Action

Based on the AI evaluation, the workflow automatically routes each lead through different business processes:

- High-priority leads → Schedule a meeting, save lead information, and notify the requester.
- Medium-priority leads → Store lead information and provide a response.
- Low-priority leads → Store lead information and provide a response.

This project demonstrates how AI, APIs, automation workflows, and business integrations can work together to reduce manual processes and improve sales response times.

---

# 🎯 Business Problem

Many companies receive multiple inbound leads every day through different channels.

Without an automated qualification process, sales teams often spend valuable time manually reviewing requests, deciding which opportunities deserve immediate attention, and performing repetitive administrative tasks.

Common challenges include:

- Slow response times for high-value prospects.
- Inconsistent lead evaluation.
- Manual data entry.
- Lack of prioritization.
- Missed business opportunities.

This project solves this problem by creating an automated AI-driven pipeline capable of analyzing incoming leads and triggering the appropriate business actions automatically.

---

# 💡 Solution Overview

The solution implements an end-to-end AI automation workflow using n8n.

The system follows this process:

1. Receive lead information through a Webhook API.
2. Validate and prepare incoming data.
3. Normalize the lead information into a structured JSON format.
4. Send lead data to OpenAI for intelligent evaluation.
5. Analyze AI-generated scoring and recommendations.
6. Route the lead using conditional business logic.
7. Execute different actions depending on priority.
8. Store lead information for future reference.

The workflow acts as an intelligent sales assistant capable of making automated decisions based on AI-generated insights.

---

# 🏗️ Workflow Architecture

The Intelligent Lead Processing Platform is designed as an event-driven automation pipeline where incoming lead data is processed, analyzed using Artificial Intelligence, and routed through different business workflows depending on the generated priority.

The architecture separates the workflow into different stages:

1. Data Ingestion
2. Data Validation and Normalization
3. AI Analysis and Decision Making
4. Business Logic Routing
5. Automated Actions and Response

---

# 🔄 System Workflow

```text
                    Incoming Lead
                         |
                         ↓
                  Webhook Endpoint
                         |
                         ↓
              Validate Lead Information
                         |
                         ↓
              Normalize Lead Data (JSON)
                         |
                         ↓
                  OpenAI Analysis
                         |
                         ↓
        ┌────────────────────────────────┐
        │      AI Lead Evaluation        │
        │                                │
        │  - Lead Score                  │
        │  - Priority Level              │
        │  - Business Reasoning          │
        │  - Recommended Action          │
        └────────────────────────────────┘
                         |
                         ↓
                 Priority Router
                    (Switch)
                         |
        ┌────────────────┼────────────────┐
        ↓                ↓                ↓

      HIGH            MEDIUM             LOW

        ↓                ↓                ↓

Google Calendar   Save Lead         Save Lead
Meeting           Information       Information

        ↓                ↓                ↓

Save Lead         Respond           Respond
Information       Webhook            Webhook

        ↓
Respond
Webhook
```

---

# 🧩 Architecture Components

## 1. API Layer

Responsible for receiving external lead information.

**Technologies:**

- Webhooks
- JSON Payloads
- Postman

The workflow exposes an API endpoint capable of receiving structured lead data from external systems.

Example use cases:

- Website contact forms
- Marketing campaigns
- CRM integrations
- Sales inquiry forms

---

## 2. Data Processing Layer

Responsible for preparing incoming information before AI analysis.

Main responsibilities:

- Validate required fields.
- Normalize incoming data.
- Create a consistent JSON structure.
- Prepare information for AI processing.

This layer ensures that the AI model receives clean and predictable data.

---

## 3. AI Decision Layer

Responsible for analyzing the lead using OpenAI.

The AI model evaluates:

- Lead quality.
- Business opportunity.
- Potential urgency.
- Recommended next action.

The output is transformed into structured information that can be used by the automation workflow.

Example:

```json
{
  "leadScore": 85,
  "priority": "High",
  "reasoning": "The lead represents a strong business opportunity.",
  "recommendedAction": "Schedule a meeting"
}
```

---

## 4. Business Logic Layer

Responsible for deciding what action should happen after AI analysis.

The workflow uses a Switch node to route leads based on their priority:

### High Priority

Actions:

- Create Google Calendar meeting.
- Store lead information.
- Send webhook response.

### Medium Priority

Actions:

- Store lead information.
- Send webhook response.

### Low Priority

Actions:

- Store lead information.
- Send webhook response.

---

## 5. Data Storage Layer

Google Sheets is used as the initial data storage solution for lead records.

Stored information includes:

- Lead information.
- AI evaluation.
- Priority level.
- Processing results.

This approach provides a lightweight database solution during the prototype phase while keeping the architecture ready for future migration to production databases.

---

# 🧠 Engineering Design Decisions

## Structured JSON throughout the workflow

The workflow was designed around structured JSON objects to maintain consistency between nodes and simplify data processing.

This allows information to be reused across multiple steps without unnecessary transformations.

---

## Switch-based routing architecture

A Switch node was selected instead of multiple conditional branches because it provides a cleaner and more scalable way to handle different lead priorities.

Future priority levels can be added without redesigning the entire workflow.

---

## Separation between processing and actions

The workflow separates:

- Data preparation.
- AI analysis.
- Business actions.

This improves maintainability and makes debugging easier because each stage has a specific responsibility.

---

## AI-assisted decision making

OpenAI is used as a decision-support layer rather than simply generating text.

The model evaluates business context and produces structured outputs that directly influence automation behavior.

---

# 📊 High-Level Data Flow

```text
Lead Input
    ↓
Webhook Request
    ↓
Validated Data
    ↓
Normalized JSON Object
    ↓
OpenAI Lead Analysis
    ↓
Priority Classification
    ↓
Business Automation
    ↓
Final Response
```

---

# 📂 Project Structure

```text
project-01-intelligent-lead-processing-platform/

├── README.md                     # Project documentation
│
├── workflow/
│   └── .gitkeep                  # n8n workflow files
│
├── docs/
│   └── .gitkeep                  # Technical documentation
│
├── assets/
│   └── .gitkeep                  # Screenshots, diagrams and media
│
└── LICENSE                       # MIT License (to be added)
```

## Directory Overview

### README.md

Contains the complete project documentation, including architecture, setup instructions, lessons learned, troubleshooting, and future improvements.

### workflow/

Stores the exported n8n workflow files used by this project.

### docs/

Contains additional technical documentation that complements the main README.

### assets/

Stores project resources such as workflow screenshots, architecture diagrams, GIF demonstrations, and other visual assets.

---

# 🧠 AI Automation Engineering Lab

This repository is part of my **AI Automation Engineering Lab**, a practical learning environment focused on designing real-world automation systems using:

- n8n workflow automation
- Artificial Intelligence integrations
- APIs and Webhooks
- Data processing
- Business workflow design
- Debugging and optimization
- Production-oriented architecture

The goal of this laboratory is not only to build automations, but to understand the engineering principles behind scalable AI-powered systems.

---

# ✨ Features

- AI-powered lead qualification using OpenAI
- Automatic lead scoring and priority classification
- Intelligent business reasoning and recommended actions
- Event-driven workflow using Webhooks
- Conditional routing with n8n Switch nodes
- Automatic Google Calendar meeting creation for high-priority leads
- Google Sheets integration for lead storage
- JSON data normalization for consistent processing
- Modular workflow architecture
- Real-time API responses using Respond to Webhook
- Production-oriented workflow design

---

# 🛠️ Technologies Used

| Category | Technology |
|-----------|------------|
| Workflow Automation | n8n |
| Artificial Intelligence | OpenAI |
| Programming | JavaScript |
| APIs | Webhooks |
| Data Format | JSON |
| Database | Google Sheets |
| Calendar | Google Calendar |
| API Testing | Postman |
| Decision Logic | Switch Node |
| Data Transformation | Set Node, Code Node |

---

# ⚙️ Installation

## Prerequisites

- n8n installed (Cloud or Self-hosted)
- OpenAI API Key
- Google Cloud Project
- Google Calendar credentials
- Google Sheets credentials
- Postman (optional for testing)

## Setup

1. Clone this repository.
2. Import the workflow into n8n.
3. Configure all required credentials.
4. Update the environment variables.
5. Activate the workflow.
6. Test the webhook endpoint using Postman.

---

# 🔐 Required Credentials

The following credentials must be configured inside n8n:

| Service | Purpose |
|----------|---------|
| OpenAI | AI Lead Analysis |
| Google Calendar | Meeting Scheduling |
| Google Sheets | Lead Storage |

> No credentials are included in this repository.

---

# 🧪 Testing with Postman

The workflow can be tested by sending a POST request to the webhook endpoint.

Example request:

```json
{
  "name": "John Doe",
  "email": "john@example.com",
  "company": "Example Inc.",
  "message": "We are interested in learning more about your services."
}
```

Expected AI Output

```json
{
  "leadScore": 92,
  "priority": "High",
  "reasoning": "High-value B2B opportunity.",
  "recommendedAction": "Schedule a meeting"
}
```

Expected Workflow Behavior

High Priority

- Create Google Calendar meeting
- Save lead in Google Sheets
- Return JSON response

Medium Priority

- Save lead
- Return JSON response

Low Priority

- Save lead
- Return JSON response

---

# 🧩 Main Workflow Nodes

| Node | Purpose |
|------|---------|
| Webhook | Receives incoming lead data |
| Validate Lead | Validates required fields |
| Normalize Lead | Creates a standardized JSON object |
| OpenAI | Performs AI lead analysis |
| Parse AI Response | Extracts structured AI output |
| Switch | Routes leads by priority |
| Google Calendar | Creates meetings for high-priority leads |
| Google Sheets | Stores processed leads |
| Respond to Webhook | Returns API response |

---

# 🐛 Troubleshooting

## Missing JSON fields after Google Calendar

**Problem**

Google Calendar appeared to remove information from the workflow.

**Cause**

The node was incorrectly being used as part of the data flow.

**Solution**

Connect downstream nodes directly from the data preparation node instead of relying on Google Calendar to pass data forward.

---

## Missing Fields after Set Node

**Cause**

The Set node replaces the incoming JSON unless **Include Other Input Fields** is enabled.

**Solution**

Enable **Include Other Input Fields** whenever existing workflow data must be preserved.

---

## Expression Errors

Understanding when to use:

```text
{{$json.lead.email}}
```

versus

```text
{{ $('Normalize Lead').item.json.lead.email }}
```

was essential to correctly reference workflow data.

---

# 📚 Lessons Learned

During the development of this project I gained practical experience with:

- Designing production-style n8n workflows
- Structuring reusable JSON objects
- AI-assisted business decision making
- Google Calendar integration
- Google Sheets as lightweight data storage
- Debugging complete workflows node by node
- Respond to Webhook best practices
- Understanding Set node behavior
- Using Include Other Input Fields correctly
- Working with n8n expressions
- Separating data processing from business actions

---

# 🚀 Future Improvements

Potential production enhancements include:

- Duplicate lead detection
- CRM integration (HubSpot)
- CRM integration (Salesforce)
- Automatic Gmail notifications
- Slack notifications
- PostgreSQL database
- Redis caching
- Queue Mode
- Docker deployment
- Webhook authentication
- Rate limiting
- Monitoring dashboard
- Analytics and KPIs
- Automatic follow-up workflows
- AI-generated commercial proposals

---

# 📸 Repository Showcase

To improve the project presentation, include:

- Complete workflow screenshot
- Zoomed architecture screenshot
- OpenAI node configuration
- Google Calendar integration
- Google Sheets output
- Postman request example
- Workflow execution GIF
- Architecture diagram

---

# 📄 License

This project is licensed under the MIT License.

---

# 🙌 Credits

Developed by **Gary Vargas** as part of the **AI Automation Engineering Lab**.

This project was created to demonstrate practical AI automation engineering skills, including workflow architecture, AI integration, debugging, API design, and business process automation.

If you found this repository useful, feel free to connect with me on LinkedIn or explore the rest of the projects in this laboratory.
