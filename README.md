

<h1 align="center">GreenMines</h1>

<p align="center">
  <strong>Carbon Footprint Quantification & Neutrality Pathways for Indian Coal Mines</strong>
</p>

<p align="center">
  <a href="#-features">Features</a> •
  <a href="#%EF%B8%8F-architecture">Architecture</a> •
  <a href="#-tech-stack">Tech Stack</a> •
  <a href="#-getting-started">Getting Started</a> •
  <a href="#-api-reference">API Reference</a> •
  <a href="#-project-structure">Project Structure</a> •
  <a href="#-contributing">Contributing</a> •
  <a href="#-license">License</a>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/React-18.0-61DAFB?style=for-the-badge&logo=react&logoColor=white" alt="React"/>
  <img src="https://img.shields.io/badge/Node.js-Express-339933?style=for-the-badge&logo=node.js&logoColor=white" alt="Node.js"/>
  <img src="https://img.shields.io/badge/Python-Flask-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python"/>
  <img src="https://img.shields.io/badge/MongoDB-Mongoose-47A248?style=for-the-badge&logo=mongodb&logoColor=white" alt="MongoDB"/>
  <img src="https://img.shields.io/badge/TailwindCSS-3.0-06B6D4?style=for-the-badge&logo=tailwindcss&logoColor=white" alt="TailwindCSS"/>
  <img src="https://img.shields.io/badge/Google-Gemini%20AI-4285F4?style=for-the-badge&logo=google&logoColor=white" alt="Gemini AI"/>
</p>

---

## 📋 Table of Contents

