# 🤖 Claire – AI Appointment Scheduling Assistant

Claire is a friendly, voice-enabled AI assistant built to handle appointment scheduling, rescheduling, cancellations, and weather inquiries—entirely over voice. Designed with minimal code using modern tools like [ElevenLabs AI Agents](https://elevenlabs.io/), Cal.com APIs, and webhook integrations, Claire showcases how powerful, human-like assistants can be created without writing complex backend logic.



## 🧠 About This Project

**Claire** acts as a conversational agent for booking and managing appointments through natural, voice-based interaction. It speaks **English and German** natively and responds with clarity, charm, and a bit of wit—perfect for both professional and casual contexts.

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

![System Flow](./AI%20Agent%20-%20Claire%20-%20Appointment%20Scheduling.png)

---

## 🧩 Key Features

### 🗓️ Intelligent Scheduling
Claire can:
- Check availability (`get_Available_Slots`)
- Book new appointments (`Book_Appointment`)
- Reschedule existing appointments (`reschedule_appointment`)
- Cancel appointments (`cancel_appointment`)
- Lookup current bookings (`find_appointment`)

### ☀️ Weather Forecasting
Claire fetches real-time weather forecasts based on appointment location and time (`get_weather`), offering:
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

Claire integrates with these webhooks (API endpoints):
- `get_Available_Slots` – See open times
- `Book_Appointment` – Schedule a meeting
- `reschedule_appointment` – Adjust a booking
- `cancel_appointment` – Delete a booking
- `find_appointment` – Lookup existing booking
- `get_weather` – Forecast weather at appointment location

See tool configuration screenshot here:  
![Custom Tools](./AI%20Agent%20-%20Claire%20-%20Appointment%20Scheduling%20-%20Custom%20Tools.png)

---

## 🌍 Multilingual Support

Claire dynamically detects and responds in German if the caller speaks it—enabling a more inclusive and accessible user experience.

![Bilingual Setup](./AI%20Agent%20-%20Claire%20-%20Appointment%20Scheduling%20-%20bilingual.png)

---

## ✅ Next Steps & Ideas
- Add calendar integration to check personal availability from Outlook/Google
- Add SMS/email confirmation post-booking
- Support rich context memory for returning users

---

## 🙌 Acknowledgements
Built with ❤️ using:
- [ElevenLabs AI Agents](https://elevenlabs.io/)
- [Cal.com](https://cal.com/)
- Years of experience in ML, NLP, and data product design
