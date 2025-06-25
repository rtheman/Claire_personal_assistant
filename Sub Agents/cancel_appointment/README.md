# 📅 Custom Tool Summary: `cancel_appointment` Integration

This tool is integrated with [Cal.com](https://cal.com) to allow the AI Assistant (Claire) to cancel a previously scheduled appointment from the user's Google Calendar.



## 🧠 Purpose & Use Case

Used to cancel an existing appointment by referencing the unique booking identifier (`bookingUid`) returned by the `find_appointment` tool. Caller may optionally provide a cancellation reason.



## 🔧 API Configuration

**Tool ID:** `tool_01xjfzjan7f4wshnmm9v13t5gm`  
**Method:** `POST`  
**Endpoint:** `https://api.cal.com/v2/bookings/{bookingUid}/cancel`  
**Dependent Agent:** Claire - Appointment



## 🔐 Headers

| Name             | Type   | Value             |
|------------------|--------|------------------|
| cal-api-version  | Value  | 2024-08-13        |
| Authorization    | Secret | Bearer Token      |
| Content-Type     | Value  | application/json  |



## 📥 Path Parameters

| Identifier | Type   | Value Type  | Description |
|------------|--------|-------------|-------------|
| bookingUid | String | LLM Prompt  | The `uid` of the target appointment from the 'data' array returned by the `find_appointment` tool. |



## 🧾 Body Parameters

Description: Information of the target appointment to be canceled. This includes the reason for cancellation by caller if provided.

### Properties

| Identifier        | Type   | Required | Value Type | Description                                               |
|-------------------|--------|----------|------------|-----------------------------------------------------------|
| cancellationReason| String | ✅        | LLM Prompt | Cancelation reasons provided by caller for this cancellation. |



## 🧾 Prompt Engineering Details

Make sure the LLM is instructed to:

- Retrieve the `bookingUid` from the response object of the `find_appointment` call.
- Request a brief reason for cancellation from the user (optional but encouraged).
- Convert user-friendly intent into proper string input for `cancellationReason`.



## 📢 Sample Response Flow (in Voice)

> **User:** "Cancel my appointment at 2pm with Rich. I can't make it."  
> **Claire (AI):** "No problem. I’ve canceled your 2pm appointment. I’ve also noted that you're unavailable — reason: 'I can't make it.' Let me know if you’d like to reschedule."



## ✅ Why It Matters

- Frees up the user’s calendar availability for rebooking.
- Captures feedback or reason for cancellation.
- Maintains calendar hygiene and user satisfaction via voice-friendly interactions.



## 🧩 Dependencies

This tool assumes the appointment has first been found via the `find_appointment` tool, which provides the required `bookingUid`.
