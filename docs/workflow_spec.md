# Workflow Specification for Agent-Driven Activation MVP  

## Overview  

This minimal workflow outlines how to build an agent-driven activation MVP using OpenAI Agents (via the Responses API and AgentKit), Google's Gemini Builder with Bolt.Neo / Windsurf IDE, and custom toolchains. The goal is to onboard merchants, schedule activations, collect data, and generate reports.  

The design follows principles from Faktion's six ‑step agentic workflow framework, which emphasises laying out the end ‑to ‑end process, mapping triggers, and cataloguing required data ([www.faktion.com](https://www.faktion.com/post/designing-agentic-ai-workflows-our-insights-for-each-of-the-6-steps#:~:text=Workflow%20Design%20Step%201%3A%20Laying,Their%20Types%20After%20mapping%20the)). It also recommends defining agent types suited to each task (e.g., research agents, action ‑executing agents, conversational agents, structured ‑output agents) ([www.faktion.com](https://www.faktion.com/post/designing-agentic-ai-workflows-our-insights-for-each-of-the-6-steps)). OpenAI’s Responses API and Agents SDK provide built‑in tools such as web search, file search and computer use to simplify orchestration ([openai.com](https://openai.com/index/new-tools-for-building-agents/)). OpenAI AgentKit adds a visual canvas, ChatKit UI components, connector registry, testing/evaluation and guardrails ([inceptasolutions.com](https://inceptasolutions.com/building-production-ready-ai-agents-with-openai-agent-builder-technical-guide/)). Automated merchant onboarding uses AI to replace manual verifications and integrate merchants into payment systems quickly and securely ([xplorpay.com](https://xplorpay.com/blog/automated-merchant-onboarding/)).  

## Agents and Roles  

- **Merchant Onboarding Agent (Action ‑Executing Agent)**:  
  - Collects merchant details (legal name, address, business model, ID/KYC documents).  
  - Uses integrated KYC/AML API connectors via OpenAI AgentKit's connector registry to verify identity and compliance.  
  - Creates merchant account in payment platform and stores credentials securely.  
  - Sends confirmation once onboarding is complete.  

- **Activation Scheduler Agent (Action ‑Executing + Conversational Agent)**:  
  - Interacts with merchant to agree on activation date/time and requirements.  
  - Integrates with calendar APIs (e.g., Google Calendar / internal scheduling) to book onboarding calls and system activations.  
  - Sends reminders and updates.  

- **Data Collector Agent (Structured ‑Output Agent)**:  
  - After activation, periodically fetches transaction and usage data via connector APIs.  
  - Normalises data into structured JSON/CSV formats.  
  - Stores data in a database or data lake for analysis.  

- **Reporting Agent (Structured ‑Output + Research Agent)**:  
  - Aggregates collected data to generate periodic reports (daily/weekly/monthly).  
  - Computes metrics such as transaction volume, success rates, activation completion, and merchant engagement.  
  - Produces human‑readable markdown or PDF reports and can trigger visual dashboards.  

## Workflow Steps  

1. **Groundwork & Data Mapping** ([www.faktion.com](https://www.faktion.com/post/designing-agentic-ai-workflows-our-insights-for-each-of-the-6-steps#:~:text=Workflow%20Design%20Step%201%3A%20Laying,Their%20Types%20After%20mapping%20the))  
   - Define end ‑to ‑end merchant activation process: onboarding → activation scheduling → data collection → reporting.  
   - Identify triggers (e.g., merchant signs up) and expected outcomes.  
   - Catalogue required data: merchant KYC data, activation schedule, transaction logs, reporting metrics.  

2. **Define Agents & Choose Types** ([www.faktion.com](https://www.faktion.com/post/designing-agentic-ai-workflows-our-insights-for-each-of-the-6-steps))  
   - Assign each stage to a specialised agent.  
   - Onboarding and scheduling require action ‑executing agents with conversational capabilities; data collection and reporting use structured ‑output and research agents.  

3. **Equip Agents with Tools & Data**  
   - Use OpenAI Responses API built‑in tools (web search, file search, computer use) to perform external tasks ([openai.com](https://openai.com/index/new-tools-for-building-agents/)).  
   - Leverage OpenAI AgentKit connectors to integrate KYC systems, calendars, databases and analytics platforms ([inceptasolutions.com](https://inceptasolutions.com/building-production-ready-ai-agents-with-openai-agent-builder-technical-guide/)).  

4. **Orchestration & Observability**  
   - Use AgentKit’s visual builder to connect nodes representing each agent and control flow (e.g., if‑else for approval outcomes).  
   - Implement guardrails for PII detection, jailbreak protection and hallucination detection as per AgentKit’s safety features ([inceptasolutions.com](https://inceptasolutions.com/building-production-ready-ai-agents-with-openai-agent-builder-technical-guide/)).  
   - Add evaluation tests for each agent to monitor performance over time.  

5. **Iterate & Improve**  
   - Start with minimal flows and gradually expand capabilities.  
   - Capture merchant and operator feedback via the conversational agent, and iterate on prompts and tools.  

## Repository Structure  

- `README.md` – high ‑level project overview.  
- `docs/workflow_spec.md` – this workflow specification.  
- `src/` – directory for agent scripts or configuration (empty placeholder). 
