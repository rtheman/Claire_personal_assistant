# 🔁 Custom Tool Summary – `reschedule_appointment` Integration

The `reschedule_appointment` tool empowers Claire, the AI scheduling assistant, to update an existing booking on your calendar using [Cal.com](https://cal.com). This function is triggered once a caller confirms their current appointment and specifies a new desired time.



## 🔧 Tool Configuration

| Setting         | Value                                                               |
|----------------|---------------------------------------------------------------------|
| **Method**      | `POST`                                                              |
| **Endpoint**    | `https://api.cal.com/v2/bookings/{bookingUid}/reschedule`          |
| **Timeout**     | 20 seconds (default)                                                |
| **Headers**     | `cal-api-version: 2024-08-13`, `Authorization: Bearer <secret>`     |



## 🧠 Purpose & Use Case

This tool is invoked when:
- A caller wants to **change an already scheduled appointment**
- Claire has successfully used `find_appointment` to retrieve the current booking
- A new preferred time has been collected and validated

It enables seamless calendar updates without requiring caller to re-enter all information.



## 🔂 Path Parameters

| Parameter      | Type    | Source     | Description                                                       |
|----------------|---------|------------|-------------------------------------------------------------------|
| `bookingUid`   | String  | LLM Prompt | Unique identifier of the appointment retrieved via `find_appointment` |



## 📥 Body Parameters

| Parameter  | Type    | Source     | Description                                   |
|------------|---------|------------|-----------------------------------------------|
| `start`    | String  | LLM Prompt | New start time in ISO 8601 format (UTC)       |



## 🧾 Prompt Engineering Details

- Claire confirms which appointment to reschedule by presenting options if more than one is found.
- The `bookingUid` is extracted from the `data` returned by the `find_appointment` tool.
- Once a new time is agreed upon, it is parsed and formatted to the required ISO 8601 structure.
- Optional logic may be added to also collect a cancellation reason, though not required.



## 📢 Sample Response Flow (in Voice)

> “Okay, I’ve rescheduled your appointment to Thursday at 1 PM.  
You should receive a confirmation email shortly.  
Would you like help with anything else?”



## ✅ Why It Matters

- Enables **dynamic and user-friendly appointment management**
- Minimizes friction by eliminating the need for a new booking flow
- Ensures **accurate handling of timezones and calendar sync**
- Complements Claire’s broader scheduling toolkit (find, book, cancel)