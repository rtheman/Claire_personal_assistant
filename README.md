# 🤖 Cl(ai)re – AI Appointment Scheduling Assistant

Cl(ai)re is a friendly, voice-enabled AI assistant built to handle appointment scheduling, rescheduling, cancellations, and weather inquiries—entirely over voice. Designed with minimal code using modern tools like [ElevenLabs AI Agents](https://elevenlabs.io/), Cal.com APIs, and webhook integrations, Claire showcases how powerful, human-like assistants can be created without writing complex backend logic.

Currently, you can find this on bottom-right of [rtheman.com](rtheman.com), which looks something like this:
![image](https://github.com/user-attachments/assets/cdbd95b1-fae4-4a1b-af6f-b7cf0bc80719)




## 🧠 About This Project

**Cl(ai)re** acts as a conversational agent for booking and managing appointments through natural, voice-based interaction. It speaks **English and German** natively and responds with clarity, charm, and a bit of wit—perfect for both professional and casual contexts.

This project highlights how **low-code/no-code platforms** paired with thoughtful **system architecture and prompt design** can produce real-world, production-grade AI solutions.



## 💡 Why This Matters

Even as a seasoned data scientist and ML strategist, I wanted to demonstrate that **powerful AI systems don’t need to start with code**. This project proves:
- You can build intelligent assistants using voice, logic, APIs, and prompt engineering
- Conversational UX matters as much as backend logic
- No need to reinvent the wheel when excellent platforms like ElevenLabs and Cal.com exist

---

## 🛠️ Tech Stack & Architecture

| Component              | Description                                                                 |
|------------------------|-----------------------------------------------------------------------------|
| **ElevenLabs AI Agent** | No-code platform for building voice assistants with personality + logic    |
| **Cal.com API**         | Backend calendar platform for appointment booking, lookup, and scheduling |
| **Webhooks**            | Custom tools configured as API calls (see screenshots)                     |
| **Multilingual Support**| Agent auto-detects and responds in German or English                       |

Visual workflow and logic are shown in the diagram below:

![System Flow](https://github.com/rtheman/Claire_personal_assistant/blob/dc40e4360d303a0abb20b12034ec8c571e54d091/AI%20Agent%20-%20Claire%20-%20Appointment%20Scheduling%20-%20Functional%20flow%20chart.png)

---

## 🤖 System Prompt
This AI agent prompt defines how **Claire**, the voice-enabled appointment assistant, behaves, speaks, and handles scheduling tasks. It acts as the foundation for repeatable, explainable performance across all caller interactions.

Details of system prompt can be found [here](./Main%20Agent%20System%20Prompt).


## 🧩 Key Features

### 🗓️ Intelligent Scheduling
Cl(ai)re can:
- Check availability (`get_Available_Slots`)
- Book new appointments (`Book_Appointment`)
- Reschedule existing appointments (`reschedule_appointment`)
- Cancel appointments (`cancel_appointment`)
- Lookup current bookings (`find_appointment`)

### ☀️ Weather Forecasting
Cl(ai)re fetches real-time weather forecasts based on appointment location and time (`get_weather`), offering:
- Current weather summaries
- 3–14 day forecasts
- Friendly alerts for extreme weather

### 👥 Natural Voice & Bilingual UX
- Bilingual support (English 🇺🇸 & German 🇩🇪)
- Voice responses use conversational filler phrases like:
  - “Let me check that real quick…”
  - “Hmm, looks like that time’s taken—shall we try another?”
  - “Awesome, we’re all set!”

---

## 📦 Custom Tools Overview

Cl(ai)re integrates with these webhooks (API endpoints):
- [`get_Available_Slots`](./Sub%20Agents/get_available_slots) – See open times
- [`Book_Appointment`](./Sub%20Agents/Book_Appointment) – Schedule a meeting
- [`reschedule_appointment`](./Sub%20Agents/reschedule_appointment) – Adjust a booking
- [`cancel_appointment`](./Sub%20Agents/cancel_appointment) – Delete a booking
- [`find_appointment`](./Sub%20Agents/find_appointment) – Lookup existing booking
- [`get_weather`](./Sub%20Agents/get_weather) – Forecast weather at appointment location

See tool configuration screenshot here:  
![Custom Tools](./AI%20Agent%20-%20Claire%20-%20Appointment%20Scheduling%20-%20Custom%20Tools.png)

---

## 🌍 Multilingual Support

Cl(ai)re dynamically detects and responds in German if the caller speaks it—enabling a more inclusive and accessible user experience.

![Bilingual Setup](./AI%20Agent%20-%20Claire%20-%20Appointment%20Scheduling%20-%20bilingual.png)


---

## 🙌 Acknowledgements
Built with ❤️ using:
- [ElevenLabs AI Agents](https://elevenlabs.io/)
- [Cal.com](https://cal.com/)
- Years of experience in ML, NLP, and data product design


---
---


# 🔭 Next Steps & Future Project Plan

To build on Claire’s current capabilities and infrastructure, the following future enhancements are planned:

## 1. 🧠 Migrate to Model Context Protocol (MCP)

**Current State:** Claire interacts with external services like Cal.com and WeatherAPI.com using custom HTTP tools.

**Planned Upgrade:** Replace these isolated API services with a **unified MCP layer** that enables structured, secure, and efficient access to services such as:
- Gmail (for reading/responding to emails)
- Google Drive (for accessing/storing files)
- Weather forecast via Google's ecosystem

**Benefits:**
- ✅ Cleaner system flow by calling a **single callable MCP endpoint** instead of multiple APIs.
- 🚀 Easier to scale and manage access control.
- 🔍 More observable & secure interactions with OAuth-based Google Services.
- 🧪 Personal learning: Gain firsthand experience with the emerging best practices around MCP integrations.

---

## 2. 🔄 Refactor Voice Agent Backend from ElevenLabs to N8N

**Current State:** ElevenLabs manages voice synthesis and agent operations.

**Planned Upgrade:** Refactor backend flows to use **[N8N](https://n8n.io)** for task orchestration and webhook-driven flows.

**Benefits:**
- 🧩 Unified platform for API orchestration, scheduling, and webhook flows.
- 💡 Simplifies debugging and flow visualization for non-technical stakeholders.
- 💬 Greater control over execution logic and retry mechanisms.
- 🔄 Enables automation pipelines beyond voice—e.g., notification logic, multi-channel comms.


---
---


# 💡 Lessons Learned
*as of 2025-06-25*

![image](https://github.com/user-attachments/assets/bed217b2-4ada-4ffe-8dd7-f9ecac502d36)


## 1. 🔁 Repeatability vs Flexibility

AI Agents thrive when grounded in structure. But building Claire raised this question:  
> “How do we strike the right balance between **framework-driven system prompts** and **freeform design** for creativity?”

**Takeaway:**  
Crafting reusable agents often means defining clear components (Role, Voice & Persona, Tasks, Tools, etc.), but leaving room for adaptation through modular sub-prompts or dynamic memory. Best practices suggest:
- Define a **core template** but allow for prompt chaining.
- Use variable blocks (like `{{user_context}}`) to enable flexible persona shaping
- Avoid over-engineering; start with functional structure, then let the agent iterate

---

## 2. 🔍 Explainability & Interpretability

Much like ML models, AI agents can exhibit **opaque behavior**. Hallucinations are just one layer.

**Takeaway:**  
- Treat prompts like **input parameters**—small changes matter
- Log agent thoughts, message history, tool usage
- Borrow from **LIME/SHAP-style concepts** in ML to probe prompt sensitivity
- Implement **controlled testing** (e.g., prompt A/B tests, agent trace logs)

---

## 3. ☎️ Voice Agent Acceptance (Inbound vs Outbound)

**Context matters** when deploying voice agents:

- ❌ **Outbound Call**: Users expect empathy, improvisation, and exploration. AI here may feel pushy or inadequate.
- ✅ **Inbound Call**: For transactional use-cases like booking appointments or checking status, AI is welcome—especially when:
  - It’s faster than a human
  - Offers 24/7 availability
  - Doesn’t judge or get tired
  - Benefits vendors *and* consumers

**Takeaway:**  
Design voice agents to **complement**, not replace. Always **disclose AI nature** early, and offer escalation to human fallback when context demands depth, nuance, or emotional intelligence.
