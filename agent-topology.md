# Agent Topology

This document describes common topologies for structuring multi-agent systems in production environments.

## Overview

Agent topology defines how agents are arranged, how they communicate, and how control flows through the system.

A good topology should:
- reflect clear functional boundaries
- minimise unnecessary coordination overhead
- support observability and control
- remain adaptable as workflows evolve

The correct topology depends on the task complexity, execution model, and operational constraints.

---

## 1. Centralised Routing Topology

In this model, a central routing agent receives requests and delegates work to specialist agents.

### Structure

Client  
→ Routing Agent  
→ Specialist Agent A  
→ Specialist Agent B  
→ Specialist Agent C  

### Characteristics

- Clear control point
- Easy to observe and govern
- Straightforward to implement
- Suitable for most enterprise use cases

### Typical use cases

- Sales qualification
- Support triage
- Internal knowledge workflows
- Request classification and delegation

### Trade-offs

Advantages:
- simple control model
- strong governance
- predictable delegation paths

Limitations:
- routing agent can become a bottleneck
- central logic can become complex over time

---

## 2. Hierarchical Topology

A higher-level orchestration agent delegates tasks to manager agents, which then coordinate specialist sub-agents.

### Structure

Client  
→ Orchestrator Agent  
→ Manager Agent  
→ Specialist Agents  

### Characteristics

- Supports decomposition of large workflows
- Useful where work must be broken into multiple stages
- Provides strong structural control

### Typical use cases

- Proposal generation
- Multi-stage research workflows
- Long-form document production
- Complex business process automation

### Trade-offs

Advantages:
- handles complexity well
- supports layered responsibility
- easier to scale by functional area

Limitations:
- more orchestration overhead
- greater implementation complexity
- slower debugging if poorly instrumented

---

## 3. Sequential Pipeline Topology

Each agent performs one step in a fixed sequence.

### Structure

Client  
→ Agent 1  
→ Agent 2  
→ Agent 3  
→ Output

### Characteristics

- Linear flow
- Each stage transforms or augments output
- Well suited to repeatable workflows

### Typical use cases

- Input classification → retrieval → response generation
- Lead intake → qualification → proposal drafting
- Data extraction → validation → action execution

### Trade-offs

Advantages:
- easy to reason about
- deterministic flow
- good for standardised processes

Limitations:
- less flexible
- failures in one stage can block the full flow
- harder to adapt to variable task structures

---

## 4. Parallel Specialist Topology

Multiple specialist agents work concurrently on different aspects of the same task, and a coordinator combines the results.

### Structure

Client  
→ Coordinator Agent  
→ Specialist Agent A  
→ Specialist Agent B  
→ Specialist Agent C  
→ Aggregated Response

### Characteristics

- Improves speed for decomposable tasks
- Useful where multiple perspectives are valuable
- Requires careful aggregation logic

### Typical use cases

- Research across multiple domains
- Risk, legal, and commercial analysis in parallel
- Multi-perspective evaluation of plans or outputs

### Trade-offs

Advantages:
- lower end-to-end latency in some workflows
- richer outputs
- good decomposition model for independent subtasks

Limitations:
- more complex aggregation
- inconsistent output quality across agents
- possible duplication of effort

---

## 5. Event-Driven Topology

Agents react to events, triggers, or state changes rather than being invoked in a single synchronous chain.

### Structure

Event Source  
→ Event Bus / Queue  
→ Triggered Agent(s)  
→ Action / Update / Notification

### Characteristics

- Decoupled execution model
- Suitable for asynchronous workflows
- Supports automation across systems

### Typical use cases

- Inbound form submissions
- CRM updates
- support ticket creation
- monitoring and alerting workflows

### Trade-offs

Advantages:
- scalable
- resilient
- well suited to business process automation

Limitations:
- more infrastructure complexity
- harder to trace if observability is weak
- state consistency requires care

---

## 6. Shared Memory Topology

Agents operate with access to a common memory or context store.

### Structure

Client  
→ Agent Network  
↔ Shared Memory Layer  
↔ Tool Layer

### Characteristics

- Supports continuity across long-running workflows
- Useful where multiple agents need access to evolving context
- Can reduce repeated context passing

### Typical use cases

- persistent assistants
- long-duration business workflows
- project-based multi-agent collaboration

### Trade-offs

Advantages:
- better continuity
- reduced duplication of context
- stronger support for collaborative behaviour

Limitations:
- memory consistency becomes important
- hidden state can reduce predictability
- governance becomes more complex

---

## 7. Hybrid Topology

Most production systems combine multiple patterns.

Example:

Client  
→ Routing Agent  
→ Parallel Research Agents  
→ Sequential Validation Stage  
→ Execution Agent  
→ Output

This is often the most practical model because real workflows are rarely uniform.

---

## Choosing the Right Topology

Selection depends on:

### Workflow complexity
Simple workflows often benefit from centralised or sequential models.

### Need for control
Highly governed environments often favour centralised routing or hierarchical structures.

### Need for speed
Parallel topologies can reduce latency where tasks are independent.

### Need for continuity
Shared memory models support persistent or multi-session workflows.

### Operational maturity
Simpler topologies are easier to deploy, monitor, and debug.

---

## Recommended Enterprise Starting Point

A strong default pattern for enterprise systems is:

- central routing agent
- specialist domain agents
- governed tool execution layer
- optional memory layer
- structured observability throughout

This provides a good balance of:
- clarity
- scalability
- governance
- extensibility

---

## Summary

Agent topology is not just a design choice. It directly affects:
- scalability
- debuggability
- governance
- latency
- business reliability

The most effective multi-agent systems use topology deliberately, with clear operational reasoning behind the design.

In most enterprise settings, the right answer is not maximum complexity. It is the simplest topology that can support the required workflow safely and predictably.
