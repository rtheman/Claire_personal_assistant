# 🌦️ Custom Tool Summary – `get_weather` Integration

The `get_weather` tool is a custom webhook used by Claire to provide real-time weather information and short-term forecasts based on a caller’s appointment location. It leverages the [WeatherAPI.com](https://www.weatherapi.com/) service and is seamlessly integrated into Claire’s conversational flow.



## 🔧 Tool Configuration

| Setting         | Value                                                           |
|----------------|-----------------------------------------------------------------|
| **Method**      | `GET`                                                           |
| **Endpoint**    | `https://api.weatherapi.com/v1/forecast.json`                  |
| **Timeout**     | 20 seconds (default)                                            |
| **Authentication** | API Key (constant variable, securely stored)                  |



## 🧠 Purpose & Use Case

This tool enhances the assistant’s helpfulness by enabling it to:
- **Proactively offer weather forecasts** after an appointment is scheduled or rescheduled
- **Respond to direct weather queries**, e.g., “What’s the weather like in Berlin tomorrow?”
- Tailor responses to the caller’s **specific location** and **date of the appointment**



## 🗂️ Parameters Passed to the API

| Parameter | Type    | Source      | Description                                                                 |
|-----------|---------|-------------|-----------------------------------------------------------------------------|
| `q`       | String  | LLM Prompt  | Caller's location (e.g., city name, US zip, UK postcode, etc.)             |
| `days`    | Integer | LLM Prompt  | Number of days of forecast (range: 1 to 14; default: 3 if not specified)    |
| `key`     | String  | Constant    | WeatherAPI key (stored securely in tool config)                             |



## 🧾 Prompt Engineering Details

- **`q`** is extracted directly from caller input like “I’ll be in Hamburg” or inferred from the appointment context.
- **`days`** is either user-specified (e.g., “next 5 days”) or defaulted to 3 days.
- **Clear system instruction formatting** helps ensure the LLM collects these values reliably and predictably.



## 📢 Sample Response Flow (in Voice)

> “Sure! Let me check the weather for Hamburg…  
Currently, it’s 17°C with light rain.  
Looking ahead: Tomorrow will be 19°C and sunny. The day after, expect showers around 21°C.”  
<br>“Hope that helps! Would you like me to text or email this forecast to you as well?”



## ✅ Why It Matters

- Adds **real-world utility** to the scheduling agent
- Demonstrates **multi-modal reasoning** (time + location + external data)
- Makes the assistant feel **proactive and thoughtful**, improving user trust and satisfaction
