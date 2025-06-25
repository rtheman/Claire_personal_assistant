# 📆 Custom Tool Summary – `Book_Appointment` Integration

The `Book_Appointment` tool enables Claire, the AI scheduling assistant, to finalize appointments by creating calendar entries using the [Cal.com](https://cal.com) platform. Once the user’s name, email, preferred time, and other key details are collected, this POST request is triggered to securely register the meeting in your connected calendar (e.g., Google Calendar).



## 🔧 Tool Configuration

| Setting         | Value                                         |
|----------------|-----------------------------------------------|
| **Method**      | `POST`                                       |
| **Endpoint**    | `https://api.cal.com/v2/bookings`            |
| **Timeout**     | 20 seconds (default)                         |
| **Headers**     | `cal-api-version: 2024-08-13`, `Content-Type: application/json`, `Authorization: Bearer <secret>` |



## 🧠 Purpose & Use Case

This tool is triggered when:
- An available time slot has been identified
- The user confirms the booking
- All necessary fields have been collected via conversation

This enables Claire to:
- Securely schedule the meeting
- Sync with your real-time Google Calendar
- Offer confirmation responses with appointment details



## 📥 Body Parameters

| Parameter      | Type    | Description                                                             |
|----------------|---------|-------------------------------------------------------------------------|
| `start`        | String  | Start time in ISO 8601 UTC format (e.g., `'2025-05-25T09:00Z'`)         |
| `eventTypeId`  | Number  | Cal event type ID (e.g., `2537695`) to define the meeting duration      |
| `attendee`     | Object  | Includes attendee's name, email, timezone, and language                 |
| `phoneNumber`  | String  | Optional – caller’s phone number; default to `+1.202.867.5309` if missing |

### 📦 `attendee` Object Properties

| Field        | Type    | Source        | Description                                                       |
|--------------|---------|---------------|-------------------------------------------------------------------|
| `name`       | String  | LLM Prompt     | Caller's full name                                                |
| `email`      | String  | LLM Prompt     | Valid email address of the caller                                 |
| `timeZone`   | String  | LLM Prompt     | Caller's timezone (e.g., `Europe/Berlin`)                         |
| `language`   | String  | Constant       | Default language set to `'en'`                                    |



## 🧾 Prompt Engineering Details

- The LLM is responsible for gathering the full payload through natural dialogue.
- Timestamps are converted to UTC in ISO 8601 format before submission.
- Email address is validated and confirmed verbally before processing.
- Timezone context is extracted to avoid mismatches between caller and calendar.



## 📢 Sample Response Flow (in Voice)

> “Okay, I’ve locked in your appointment for Tuesday at 2 PM Berlin time.  
I’ve sent a confirmation to rich@example.com.  
Would you like me to check the weather for that day as well?”



## ✅ Why It Matters

- **Closes the scheduling loop** by finalizing appointments
- **Personalizes interactions** by validating and echoing details like name and email
- **Enhances reliability** by ensuring accurate timezone and time handling
- **Works seamlessly with other tools** (availability + weather) to deliver full-cycle support