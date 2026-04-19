# Example Workflow

This document illustrates a practical multi-agent workflow in an enterprise setting.

## Overview

The following example demonstrates how a multi-agent system handles an inbound commercial enquiry and produces a structured outcome.

Use case:
> A prospective client requests information about deploying an AI solution.

The system:
- classifies the request
- gathers requirements
- retrieves relevant information
- constructs a response
- proposes next actions

---

## Workflow Summary

Client  
→ Routing Agent  
→ Sales Agent  
→ Research Agent  
→ Execution Agent  
→ Response

---

## Step-by-Step Flow

### 1. Inbound Request

User submits:

> "We run a financial services firm and want an AI agent to handle customer queries and qualify leads. Can this integrate with our CRM?"

The request is sent to the API with:
- full message history
- context (industry, region, source)
- permitted tools

---

### 2. Routing

The routing agent evaluates:
- intent (commercial enquiry)
- domain (enterprise AI deployment)
- required capabilities (sales + technical explanation)

Decision:
→ Route to **Sales Agent**

---

### 3. Sales Agent (Engagement + Qualification)

Responsibilities:
- clarify requirements
- frame the solution
- guide conversation

Output:
- identifies key requirements:
  - CRM integration
  - knowledge base support
  - lead qualification workflow

- generates follow-up questions:
  - which CRM platform?
  - expected volume of enquiries?
  - compliance constraints?

- determines next step:
→ invoke Research Agent for supporting detail

---

### 4. Research Agent (Information Retrieval)

Responsibilities:
- retrieve relevant architecture patterns
- identify integration approaches
- provide structured supporting data

Sources:
- internal knowledge base
- prior deployment patterns
- integration templates

Output:
- CRM integration methods (API / webhook / middleware)
- deployment patterns for financial services
- compliance considerations (data handling, audit trails)

---

### 5. Execution Agent (Response Construction)

Responsibilities:
- synthesise outputs from Sales and Research agents
- generate structured response
- prepare next actions

Output includes:
- concise explanation of solution
- tailored to client context
- suggested deployment approach
- recommended next steps

---

### 6. Tool Invocation (Optional)

If enabled, the system may:
- log the lead in CRM
- tag opportunity type
- trigger follow-up workflow
- schedule a meeting

All tool calls are:
- explicit
- permissioned
- logged

---

### 7. Final Response

Returned to client:

- clear answer to question
- explanation of capabilities
- relevant technical reassurance
- next-step guidance

Example:

> "Yes, the system can integrate with your CRM via API or middleware. A typical deployment would separate customer-facing automation from internal lead qualification, with structured routing and audit controls. For a firm of your size, we would recommend..."

---

### 8. Next Actions

System suggests:

- confirm CRM platform
- assess data sources
- define compliance requirements
- schedule discovery call

---

## Key Observations

### Separation of Concerns
- Sales agent handles interaction
- Research agent handles knowledge retrieval
- Execution agent constructs final output

### Controlled Tool Use
- Agents request actions
- System executes through governed layer

### Structured Outputs
- Responses include metadata and next actions
- Enables downstream automation

### Observability
Each step can be logged and analysed:
- routing decisions
- agent outputs
- tool usage
- response quality

---

## Variations

This workflow can be adapted for:

### Support Automation
Routing → Support Agent → Knowledge Retrieval → Resolution

### Internal Assistants
Routing → Knowledge Agent → Tool Invocation → Response

### Process Automation
Routing → Workflow Agent → Execution → Status Update

---

## Summary

This example demonstrates how multi-agent orchestration:
- decomposes complex tasks
- coordinates specialised agents
- integrates with enterprise systems
- produces structured, actionable outcomes

The goal is not just to generate responses, but to execute controlled, measurable workflows aligned to business objectives.
