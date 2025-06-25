# 🛠️ Custom Tool Summary: `find_appointment` Integration

## 🔧 Tool Configuration

| Setting         | Value                                                               |
|----------------|---------------------------------------------------------------------|
| **Method:**     | `GET`                                                               |
| **Endpoint:**   | `https://api.cal.com/v2/bookings`                                   |


## 🧠 Purpose & Use Case

The `find_appointment` tool is designed to **retrieve existing appointments** by querying Cal.com via the caller's email and optionally their name. It helps agents determine whether a specific appointment exists before taking further actions like rescheduling or canceling.

### 📌 Common Use Cases:
- Confirm upcoming appointments
- Identify specific bookings for updates or cancellations
- Enable appointment lookup before executing time-sensitive actions



## 🔧 Configuration Summary

- **Tool ID:** `tool_01kjfzjan3eyibt9s19sp3bmx9`
- **URL:** `https://api.cal.com/v2/bookings`
- **Method:** `GET`
- **Headers:**
  - `cal-api-version: 2024-08-13`
  - `Authorization: Bearer <secret_token>`



## 🧾 Prompt Engineering Details

### Query Parameters:
| Identifier      | Required | Source       | Description                            |
|----------------|----------|--------------|----------------------------------------|
| `attendeeEmail`| ✅        | LLM Prompt   | Caller's email address                 |
| `status`       | ✅        | LLM Prompt   | Appointment status (e.g., `upcoming`)  |
| `attendeeName` | ❌        | LLM Prompt   | Optional – Caller's name               |



## 📢 Sample Response Flow (in Voice)

> “Alright! I’ve found your appointment for Monday at 3 PM under the name Alex Johnson. Let me know if you’d like to reschedule or cancel it.”



## ✅ Why It Matters

Before modifying or canceling an appointment, it's crucial to confirm it exists. This tool ensures that agents have the necessary data to:
- Prevent accidental edits to the wrong booking
- Provide personalized, intelligent responses to users
- Automate workflow decisions based on appointment presence



## 🧩 Integration Path

This tool typically acts as a precursor to:
- `cancel_appointment`
- `reschedule_appointment`

When paired with other tools in the scheduling suite, it enables a seamless and intelligent booking management experience.