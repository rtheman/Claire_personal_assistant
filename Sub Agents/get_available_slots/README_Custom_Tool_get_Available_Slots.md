# 🗓️ Custom Tool Summary – `get_Available_Slots` Integration

The `get_Available_Slots` tool is a webhook that allows Claire, the AI scheduling assistant, to query your real-time availability using the [Cal.com](https://cal.com) API. This enables dynamic, context-aware scheduling directly from your connected calendar (e.g., Google Calendar).



## 🔧 Tool Configuration

| Setting         | Value                                             |
|----------------|---------------------------------------------------|
| **Method**      | `GET`                                             |
| **Endpoint**    | `https://api.cal.com/v2/slots`                   |
| **Timeout**     | 20 seconds (default)                              |
| **Authentication** | Bearer token (secret)                            |
| **Header**      | `cal-api-version: 2024-09-04`                     |



## 🧠 Purpose & Use Case

This tool allows the agent to:
- **Check your availability** over a specified date and time range
- **Validate whether a time slot is open** before attempting to book or reschedule an appointment
- **Offer alternative slots** when a caller’s preferred time is unavailable

This ensures that all appointment-related actions are grounded in your live calendar, making scheduling highly reliable.



## 🗂️ Parameters Passed to the API

| Parameter       | Type   | Source      | Description                                                                                     |
|----------------|--------|-------------|-------------------------------------------------------------------------------------------------|
| `start`         | String | LLM Prompt  | ISO 8601 formatted start time in Europe/Berlin timezone (e.g., `2025-05-29T12:30:00.000+02:00`) |
| `end`           | String | LLM Prompt  | ISO 8601 formatted end time in Europe/Berlin timezone                                           |
| `timeZone`      | String | Constant    | Set to `Europe/Berlin`                                                                          |
| `eventTypeId`   | String | Constant    | Unique Cal.com event type ID for this booking context                                           |
| `format`        | String | Constant    | Set to `range` to specify the time slot query mode                                              |



## 🧾 Prompt Engineering Details

- **`start` and `end`** times are interpreted from natural language input (e.g., “next Tuesday at 3pm”) and converted to the proper ISO 8601 format.
- The agent ensures that all time inputs are treated in **Europe/Berlin (UTC+2)** timezone before making API calls.
- **Fallback logic** in Claire checks if the `data` field in the API response is empty—indicating no available slots—and gracefully handles this by offering alternatives.



## 📢 Sample Response Flow (in Voice)

> “Let me check Rich’s calendar for that time…  
Hmm, looks like he’s busy then. But he’s free at 2:30 PM or 4:00 PM. Would either of those work?”



## ✅ Why It Matters

- Ensures **accuracy and synchronization** with your actual calendar
- Adds a layer of **intelligence** to availability checks
- Prevents double-bookings and avoids hardcoding time slots
- Keeps the conversation natural by responding with smart time suggestions