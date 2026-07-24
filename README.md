# weather-api-automation
Parent and child workfloww
🌦️ Parent-Child Workflow using n8n & OpenWeatherMap API
📌 Project Overview

This project demonstrates how to build a Parent-Child Workflow in n8n using the OpenWeatherMap API. The parent workflow acts as an AI agent that receives a user's weather query and delegates the weather retrieval task to a child workflow. The child workflow fetches real-time weather data, processes it, and returns a human-readable response back to the parent workflow.

This architecture improves modularity, reusability, and workflow organization by separating weather-related logic into a dedicated child workflow.

🛠️ Technologies Used
n8n
OpenWeatherMap API
AI Agent Node
Groq Chat Model (or any configured LLM)
Parent Workflow
Child Workflow
📂 Workflow Architecture
User
   │
   ▼
Parent Workflow
   │
   ▼
AI Agent
   │
   ▼
Execute Child Workflow
   │
   ▼
Child Workflow
   │
   ▼
OpenWeatherMap API
   │
   ▼
Generate Weather Response
   │
   ▼
Return Result
   │
   ▼
Parent Workflow
   │
   ▼
User
🔹 Parent Workflow

The Parent Workflow is responsible for interacting with the user.

Steps
Waits for a chat message.
AI Agent analyzes the user's request.
Detects that weather information is required.
Calls the Child Workflow as a Tool.
Receives the weather response.
Sends the final answer back to the user.
Parent Workflow Nodes
When Chat Message Received
AI Agent
Chat Model (Groq)
Memory
Execute Child Workflow Tool
🔹 Child Workflow

The Child Workflow is dedicated to weather information retrieval.

Steps
Receives the city name from the Parent Workflow.
Extracts and formats the input.
Calls the OpenWeatherMap API.
Retrieves real-time weather data.
AI Model converts raw weather data into simple English.
Returns the response to the Parent Workflow.
Child Workflow Nodes
When Executed by Another Workflow
Edit Fields
OpenWeatherMap
Message a Model
Edit Fields (Response)
🌤 OpenWeatherMap API

The project uses the Current Weather endpoint provided by OpenWeatherMap.

The API returns:

Temperature
Feels Like Temperature
Humidity
Weather Condition
Cloud Coverage
Wind Information

These values are converted into a user-friendly response using an AI model.

🤖 AI Processing

Instead of returning raw JSON data, the workflow uses an AI model to generate a natural language summary.

Example Output:

The weather in Faisalabad is mostly cloudy with overcast skies. The temperature is around 33.6°C but feels like 37.7°C. The humidity is 51%.

🔄 Workflow Execution
Parent Workflow
User asks:
"What is the weather in Lahore?"

↓

AI Agent

↓

Execute Child Workflow
Child Workflow
Receive City

↓

OpenWeatherMap API

↓

AI Model

↓

Return Response
Final Output
The current weather of Lahore is mostly sunny with a high of 28°C and a low of 18°C.
✅ Features
Parent-Child Workflow Architecture
Modular Design
Real-time Weather Information
AI-generated Human-readable Responses
OpenWeatherMap API Integration
Reusable Child Workflow
Easy to Extend with Additional Tools
📸 Workflow Screenshots
Parent Workflow

(Insert Parent Workflow Screenshot Here)

Child Workflow

(Insert Child Workflow Screenshot Here)

🚀 Future Improvements
5-Day Weather Forecast
Weather Alerts
Multiple Weather APIs
Voice-based Weather Assistant
WhatsApp Integration
Telegram Bot Integration
Multi-language Responses