- [About the Project](#-about-the-project)
- [Features](#-features)
- [Architecture](#%EF%B8%8F-architecture)
- [Tech Stack](#-tech-stack)
- [Getting Started](#-getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
  - [Environment Variables](#environment-variables)
  - [Running the Application](#running-the-application)
- [API Reference](#-api-reference)
- [ML Models](#-ml-models)
- [Project Structure](#-project-structure)
- [Contributing](#-contributing)
- [License](#-license)
- [Acknowledgements](#-acknowledgements)

---

## 🌍 About the Project

**GreenMines** is a comprehensive web platform engineered to help the Indian coal mining sector transition toward carbon neutrality. The platform combines real-time emission tracking, predictive machine learning models, and generative AI-powered analytics to deliver a holistic carbon management solution.

Coal mining in India remains a critical contributor to greenhouse gas emissions. GreenMines addresses this by providing mine operators with:

- **Precise emission quantification** across six major sources (electricity, fuel, shipping, explosives, coal burning, methane)
- **AI-driven environmental impact analysis** using Google Gemini and Cohere AI
- **Predictive ML models** that forecast future emissions based on 7-day operational data
- **Six actionable carbon neutrality pathways** including carbon sinks, renewable energy integration, CCS, MCS, AFOLU analysis, and EV fleet optimization
- **Real-time dashboards and reporting** with automated PDF generation

---

## ✨ Features

### 🔢 Carbon Footprint Calculators

| Calculator | Data Source | Description |
|-----------|------------|-------------|
| **Electricity** | CarbonKit API | State-wise electricity emission calculation for all Indian states |
| **Fuel Combustion** | CarbonKit DEFRA | Multi-fuel emission tracking (petrol, diesel, LPG, etc.) |
| **Shipping & Transport** | Carbon Interface API | Weight/distance-based transport emissions |
| **Explosives** | Built-in factors | 9 explosive types with gas-specific breakdowns (CO, CO₂, NOx, H₂S, NH₃) |
| **Coal Burning** | Built-in factors | 4 coal types (Lignite, Sub-bituminous, Bituminous, Anthracite) |
| **Methane** | Built-in model | Surface and underground mining with atmospheric condition adjustments |

### 📊 Dashboard & Analytics

- **Real-time tracking dashboard** with daily, weekly, monthly, and yearly views
- **Interactive charts** — line, bar, donut, and comparative visualizations
- **Date-range data fetching** with filtering and entry deletion
- **Per-ton emission analysis** for benchmarking

### 🤖 AI-Powered Features

| Feature | AI Provider | Capability |
|---------|------------|------------|
| **Emission Impact Analyzer** | Cohere AI (command-xlarge) | Environmental forensics report: biodiversity hazard, ozone depletion, soil contamination, climate refugees, health risks |
| **AI Chat Assistant** | Google Gemini Pro | Context-aware chatbot for coal mining sustainability guidance |
| **Environmental Reports** | Google Gemini Pro | Automated daily/weekly/monthly/yearly comprehensive reports with PDF export |

### 🧪 Machine Learning Predictions

Four trained ML models that accept 7 days of operational data and generate:
- Daily emission predictions with risk levels (Low / Medium / High / Critical)
- Monthly and annual emission forecasts
- Carbon neutrality pathway recommendations

| Model | Input Data | Prediction Output |
|-------|-----------|-------------------|
| **Electricity** | Daily kWh + state | State-adjusted emission forecast |
| **Fuel** | Daily fuel consumption | Combustion emission projections |
| **Transport** | Daily transport logs | Logistics emission predictions |
| **Explosives** | Daily explosive usage | Blasting emission forecasts |

### 🌱 Carbon Neutrality Pathways (6 Modules)

1. **Carbon Sink Estimation** — Calculate sequestration rates for vegetation types, analyze existing sinks, estimate land requirements
2. **Renewable Energy Integration** — Solar, Wind, Hydropower, Hydrogen-Electric cost/benefit analysis with carbon credit calculations
3. **Carbon Capture & Storage (CCS)** — Post-combustion, Pre-combustion, Oxy-fuel technologies with 10-year financial projections
4. **Methane Capture & Storage (MCS)** — Flaring, Catalytic Oxidation, Membrane Separation with 3 utilization strategies (energy, hydrogen, LNG)
5. **AFOLU Analysis** — Agriculture, Forestry, and Other Land Use impact assessment
6. **EV Fleet Optimization** — ICE vs EV comparison with fuel savings and emission reduction metrics

### 🗺️ Additional Features

- **Route Optimization** — OSRM-powered vehicle route optimization with interactive Leaflet maps
- **Regenerative Zone Mapping** — Draw and manage regenerative zones on interactive maps
- **User Profiles** — Cloudinary-hosted profile pictures, CO₂ goals, role management
- **2FA Authentication** — Email-based two-factor authentication with TOTP support
- **PDF Report Generation** — Automated, downloadable environmental reports

---

## 🏗️ Architecture

GreenMines follows a **three-tier microservice architecture**:

```
┌─────────────────────────────────────────────────────────────────┐
│                     CLIENT (Browser)                            │
│                  React 18 + TailwindCSS                         │
│                     Port: 3000                                  │
└───────────────┬─────────────────────────┬───────────────────────┘
                │ REST API                │ Direct HTTP
                ▼                         ▼
┌───────────────────────────┐  ┌─────────────────────────────────┐
│   BACKEND API SERVER      │  │     ML PREDICTION SERVICE       │
│   Node.js + Express       │  │     Python + Flask              │
│   Port: 5000              │  │     Port: 8800                  │
│                           │  │                                 │
│  ┌─────────────────────┐  │  │  ┌───────────────────────────┐  │
│  │  14 Route Files     │  │  │  │  4 ML Models              │  │
│  │  18 Controllers     │  │  │  │  • Electricity             │  │
│  │  1 Service Layer    │  │  │  │  • Fuel                    │  │
│  │  17 Mongoose Models │  │  │  │  • Transport               │  │
│  └─────────────────────┘  │  │  │  • Explosives              │  │
└───────────┬───────────────┘  │  └───────────────────────────┘  │
            │                  └─────────────────────────────────┘
            ▼
┌───────────────────────────┐  ┌─────────────────────────────────┐
│   DATABASE                │  │     EXTERNAL SERVICES           │
│   MongoDB                 │  │                                 │
│   Port: 27017             │  │  • CarbonKit API                │
│   DB: carbon-estimation   │  │  • Carbon Interface API         │
│                           │  │  • Google Gemini Pro AI         │
│   17 Collections          │  │  • Cohere AI                    │
│                           │  │  • OSRM Routing API             │
│                           │  │  • Cloudinary (File Storage)    │
└───────────────────────────┘  └─────────────────────────────────┘
```

### Data Flow

```
User Input → React Frontend → Express API → External APIs / MongoDB → Response
                    │
                    └──→ Flask ML Service → Predictions → Response
```

---

## 🛠 Tech Stack

### Frontend

| Technology | Version | Purpose |
|-----------|---------|---------|
| React | 18.x | UI framework |
| React Router DOM | 6.x | Client-side routing |
| TailwindCSS | 3.x | Utility-first CSS |
| Material UI (MUI) | 5.x | Component library |
| Framer Motion | 11.x | Animations |
| Chart.js + react-chartjs-2 | 4.x / 5.x | Data visualization |
| Leaflet + react-leaflet | 1.9 / 4.2 | Interactive maps |
| Axios | 1.7 | HTTP client |
| jsPDF + html2canvas | 2.5 / 1.4 | PDF generation |
| Lucide React | 0.462 | Icon library |

### Backend

| Technology | Version | Purpose |
|-----------|---------|---------|
| Node.js + Express | 4.21 | REST API server |
| Mongoose | 8.8 | MongoDB ODM |
| JWT (jsonwebtoken) | 9.x | Authentication tokens |
| bcryptjs | 2.4 | Password hashing |
| Speakeasy | 2.0 | TOTP-based 2FA |
| Nodemailer | 6.9 | Email service (2FA, password reset) |
| Helmet | 7.1 | Security headers |
| Cloudinary | 2.5 | Image uploads |
| @google/generative-ai | 0.21 | Google Gemini integration |
| Axios | 1.7 | External API calls |

### ML Service

| Technology | Purpose |
|-----------|---------|
| Python 3.x | Runtime |
| Flask | Web framework |
| Flask-CORS | Cross-origin support |

### Database

| Technology | Purpose |
|-----------|---------|
| MongoDB | Document database |
| 17 Collections | Emissions, sinks, users, zones, etc. |

---

## 🚀 Getting Started

### Prerequisites

Ensure you have the following installed on your system:

| Software | Minimum Version | Download |
|---------|----------------|----------|
| **Node.js** | v18.x or higher | [nodejs.org](https://nodejs.org/) |
| **npm** | v9.x or higher | Bundled with Node.js |
| **Python** | v3.8 or higher | [python.org](https://python.org/) |
| **pip** | Latest | Bundled with Python |
| **MongoDB** | v6.0 or higher | [mongodb.com](https://www.mongodb.com/try/download/community) |
| **Git** | Latest | [git-scm.com](https://git-scm.com/) |

### Installation

**1. Clone the repository**

```bash
git clone https://github.com/your-username/GreenMines.git
cd GreenMines
```

**2. Install Backend dependencies**

```bash
cd Backend
npm install
```

**3. Install Frontend dependencies**

```bash
cd ../Frontend/GreenMines-main
npm install
```

**4. Install ML Service dependencies**

```bash
cd ../../Backend/ML
pip install -r req.txt
```

### Environment Variables

Create a `.env` file in the `Backend/` directory:

```env
# ─── Database ────────────────────────────────────────────
MONGO_URI=mongodb://localhost:27017/carbon-estimation

# ─── Authentication ──────────────────────────────────────
JWT_SECRET=your_jwt_secret_key_here

# ─── Email Service (Nodemailer) ──────────────────────────
AUTHMAIL=your_email@gmail.com
AUTHPASS=your_app_password

# ─── Server Configuration ───────────────────────────────
PORT=5000
FRONTEND_URL=http://localhost:3000

# ─── AI Services ─────────────────────────────────────────
GEMINI_API_KEY=your_gemini_api_key
GEMINI_API_KEY3=your_gemini_api_key_for_reports
COHERE_API_KEY=your_cohere_api_key

# ─── Cloudinary (Profile Pictures) ───────────────────────
CLOUD_NAME=your_cloudinary_cloud_name
CLOUD_KEY=your_cloudinary_api_key
CLOUD_SECRET=your_cloudinary_api_secret
```

Create a `.env` file in `Frontend/GreenMines-main/`:

```env
REACT_APP_BACKEND_URL=http://localhost:5000
```

> **Note:** For the email service, if using Gmail, you'll need to generate an [App Password](https://support.google.com/accounts/answer/185833) with 2FA enabled on your Google account.

### Running the Application

You need **four terminal windows** to run the complete stack:

**Terminal 1 — Start MongoDB**

```bash
# macOS (Homebrew)
brew services start mongodb-community

# Linux
sudo systemctl start mongod

# Windows
net start MongoDB
```

**Terminal 2 — Start Backend Server**

```bash
cd Backend
npm run dev
```

> Server starts at `http://localhost:5000`

**Terminal 3 — Start ML Service**

```bash
cd Backend/ML
python app.py
```

> Flask server starts at `http://localhost:8800`

**Terminal 4 — Start Frontend**

```bash
cd Frontend/GreenMines-main
npm start
```

> React app opens at `http://localhost:3000`

### Verify Installation

| Service | URL | Expected Response |
|---------|-----|-------------------|
| Frontend | http://localhost:3000 | GreenMines landing page |
| Backend API | http://localhost:5000 | Express server running |
| ML Service | http://localhost:8800 | Flask server running |
| MongoDB | mongodb://localhost:27017 | Connection successful |

---

## 📡 API Reference

### Authentication

| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| `POST` | `/api/register` | Register a new user | ❌ |
| `POST` | `/api/login` | Login (triggers 2FA email) | ❌ |
| `POST` | `/api/verify-2fa` | Verify 2FA code → receive JWT | ❌ |
| `POST` | `/api/forgot-password` | Send password reset email | ❌ |
| `POST` | `/api/reset-password` | Reset password with token | ❌ |
| `POST` | `/api/enable-2fa` | Enable TOTP-based 2FA | ✅ |
| `POST` | `/api/setup-2fa` | Generate QR code for 2FA setup | ✅ |

### Emission Calculations

| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/api/electricity-consumption` | Calculate electricity emissions by Indian state |
| `GET` | `/api/fuel-combustion` | Calculate fuel combustion emissions |
| `POST` | `/api/shipping-emissions` | Calculate shipping/transport emissions |
| `POST` | `/api/explosion-emissions` | Calculate explosive emissions |
| `POST` | `/api/coal-emission` | Calculate coal burning emissions |
| `POST` | `/api/methane-emission` | Calculate methane emissions (surface/underground) |

### Data Fetching

| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/api/date/:date` | Fetch all emission data for a specific date |
| `GET` | `/api/date-range/:startDate/:endDate` | Fetch emissions for a date range |
| `DELETE` | `/api/delete/:id` | Delete a specific emission entry |

### Carbon Neutrality Pathways

| Method | Endpoint | Description |
|--------|----------|-------------|
| `POST` | `/api/create-sink` | Create a new carbon sink |
| `POST` | `/api/create-existing-sink` | Register an existing carbon sink |
| `POST` | `/api/calculate-renewable` | Calculate renewable energy impact |
| `POST` | `/api/calculate-ccs` | Calculate Carbon Capture & Storage metrics |
| `POST` | `/api/calculate-mcs` | Calculate Methane Capture & Storage metrics |
| `POST` | `/api/afolu` | Calculate AFOLU impact |

### AI & Reports

| Method | Endpoint | Description |
|--------|----------|-------------|
| `POST` | `/api/genai-analysis` | Run GenAI emission impact analysis |
| `POST` | `/api/chatbot` | Send message to AI chatbot |
| `GET` | `/api/environmental-reports/daily` | Generate daily environmental report |
| `GET` | `/api/environmental-reports/weekly` | Generate weekly environmental report |
| `GET` | `/api/environmental-reports/monthly` | Generate monthly environmental report |
| `GET` | `/api/environmental-reports/yearly` | Generate yearly environmental report |

### Route Optimization

| Method | Endpoint | Description |
|--------|----------|-------------|
| `POST` | `/api/optimize-route` | Optimize vehicle routes using OSRM |

### ML Prediction Endpoints (Port 8800)

| Method | Endpoint | Description |
|--------|----------|-------------|
| `POST` | `/ml/electricity` | Predict electricity emissions |
| `POST` | `/ml/fuel` | Predict fuel emissions |
| `POST` | `/ml/transport` | Predict transport emissions |
| `POST` | `/ml/explosive` | Predict explosive emissions |

---

## 🧪 ML Models

### How Predictions Work

Each ML model follows the same pipeline:

```
7 Days Input Data → Daily Prediction → Risk Assessment → Monthly Aggregation → Neutrality Pathway
```

### Request Format

```json
{
  "days_data": [
    { "day": 1, "value": 1200 },
    { "day": 2, "value": 1350 },
    { "day": 3, "value": 980 },
    { "day": 4, "value": 1100 },
    { "day": 5, "value": 1450 },
    { "day": 6, "value": 1280 },
    { "day": 7, "value": 1150 }
  ],
  "state_name": "Maharashtra"
}
```

> **Note:** `state_name` is only required for the electricity model.

### Response Format

```json
{
  "status": "success",
  "monthly_summary": {
    "total_emissions": 38500.00,
    "average_daily_emissions": 1283.33,
    "risk_level": "Moderate",
    "predictions": [...],
    "neutrality_recommendations": [...]
  }
}
```

### Risk Level Thresholds

| Level | Color | Description |
|-------|-------|-------------|
| 🟢 Low | Green | Emissions within acceptable limits |
| 🟡 Moderate | Yellow | Emissions approaching threshold |
| 🟠 High | Orange | Emissions exceed safe limits |
| 🔴 Critical | Red | Immediate action required |

---

## 📁 Project Structure

```
GreenMines/
├── Backend/
│   ├── config/
│   │   └── db.js                    # MongoDB connection configuration
│   ├── controller/
│   │   ├── Emission.js              # Electricity, fuel, shipping, explosives, coal
│   │   ├── authController.js        # Register, login, 2FA, password reset
│   │   ├── methaneController.js     # Surface & underground methane
│   │   ├── sink.js                  # Sinks, renewables, CCS, MCS
│   │   ├── genaiController.js       # Cohere AI emission impact analysis
│   │   ├── chatbot.js               # Google Gemini chatbot
│   │   ├── datafetching.js          # Date-based data queries
│   │   ├── environmentalReportController.js  # Report generation
│   │   ├── routeController.js       # OSRM route optimization
│   │   ├── userController.js        # Profile, picture upload, CO₂ goals
│   │   ├── afoluController.js       # AFOLU calculations
│   │   ├── evCalculationscontroller.js  # EV savings
│   │   ├── landRequiredController.js    # Land requirements
│   │   ├── zoneController.js        # Regenerative zones
│   │   └── ...
│   ├── models/
│   │   ├── User.js                  # User schema (auth, 2FA, profile)
│   │   ├── Electricity.js           # Electricity emission records
│   │   ├── FuelCombustion.js        # Fuel emission records
│   │   ├── Shipping.js              # Shipping emission records
│   │   ├── Explosion.js             # Explosion emission records
│   │   ├── coalEmission.js          # Coal burning records
│   │   ├── Methane.js               # Methane emission records
│   │   ├── Sink.js                  # Carbon sink records
│   │   ├── ExistingSink.js          # Existing sink records
│   │   ├── Renewable.js             # Renewable energy records
│   │   ├── ccs.js                   # CCS calculation records
│   │   ├── mcs.js                   # MCS calculation records
│   │   ├── evCalculations.js        # EV savings records
│   │   ├── Zone.js                  # Regenerative zone records
│   │   └── ...
│   ├── routes/
│   │   ├── emissionRoute.js         # /api/electricity, /api/fuel, ...
│   │   ├── authRoutes.js            # /api/register, /api/login, ...
│   │   ├── sinkRoute.js             # /api/create-sink, ...
│   │   ├── genaiRoute.js            # /api/genai-analysis
│   │   ├── chatbotRoute.js          # /api/chatbot
│   │   ├── environmentalReportRoute.js  # /api/environmental-reports/*
│   │   ├── optimizeRoute.js         # /api/optimize-route
│   │   └── ...
│   ├── services/
│   │   └── geminiReportService.js   # Google Gemini report generation
│   ├── ML/
│   │   ├── app.py                   # Flask server (port 8800)
│   │   ├── Electricity/
│   │   │   └── electricity.py       # Electricity prediction model
│   │   ├── Fuel/
│   │   │   └── fuel.py              # Fuel prediction model
│   │   ├── Transport/
│   │   │   └── transport.py         # Transport prediction model
│   │   ├── Explosives/
│   │   │   └── explosive.py         # Explosives prediction model
│   │   └── req.txt                  # Python dependencies
│   ├── server.js                    # Express app entry point
│   ├── package.json
│   └── .env                         # Environment variables
│
├── Frontend/
│   └── GreenMines-main/
│       ├── public/
│       ├── src/
│       │   ├── App.jsx              # Root component with all routes
│       │   ├── Components/
│       │   │   ├── Header.jsx           # Landing page hero
│       │   │   ├── Navbar.jsx           # Navigation bar
│       │   │   ├── Footer.jsx           # Footer
│       │   │   ├── EmissionForm.jsx     # Master emission calculator
│       │   │   ├── DashBoard.jsx        # Real-time dashboard
│       │   │   ├── Predictions.jsx      # ML predictions interface
│       │   │   ├── Chatbot.jsx          # AI chatbot
│       │   │   ├── CCS.jsx             # Carbon Capture & Storage
│       │   │   ├── MCS.jsx             # Methane Capture & Storage
│       │   │   ├── RouteFrm.jsx         # Route optimization (Leaflet)
│       │   │   ├── RegenerativeZoneMap.jsx  # Zone mapping
│       │   │   ├── Profile.jsx          # User profile management
│       │   │   ├── Login.jsx            # Authentication
│       │   │   ├── EnvironmentalReport/ # Report sub-components
│       │   │   │   ├── ReportDisplay.jsx
│       │   │   │   ├── ReportStats.jsx
│       │   │   │   ├── PDFDownloadButton.jsx
│       │   │   │   └── Charts/
│       │   │   └── ... (66 components total)
│       │   ├── pages/
│       │   │   └── EnvironmentalReportPage.jsx
│       │   ├── services/
│       │   │   └── environmentalReportService.jsx
│       │   ├── index.js
│       │   └── index.css
│       ├── tailwind.config.js
│       ├── package.json
│       └── .env
│
└── README.md
```

---

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. **Fork** the repository
2. **Create** a feature branch
   ```bash
   git checkout -b feature/your-feature-name
   ```
3. **Commit** your changes with descriptive messages
   ```bash
   git commit -m "feat: add new emission calculator for XYZ"
   ```
4. **Push** to your branch
   ```bash
   git push origin feature/your-feature-name
   ```
5. **Open** a Pull Request with a detailed description

### Commit Convention

| Prefix | Usage |
|--------|-------|
| `feat:` | New feature |
| `fix:` | Bug fix |
| `docs:` | Documentation changes |
| `style:` | Code style/formatting |
| `refactor:` | Code refactoring |
| `test:` | Adding/updating tests |
| `chore:` | Maintenance tasks |

---

## 📄 License

This project is licensed under the **ISC License**. See the [LICENSE](LICENSE) file for details.

---

## 🙏 Acknowledgements

- [CarbonKit API](https://www.carbonkit.net/) — Electricity and fuel emission factors
- [Carbon Interface](https://www.carboninterface.com/) — Shipping emission calculations
- [Google Gemini](https://ai.google.dev/) — Generative AI for chatbot and reports
- [Cohere AI](https://cohere.com/) — Emission impact analysis
- [OSRM](http://project-osrm.org/) — Open-source route optimization
- [Cloudinary](https://cloudinary.com/) — Image hosting and management
- [Leaflet](https://leafletjs.com/) — Interactive mapping

---

<p align="center">
  <strong>Built with 💚 for a sustainable future</strong>
</p>

<p align="center">
  <a href="#greenmines">⬆ Back to Top</a>
</p>
