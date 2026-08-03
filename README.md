# 🚀 Project 01 — Intelligent Lead Processing Platform

> AI-powered lead qualification and routing system built with n8n, OpenAI, Google Calendar, and Google Sheets.

![n8n](https://img.shields.io/badge/n8n-Automation-orange)
![OpenAI](https://img.shields.io/badge/OpenAI-Artificial%20Intelligence-green)
![Google Calendar](https://img.shields.io/badge/Google%20Calendar-Integration-blue)
![Google Sheets](https://img.shields.io/badge/Google%20Sheets-Data%20Storage-brightgreen)
![Webhook](https://img.shields.io/badge/Webhook-API-purple)
![JavaScript](https://img.shields.io/badge/JavaScript-Logic-yellow)

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
