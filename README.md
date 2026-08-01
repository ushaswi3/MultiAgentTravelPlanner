# Multi Agent Travel Planner

UI Link : https://multi-agent-travel-planner-one.vercel.app/


# Multi Agent Travel Planner
# 🧭 VoyageAI: Multi-Agent AI Travel Planner

VoyageAI is a premium, state-of-the-art travel planning platform powered by a **collaborative multi-agent AI swarm network**. Designed to eliminate travel planning fatigue, it orchestrates multiple specialized AI agents to generate customized, budget-aware, weather-optimized, and curated travel itineraries.

---

## 🏗️ Swarm Architecture & Agent Flow

The platform is designed around a **Coordinator-Agent Architecture** where specialized agents collaborate synchronously to produce a complete travel plan:

```
       User Request
            │
            ▼
      [ FastAPI API ]
            │
            ▼
    [ Coordinator Agent ] (The Swarm Brain)
            │
            ├─► Destination Agent ── (Fetches geo-context & baseline data)
            ├─► Transport Agent ──── (Determines routing & cost estimation)
            ├─► Hotel Agent ──────── (Matches stays based on budget & preferences)
            ├─► Weather Agent ────── (Retrieves real-time/forecasted weather)
            ├─► Itinerary Agent ──── (Builds daily, tailored schedule)
            ├─► Budget Agent ─────── (Consolidates transport, lodging, & daily spends)
            └─► Recommendation Agent (LLM-based context synthesis & tips)
            │
            ▼
     Finalized Travel Plan 
```

---

## ✨ Features

- **Collaborative Multi-Agent Swarm**: Each segment of the travel plan is handled by a specialized micro-agent designed for that specific domain.
- **Dynamic & Interactive Frontend**: Fully responsive, glassmorphism-inspired UI built with HTML5, CSS3, and JavaScript, featuring beautiful gradients, hover states, micro-animations, and media integration.
- **Interactive Trip Customization**: Specify source, destination, dates, duration, budget, preferences, and custom requirements.
- **Secure Authentication**: Built-in user management with robust signup/login systems using JSON Web Tokens (JWT) and Bcrypt encryption.
- **Real-time API Integration & Mock Fail-safes**: Integrates with OpenWeather, Geoapify, Aviationstack, and Groq LLMs (Llama-3.3). Safely falls back to mock data if API keys are missing.
- **Comprehensive API Docs**: Automatically generated FastAPI OpenAPI UI (`/docs`).

---

## 📂 Project Structure

```
├── backend/
│   ├── agents/            # Swarm AI agent definitions
│   │   ├── coordinator_agent.py
│   │   ├── budget_agent.py
│   │   ├── destination_agent.py
│   │   ├── hotel_agent.py
│   │   ├── itinerary_agent.py
│   │   ├── recommendation_agent.py
│   │   ├── translator_agent.py
│   │   ├── transport_agent.py
│   │   └── weather_agent.py
│   ├── config/            # App configurations and settings
│   ├── database/          # SQLite database connection and models
│   ├── routes/            # FastAPI router endpoints
│   ├── main.py            # Application entrypoint
│   ├── requirements.txt   # Python dependencies
│   └── travel_planner.db  # Local SQLite database
│
├── frontend/              # Rich interactive web app files
│   ├── index.html         # Landing page & user interface
│   ├── style.css          # Modern styling (glassmorphism, gradients)
│   ├── app.js             # Client logic & state management
│   ├── dashboard.html     # User dashboard
│   ├── trips.html         # Saved trips viewer
│   ├── about.html         # About the app
│   └── oauth-mock.html    # Mock OAuth authorization page
│
└── README.md              # Project documentation
```

---

## 🚀 Setup & Installation

### 1. Prerequisites
- **Python 3.10+**
- A modern web browser
- (Optional) API keys for external services (OpenWeather, Geoapify, Aviationstack, Groq)

### 2. Backend Setup
1. Open a terminal in the `backend/` directory.
2. Create and activate a Python virtual environment:
   ```bash
   # Windows (PowerShell)
   python -m venv venv
   .\venv\Scripts\Activate.ps1

   # macOS/Linux
   python3 -m venv venv
   source venv/bin/activate
   ```
3. Install the required dependencies:
   ```bash
   pip install -r requirements.txt
   ```
4. Create a `.env` file in the `backend/` directory. You can use the following values as a guide:
   ```env
   # Core App Settings
   SECRET_KEY=your_secret_key_here
   ALGORITHM=HS256
   ACCESS_TOKEN_EXPIRE_MINUTES=60
   DATABASE_URL=sqlite:///./travel_planner.db

   # Optional External API Keys (Leave blank to use realistic mock data out-of-the-box!)
   OPENWEATHER_API_KEY=your_openweather_key
   GEOAPIFY_API_KEY=your_geoapify_key
   AVIATIONSTACK_API_KEY=your_aviationstack_key
   GROQ_API_KEY=your_groq_key
   GROQ_MODEL=llama-3.3-70b-versatile
   ```
5. Run the FastAPI development server:
   ```bash
   uvicorn main:app --reload
   ```
   *The API will start running at `http://127.0.0.1:8000`.*
   *View the interactive API docs at `http://127.0.0.1:8000/docs`.*

### 3. Frontend Setup
1. Navigate to the `frontend/` directory.
2. Open `index.html` in your web browser. You can use:
   - A VS Code extension like **Live Server**.
   - A local serving tool like `npx serve` or `python -m http.server`.
   - By double-clicking `index.html` directly (though some API functions perform best under HTTP/HTTPS local servers).

---

## 🛠️ Built With

- **Backend**: [FastAPI](https://fastapi.tiangolo.com/), [SQLAlchemy](https://www.sqlalchemy.org/), [Pydantic](https://docs.pydantic.dev/)
- **Frontend**: Vanilla HTML5, CSS3 (Modern custom design system), JavaScript (ES6+)
- **LLM/Swarm Orchestration**: Custom Python agents, [Groq](https://groq.com/) API
- **Database**: SQLite

---

