# 🌍 Wander AI — AI-Based Personalized Travel Recommendation App

Wander AI is a full-stack **AI-based personalized travel recommendation application** designed to make trip planning easier, faster, and more personalized. Instead of manually searching through multiple travel websites, users can provide their **budget, interests, travel duration, number of travelers, and travel preferences**, and the application generates suitable destination recommendations and personalized trip plans.

The application combines a **React Native Android app**, **Express.js backend**, **MongoDB**, AI services, weather information, maps, and personalized recommendation logic into a single travel-planning experience.

Users can discover destinations, receive personalized recommendations, generate day-by-day itineraries, view maps and weather information, interact with an AI travel assistant, save trips, and manage their travel history.

---

## 📌 Table of Contents

* [Project Overview](#-project-overview)
* [Problem Statement](#-problem-statement)
* [Objectives](#-objectives)
* [Key Features](#-key-features)
* [How the Application Works](#-how-the-application-works)
* [Technology Stack](#-technology-stack)
* [Project Architecture](#-project-architecture)
* [Project Structure](#-project-structure)
* [Prerequisites](#-prerequisites)
* [Installation and Setup](#-installation-and-setup)
* [Backend Setup](#-backend-setup)
* [MongoDB Atlas Setup](#-mongodb-atlas-setup)
* [Frontend Setup](#-frontend-setup)
* [Environment Variables](#-environment-variables)
* [Running the Application](#-running-the-application)
* [Testing](#-testing)
* [Application Modules](#-application-modules)
* [API Overview](#-api-overview)
* [Admin Module](#-admin-module)
* [Maps and Weather](#-maps-and-weather)
* [AI Integration](#-ai-integration)
* [Fallback and Error Handling](#-fallback-and-error-handling)
* [Troubleshooting](#-troubleshooting)
* [APK Build](#-apk-build)
* [Future Scope](#-future-scope)
* [Conclusion](#-conclusion)

---

# 🌍 Project Overview

Planning a trip can require a user to search across different platforms for destinations, activities, budgets, weather conditions, maps, and itineraries. This can make the planning process time-consuming and difficult, especially when the user has specific requirements.

**Wander AI** provides a centralized travel-planning solution.

The user enters their preferences such as:

* Travel destination or destination preferences
* Budget
* Interests
* Travel duration
* Number of travelers
* Travel style
* Activities and preferences

The system processes these requirements and provides personalized destination recommendations. After selecting a destination, the user can generate a complete day-by-day itinerary containing activities, estimated costs, mapped locations, weather information, packing suggestions, and local tips.

The application also includes an AI-powered travel assistant that allows users to ask questions and refine their trip.

---

# ❗ Problem Statement

Traditional travel planning often requires users to visit multiple platforms to find destination information, activities, accommodation-related information, maps, weather forecasts, budget estimates, and itineraries.

Most existing travel platforms primarily focus on booking or destination discovery, while users still need to manually combine information and create their own personalized itinerary.

The problem addressed by Wander AI is:

> **How can travel planning be simplified by providing personalized destination recommendations and intelligent trip planning based on a user's budget, interests, duration, and preferences within a single application?**

---

# 🎯 Objectives

The main objectives of Wander AI are:

1. To simplify the travel-planning process.
2. To provide personalized destination recommendations.
3. To consider user budget and travel preferences while recommending destinations.
4. To generate day-by-day travel itineraries.
5. To provide travel-related weather information.
6. To display destinations and itinerary stops on maps.
7. To provide an AI-powered travel assistant.
8. To allow users to save and manage their trips.
9. To provide an admin module for managing destination information.
10. To create a practical mobile application using modern full-stack technologies.

---

# ✨ Key Features

## 1. 👤 User Registration and Login

Users can create an account and securely log in to the application.

The authentication system uses:

* User registration
* User login
* JWT-based authentication
* Protected API routes
* User profile management

---

## 2. 🧭 Personalized Preferences

During onboarding, users can provide their travel preferences.

Examples include:

* Budget range
* Travel interests
* Travel style
* Preferred activities
* Travel duration
* Number of travelers

These preferences are used to personalize recommendations.

---

## 3. 🤖 AI Travel Planner

The AI planner is one of the core features of Wander AI.

The user provides travel requirements, and the system processes them to generate suitable recommendations.

The planner can consider:

* Destination
* Budget
* Duration
* Travelers
* Interests
* Currency
* Travel preferences

---

## 4. 🏆 Personalized Destination Recommendations

The application provides ranked destination recommendations based on the user's requirements.

The recommendation system can display:

* Destination name
* Match score
* Attractions
* Budget information
* Travel tags
* Destination details

The backend exposes a dedicated recommendation API:

```text
POST /api/ai/recommendations
```

---

## 5. 🗓️ AI-Generated Itinerary

After selecting a destination, users can generate a day-by-day itinerary.

Each day can contain:

```text
Morning
Afternoon
Evening
```

The itinerary can include:

* Activities
* Locations
* Estimated costs
* Coordinates
* Daily plans
* Local tips
* Packing information

---

## 6. 💰 Budget Planner

Wander AI provides estimated trip costs and budget breakdowns.

The system can organize costs into categories and calculate a total estimated budget.

This helps users understand whether a recommended trip fits their planned budget.

---

## 7. 🗺️ Maps and Navigation

The application provides mapped travel stops and destination locations.

The native Android application uses:

```text
react-native-maps
```

The map can display:

* Destination
* Itinerary stops
* Coordinates
* Routes
* Day-wise locations

The project also provides a map fallback for environments where the native map service is unavailable.

---

## 8. 🌦️ Weather Information

Users can view weather information related to their trip.

The default weather provider is:

```text
Open-Meteo
```

The project is designed so that weather information can work without requiring an API key when using the default provider.

---

## 9. 💬 AI Travel Assistant

Wander AI includes an AI-powered chat assistant named **Atlas**.

Users can ask questions related to their trip, such as:

```text
What should I visit on Day 2?
```

```text
How can I reduce my trip budget?
```

```text
What should I pack for this destination?
```

The assistant can use the selected trip as context.

---

## 10. ❤️ Saved Trips

Users can save their generated trips for later use.

Saved information can include:

* Destination
* Itinerary
* Budget
* Weather
* Activities
* Trip information

The application also supports cached trip data for offline-friendly access.

---

## 11. 📜 Trip History

Users can view previously generated trips.

Trips can be organized using filters such as:

* All
* Saved
* Drafts

---

## 12. 👤 User Profile

The profile section provides:

* User information
* Travel preferences
* Trip statistics
* Saved trips
* Account options
* Admin entry for authorized users

---

## 13. 🛠️ Admin Module

An admin module is included for managing the destination catalogue.

Authorized administrators can:

* View destinations
* Add destinations
* Edit destinations
* Delete destinations

Destination management APIs are protected using admin authorization.

---

# 🔄 How the Application Works

The general workflow is:

```text
User
  ↓
Register / Login
  ↓
Set Travel Preferences
  ↓
Enter Trip Requirements
  ↓
Personalized Recommendation Engine
  ↓
Ranked Destinations
  ↓
Select Destination
  ↓
Generate AI Itinerary
  ↓
Budget + Activities + Weather + Map
  ↓
AI Travel Assistant
  ↓
Save Trip
  ↓
View Trip History
```

---

# 🛠️ Technology Stack

## 📱 Frontend

| Technology              | Purpose                                        |
| ----------------------- | ---------------------------------------------- |
| React Native            | Android mobile application                     |
| Expo                    | React Native development and build environment |
| Expo Router             | File-based application navigation              |
| JavaScript / TypeScript | Application logic                              |
| NativeWind              | Styling                                        |
| React Native Maps       | Native map functionality                       |
| AsyncStorage            | Local/cached trip data                         |

The project uses Expo-based React Native development and Expo Router for application navigation.

---

## 🖥️ Backend

| Technology | Purpose                     |
| ---------- | --------------------------- |
| Node.js    | Server-side runtime         |
| Express.js | Backend framework           |
| Mongoose   | MongoDB object modeling     |
| JWT        | Authentication              |
| REST API   | Client-server communication |

The backend follows an Express + MongoDB architecture.

---

## 🗄️ Database

| Technology    | Purpose              |
| ------------- | -------------------- |
| MongoDB       | Application database |
| MongoDB Atlas | Cloud database       |
| Mongoose      | Database interaction |

MongoDB Atlas is recommended for persistent data storage. The project can also use an in-memory MongoDB during development when configured accordingly.

---

## 🤖 AI

| Technology | Purpose                                        |
| ---------- | ---------------------------------------------- |
| OpenRouter | AI model API                                   |
| AI Models  | Recommendations, itinerary generation and chat |

OpenRouter is optional. If it is not configured, the application can use curated fallback data.

---

## 🌦️ Weather

Primary provider:

```text
Open-Meteo
```

OpenWeatherMap can also be configured as an alternative provider.

---

## 🗺️ Maps

The application supports:

* React Native Maps
* Google Maps on Android
* OpenStreetMap-based fallback
* Mapbox static map support

---

# 🏗️ Project Architecture

```text
                   ┌───────────────────────┐
                   │      Android User     │
                   └───────────┬───────────┘
                               │
                               ▼
                   ┌───────────────────────┐
                   │ React Native + Expo   │
                   │      Frontend         │
                   └───────────┬───────────┘
                               │
                         REST API / HTTP
                               │
                               ▼
                   ┌───────────────────────┐
                   │   Node.js + Express   │
                   │       Backend         │
                   └───────┬───────┬───────┘
                           │       │
              ┌────────────┘       └─────────────┐
              ▼                                  ▼
     ┌─────────────────┐                ┌─────────────────┐
     │ MongoDB Atlas   │                │   AI Services   │
     │    Database     │                │    OpenRouter   │
     └─────────────────┘                └─────────────────┘
                           │
              ┌────────────┴─────────────┐
              ▼                          ▼
     ┌─────────────────┐        ┌──────────────────┐
     │ Weather Service │        │ Maps / Locations │
     │   Open-Meteo    │        │ Google / OSM     │
     └─────────────────┘        └──────────────────┘
```

---

# 📁 Project Structure

```text
travel-app/
│
├── backend/
│   ├── src/
│   │   ├── controllers/
│   │   ├── middleware/
│   │   ├── models/
│   │   ├── routes/
│   │   ├── services/
│   │   └── server.js
│   │
│   ├── scripts/
│   ├── .env.example
│   ├── package.json
│   └── ...
│
├── frontend/
│   ├── app/
│   │   ├── (auth)/
│   │   ├── (tabs)/
│   │   ├── trip/
│   │   ├── recommendations/
│   │   └── admin/
│   │
│   ├── components/
│   ├── services/
│   ├── assets/
│   ├── .env.example
│   ├── app.json
│   ├── package.json
│   └── ...
│
└── README.md
```

---

# 💻 Prerequisites

Before running Wander AI, install:

### Required

* Node.js
* npm
* Git
* VS Code or another code editor
* Expo Go for physical Android testing

### For database

Either:

* MongoDB Atlas

or

* Configured local/in-memory MongoDB development setup

### For Android emulator

* Android Studio
* Android SDK
* Android Emulator

---

# 🚀 Installation and Setup

## 1. Clone the repository

```bash
git clone <YOUR_GITHUB_REPOSITORY_URL>
```

Move into the project:

```bash
cd travel-app
```

---

# 🖥️ Backend Setup

Open Terminal 1:

```bash
cd backend
```

Install dependencies:

```bash
npm install
```

Create the environment file.

Windows:

```bash
copy .env.example .env
```

Then configure your `.env`.

Start the backend:

```bash
npm run dev
```

The backend runs on:

```text
http://localhost:5000
```

Health-check endpoint:

```text
http://localhost:5000/api/health
```

---

# 🗄️ MongoDB Atlas Setup

For reliable development, MongoDB Atlas is recommended.

## Step 1 — Create an Atlas account

Create an account on MongoDB Atlas.

## Step 2 — Create a free cluster

Create a development database/cluster.

## Step 3 — Create a database user

Create a username and password.

Example:

```text
Username: wanderai
Password: ********
```

## Step 4 — Configure Network Access

Add your development IP address to the Atlas Network Access list.

## Step 5 — Get the connection string

From:

```text
Database
→ Connect
→ Drivers
→ Node.js
```

copy the MongoDB connection string.

## Step 6 — Add it to `.env`

```env
MONGO_URI=mongodb+srv://USERNAME:PASSWORD@YOUR_CLUSTER.mongodb.net/wanderai
```

Also configure:

```env
ALLOW_IN_MEMORY_DB=false
```

### ⚠️ Security

Never upload `.env` to GitHub.

Your `.gitignore` should contain:

```text
.env
node_modules/
```

Never commit:

* MongoDB passwords
* JWT secrets
* OpenRouter API keys
* Google Maps API keys
* Mapbox tokens

---

# 📱 Frontend Setup

Open Terminal 2:

```bash
cd frontend
```

Install dependencies:

```bash
npm install
```

Create the environment file:

```bash
copy .env.example .env
```

Then configure the backend URL.

---

# 🔗 Environment Variables

## Backend `.env`

Example:

```env
PORT=5000

MONGO_URI=mongodb+srv://USERNAME:PASSWORD@YOUR_CLUSTER.mongodb.net/wanderai

ALLOW_IN_MEMORY_DB=false

JWT_SECRET=your_development_secret

OPENROUTER_API_KEY=

OPENROUTER_PRIMARY_MODEL=

OPENROUTER_FALLBACK_MODELS=

WEATHER_PROVIDER=open-meteo

MAPBOX_ACCESS_TOKEN=

CLOUDINARY_CLOUD_NAME=
CLOUDINARY_API_KEY=
CLOUDINARY_API_SECRET=
```

Only configure services that you actually use.

---

## Frontend `.env`

### Physical Android phone

Use your computer's local IP address:

```env
EXPO_PUBLIC_API_URL=http://YOUR-LAN-IP:5000/api
```

Example:

```env
EXPO_PUBLIC_API_URL=http://192.168.1.105:5000/api
```

### Android emulator

Use:

```env
EXPO_PUBLIC_API_URL=http://10.0.2.2:5000/api
```

`10.0.2.2` allows the Android emulator to access the host computer.

---

# ▶️ Running the Application

You need **two terminals**.

## Terminal 1 — Backend

```bash
cd travel-app/backend
npm run dev
```

## Terminal 2 — Frontend

```bash
cd travel-app/frontend
npx expo start
```

Expo will display a QR code.

---

# 📲 Running on a Physical Android Phone

1. Install Expo Go.
2. Connect your phone and laptop to the same Wi-Fi.
3. Start the backend.
4. Start Expo.
5. Make sure `EXPO_PUBLIC_API_URL` contains your laptop's LAN IP.
6. Scan the Expo QR code.
7. Open the application.

Example:

```env
EXPO_PUBLIC_API_URL=http://192.168.1.105:5000/api
```

Do **not** use:

```env
EXPO_PUBLIC_API_URL=http://localhost:5000/api
```

on a physical phone.

---

# 🤖 Running on Android Emulator

Start Android Studio and launch an Android emulator.

Then:

```bash
npx expo start
```

Press:

```text
a
```

Expo will attempt to open the Android application.

Use:

```env
EXPO_PUBLIC_API_URL=http://10.0.2.2:5000/api
```

for the backend connection.

---

# 🧪 Testing

Wander AI includes automated backend testing.

## Backend Smoke Test

Start the backend:

```bash
cd backend
npm run dev
```

Open another terminal:

```bash
cd backend
npm run smoke
```

The smoke test covers the major application journey, including:

```text
Register
↓
Preferences
↓
Recommendations
↓
Itinerary
↓
Map
↓
Weather
↓
Chat
↓
Save
↓
Edit
↓
Delete
```

It also checks authentication protection, ownership isolation, admin authorization and related backend behavior.

---

# 🔍 Frontend Type Checking

Run:

```bash
cd frontend
npx tsc --noEmit
```

This checks the frontend TypeScript code without generating build files.

---

# 🤖 AI Path Testing

The backend contains mock OpenRouter testing scenarios.

Example:

```bash
cd backend

for s in clean prose truncated allfail; do
  MOCK_SCENARIO=$s node scripts/mockOpenRouter.js & sleep 1
  MOCK_SCENARIO=$s node scripts/aiPathTest.js
  kill %1
done
```

These tests verify behavior for situations such as:

* Valid AI response
* Rate limiting
* JSON wrapped in Markdown
* Prose-wrapped JSON
* Truncated responses
* Invalid coordinates
* Failed AI responses

The project is designed to continue operating using fallback data when AI generation fails.

---

# 🧩 Application Modules

## Authentication Module

```text
Register
Login
Logout
Current User
Password Change
Profile
```

## Preference Module

```text
Travel Interests
Budget
Duration
Travel Style
Activities
Other Preferences
```

## Recommendation Module

```text
User Preferences
      ↓
Recommendation Processing
      ↓
Destination Ranking
      ↓
Match Scores
```

## Trip Planning Module

```text
Destination
      ↓
Duration
      ↓
Travelers
      ↓
Budget
      ↓
AI Planner
      ↓
Day-wise Itinerary
```

## Trip Management Module

```text
Create Trip
Edit Trip
Save Trip
View Trip
Delete Trip
Trip History
```

## Chat Module

```text
User Question
      ↓
Trip Context
      ↓
AI Assistant
      ↓
Travel Response
```

## Admin Module

```text
Admin Login
      ↓
Destination Catalogue
      ↓
Add / Edit / Delete
```

---

# 🔌 API Overview

Base API:

```text
http://localhost:5000/api
```

Protected routes use:

```text
Authorization: Bearer <token>
```

---

## Authentication

| Method | Endpoint         | Purpose         |
| ------ | ---------------- | --------------- |
| POST   | `/auth/register` | Create account  |
| POST   | `/auth/login`    | Login           |
| GET    | `/auth/me`       | Current user    |
| PUT    | `/auth/password` | Change password |

---

## Users

| Method | Endpoint                     | Purpose            |
| ------ | ---------------------------- | ------------------ |
| GET    | `/users/preferences/options` | Preference options |
| PUT    | `/users/preferences`         | Save preferences   |
| PUT    | `/users/profile`             | Update profile     |
| GET    | `/users/stats`               | User statistics    |
| DELETE | `/users/me`                  | Delete account     |

---

## AI

| Method | Endpoint              | Purpose                     |
| ------ | --------------------- | --------------------------- |
| POST   | `/ai/recommendations` | Destination recommendations |
| POST   | `/ai/itinerary`       | Generate itinerary          |
| POST   | `/ai/chat`            | AI travel assistant         |
| GET    | `/ai/chat/history`    | Chat history                |
| DELETE | `/ai/chat/history`    | Clear chat history          |
| GET    | `/ai/health`          | AI configuration status     |

---

## Trips

| Method | Endpoint             | Purpose          |
| ------ | -------------------- | ---------------- |
| GET    | `/trips`             | List trips       |
| POST   | `/trips`             | Create trip      |
| GET    | `/trips/:id`         | Get trip         |
| PUT    | `/trips/:id`         | Edit trip        |
| PATCH  | `/trips/:id/save`    | Save/unsave trip |
| POST   | `/trips/:id/weather` | Refresh weather  |
| GET    | `/trips/:id/map`     | Get map data     |
| DELETE | `/trips/:id`         | Delete trip      |

---

## Destinations and Weather

| Method | Endpoint            | Purpose               |
| ------ | ------------------- | --------------------- |
| GET    | `/destinations`     | Destination catalogue |
| POST   | `/destinations/:id` | Admin operation       |
| PUT    | `/destinations/:id` | Admin operation       |
| DELETE | `/destinations/:id` | Admin operation       |
| GET    | `/weather`          | Weather forecast      |
| GET    | `/weather/geocode`  | City coordinates      |

The API routes above correspond to the application's documented backend API structure.

---

# 👨‍💼 Admin Module

A demo admin account can be created by running:

```bash
cd backend
npm run seed
```

The seed script creates destination data and a demo administrator account in the development setup.

The admin module allows authorized administrators to manage destination catalogue information.

### Admin Operations

```text
View Destinations
       ↓
Add Destination
       ↓
Edit Destination
       ↓
Delete Destination
```

---

# 🗺️ Maps and Weather

## Maps

The Android application uses native map functionality through:

```text
react-native-maps
```

Google Maps requires an Android Maps API key for the interactive native map in a standalone build.

The environment variable is:

```env
EXPO_PUBLIC_GOOGLE_MAPS_ANDROID_KEY=YOUR_GOOGLE_MAPS_KEY
```

The project also provides a keyless OpenStreetMap-based fallback for map previews.

---

## Weather

The default provider is:

```text
Open-Meteo
```

This provider is used because it can provide weather information without requiring an API key.

An alternative OpenWeatherMap configuration is also supported.

---

# 🤖 AI Integration

Wander AI uses **OpenRouter** for AI-powered functionality.

AI functionality includes:

```text
Personalized Recommendations
        ↓
Itinerary Generation
        ↓
AI Travel Chat
```

The backend can be configured with:

```env
OPENROUTER_API_KEY=YOUR_API_KEY
```

AI models can be configured through:

```env
OPENROUTER_PRIMARY_MODEL=YOUR_MODEL
OPENROUTER_FALLBACK_MODELS=MODEL_1,MODEL_2
```

AI model availability can change over time, especially for free model identifiers, so the model configuration should be checked when an unavailable-model error occurs.

---

# 🛡️ Fallback and Error Handling

One important design feature of Wander AI is that the application is designed to **degrade gracefully** instead of completely failing when an external service is unavailable.

Examples:

| Problem                     | Application Behavior                                  |
| --------------------------- | ----------------------------------------------------- |
| No OpenRouter API key       | Uses curated/demo data                                |
| AI model unavailable        | Tries fallback models                                 |
| AI request rate-limited     | Uses fallback behavior                                |
| AI returns malformed JSON   | Attempts to sanitize/repair response                  |
| Weather service unavailable | Uses fallback climate estimates                       |
| No Mapbox token             | Uses OSM map fallback                                 |
| Backend unavailable         | Cached trips can still be displayed                   |
| No MongoDB URI              | Development in-memory database can be used if enabled |

This behavior is part of the project's documented resilience strategy.

---

# 🐛 Troubleshooting

## ❌ `MONGO_URI is not set`

If you see:

```text
[db] MONGO_URI is not set.
```

configure MongoDB Atlas in:

```text
backend/.env
```

Example:

```env
MONGO_URI=mongodb+srv://USERNAME:PASSWORD@CLUSTER.mongodb.net/wanderai
```

---

## ❌ MongoMemoryServer timeout

If the project tries to start:

```text
MongoMemoryServer
```

and fails with:

```text
Instance failed to start within 10000ms
```

use MongoDB Atlas instead of relying on the temporary in-memory database.

Set:

```env
MONGO_URI=your_mongodb_atlas_connection_string
ALLOW_IN_MEMORY_DB=false
```

Then restart:

```bash
npm run dev
```

---

## ❌ Cannot reach the server

Check:

1. Backend is running.
2. Port `5000` is available.
3. Frontend API URL is correct.
4. Phone and laptop are connected to the same Wi-Fi.
5. Windows Firewall is not blocking port `5000`.
6. Restart Expo after changing `.env`.

For a physical phone:

```env
EXPO_PUBLIC_API_URL=http://YOUR-LAN-IP:5000/api
```

For Android emulator:

```env
EXPO_PUBLIC_API_URL=http://10.0.2.2:5000/api
```

---

## ❌ Expo connection timeout

Make sure your phone and computer are on the same network.

If the normal LAN connection doesn't work, Expo can be started using a tunnel:

```bash
npx expo start --tunnel
```

---

## ❌ Changes are not appearing

Clear the Expo/Metro cache:

```bash
npx expo start --clear
```

The project documentation also recommends restarting Expo after changing environment variables.

---

## ❌ Blank map

For a standalone Android build, check:

```env
EXPO_PUBLIC_GOOGLE_MAPS_ANDROID_KEY=YOUR_KEY
```

The prototype also contains an OSM fallback if Google Maps is not configured.

---

## ❌ AI says "Demo data"

This generally means the AI provider isn't configured or the configured provider/model isn't currently available.

Check:

```env
OPENROUTER_API_KEY=
OPENROUTER_PRIMARY_MODEL=
```

The application is intentionally designed to fall back to curated data.

---

# 📦 APK Build

The project uses Expo Application Services (**EAS**) to create an Android APK.

Install EAS CLI:

```bash
npm install -g eas-cli
```

Login:

```bash
eas login
```

From the frontend directory:

```bash
cd frontend
```

Configure EAS:

```bash
eas build:configure
```

Build an Android preview APK:

```bash
eas build -p android --profile preview
```

The cloud build does not require the Android SDK on your computer and provides a build result through EAS.

---

# 🧪 Recommended Testing Checklist

Before presenting the project, test the following:

### Authentication

* [ ] Register
* [ ] Login
* [ ] Logout
* [ ] Invalid login
* [ ] Protected screen

### Preferences

* [ ] Select interests
* [ ] Select budget
* [ ] Select duration
* [ ] Save preferences
* [ ] Edit preferences

### AI Planner

* [ ] Enter trip requirements
* [ ] Generate recommendations
* [ ] View match scores
* [ ] Select destination
* [ ] Generate itinerary

### Trip

* [ ] View itinerary
* [ ] View budget
* [ ] View weather
* [ ] Open map
* [ ] Save trip
* [ ] Edit trip
* [ ] Delete trip

### AI Chat

* [ ] Send question
* [ ] Receive response
* [ ] Check trip context
* [ ] View chat history

### Admin

* [ ] Admin login
* [ ] View destinations
* [ ] Add destination
* [ ] Edit destination
* [ ] Delete destination
* [ ] Verify normal users cannot access admin operations

---

# 🚀 Future Scope

Possible future improvements include:

* Hotel and accommodation recommendations
* Flight and transportation integration
* Real-time booking integration
* More advanced machine-learning recommendations
* User feedback-based recommendation improvement
* Multi-language support
* Voice-based travel assistant
* Real-time travel alerts
* Currency conversion
* More detailed expense tracking
* Social trip sharing
* Collaborative group trip planning
* Push notifications
* More advanced offline functionality
* Production deployment and scalable cloud infrastructure

---

# 📊 Main Advantages

Wander AI provides several advantages compared with traditional manual travel planning:

### Personalized

Recommendations are based on the user's requirements rather than providing the same generic destination list to everyone.

### Centralized

Destination recommendations, itineraries, maps, weather, budget information and AI assistance are available within one application.

### Intelligent

AI can assist with recommendations, itinerary generation and conversational trip refinement.

### Flexible

Users can modify and save their trips according to their requirements.

### Resilient

The application includes fallback behavior for unavailable AI, weather and map services.

---

# 🎓 Academic Project Information

**Project Title:**
AI-Based Personalized Travel Recommendation App

**Application Name:**
Wander AI

**Project Type:**
Full-Stack Mobile Application

**Primary Domain:**
Artificial Intelligence / AI-Based Recommendation

**Platform:**
Android

**Frontend:**
React Native + Expo

**Backend:**
Node.js + Express.js

**Database:**
MongoDB / MongoDB Atlas

**AI Integration:**
OpenRouter

**Weather:**
Open-Meteo

**Maps:**
React Native Maps / OpenStreetMap fallback

---

# 👥 User Roles

## Traveler / User

A normal user can:

* Register
* Login
* Set preferences
* Get personalized recommendations
* Generate itineraries
* View maps
* View weather
* Chat with AI
* Save trips
* Edit trips
* Delete trips
* View trip history

## Administrator

An administrator can:

* Access the admin module
* Manage destinations
* Add destination information
* Edit destination information
* Delete destinations

---

# 🔐 Security Considerations

The application uses authentication and protected routes to control access to user-specific functionality.

Important security practices include:

* JWT authentication
* Protected API endpoints
* User ownership checks
* Admin authorization
* Password hashing
* Environment variables for secrets
* `.env` excluded from version control

Never expose private API keys or database credentials in source code.

---

# 📚 Development Commands

## Backend

```bash
cd backend
npm install
npm run dev
npm run seed
npm run smoke
```

## Frontend

```bash
cd frontend
npm install
npx expo start
npx expo start --clear
```

## Frontend Type Check

```bash
npx tsc --noEmit
```

## Android APK

```bash
eas build -p android --profile preview
```

---

# 🏁 Conclusion

Wander AI is an AI-based personalized travel recommendation application developed to simplify the complete travel-planning process. The application combines **React Native and Expo for mobile development, Node.js and Express.js for backend services, MongoDB for data storage, OpenRouter for AI functionality, weather services, and map integration** into one platform.

The key idea of the application is personalization. Instead of forcing every traveler to manually search through different platforms, Wander AI uses the user's **budget, interests, duration, number of travelers, and preferences** to generate suitable destinations and personalized itineraries.

The application goes beyond simple destination searching by providing **AI recommendations, day-wise itinerary generation, budget estimation, weather information, maps, an AI travel assistant, saved trips, trip history, and an administrative destination catalogue**.

With its combination of AI, mobile development, full-stack architecture, external API integration, and fallback mechanisms, Wander AI demonstrates how modern technologies can be used to create a practical and intelligent travel-planning solution.

---

# ⭐ Project Highlights

```text
🤖 AI-Based Personalized Recommendations
🗓️ Day-by-Day AI Itinerary
💰 Budget Planning
🗺️ Interactive Maps
🌦️ Weather Information
💬 AI Travel Assistant
❤️ Saved Trips
📜 Trip History
👤 User Profiles
🛠️ Admin Destination Management
🔐 JWT Authentication
🗄️ MongoDB Atlas
📱 React Native Android App
⚡ Expo Development
```

---

## 📄 License

This project is developed for **academic/educational purposes**.

---

## 🙏 Acknowledgement

This project uses open-source technologies and third-party services including React Native, Expo, Node.js, Express.js, MongoDB, OpenRouter, Open-Meteo, OpenStreetMap and related libraries.

---

**Made with ❤️ for smarter and more personalized travel planning.**
