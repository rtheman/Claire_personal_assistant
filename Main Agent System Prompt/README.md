
# 🧠 System Prompt Summary – Claire’s Behavioral Blueprint

This AI agent prompt defines how **Claire**, the voice-enabled appointment assistant, behaves, speaks, and handles scheduling tasks. It acts as the foundation for repeatable, explainable performance across all caller interactions.

## 🎯 Core Role
Claire is designed as a **scheduling personal assistant**, responsible for understanding the caller's intent and helping with the following key tasks:
- Checking availability
- Booking appointments
- Rescheduling existing ones
- Canceling confirmed appointments
- Providing weather forecasts tied to appointment locations

## 🗣️ Voice, Persona & User Experience
The prompt goes beyond utility—it crafts a **charming and professional persona**:
- Friendly, organized, and efficient
- Patient with confused or elderly callers
- Witty and lighthearted, using casual phrases like “Let me pull that up real quick…” or “Awesome, we’re all set!”
- Prioritizes human-likeness using filler words, confirmations, and natural contractions

> **Why it matters:** These voice design elements create an intuitive and pleasant conversational experience—critical for trust and usability in voice-based AI.

## 🧾 Structured Response Logic
The prompt is intentionally **task-oriented and modular**, with logic blocks that control how the agent performs each task:

### ✅ **Availability Check**
- Uses the `get_Available_Slots` API
- If no date is given, it searches forward from tomorrow
- Gracefully handles unavailable slots by offering alternatives

### 📅 **Appointment Booking**
- Gathers required fields: name, email, time, topic, and duration
- Repeats and validates email format
- If booking fails, it tries to troubleshoot based on email or time

### 🔁 **Rescheduling**
 Validates identity (name + email)
- Locates and confirms the existing appointment
- Checks availability for the new date
- Offers fallback suggestions when desired slots are busy

### ❌ **Cancellation**
- Repeats verification steps
- Requests (optional) reason
- Confirms details before canceling

### 🌦️ **Weather Forecast**
- Retrieves multi-day forecast using `get_weather`
- Handles both standalone and appointment-related queries
- Communicates weather clearly, rounding temps and highlighting extreme conditions

## 🕒 Timezone Intelligence
Claire handles date and time using:
- UTC-based time processing
- Europe/Berlin (UTC+2) as default caller timezone
- Dynamic conversion for appointments and forecasts

---

## 🧩 Why This Prompt Design Works

This system prompt is carefully constructed for:
- **Repeatability** – Tasks follow deterministic steps
- **Explainability** – Agent decisions (e.g., why an appointment can’t be booked) are transparent
- **Adaptability** – Voice tone + fallback logic make it resilient to edge cases
- **Minimal Engineering Overhead** – It enables low-code design while offering enterprise-grade functionality
