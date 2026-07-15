# Tabipro: AI-Powered Tokyo Travel Companion

Tabipro is a smart travel application designed to help students and young travelers explore Tokyo with ease. By leveraging AI, the app creates personalized itineraries, manages budgets, and provides real-time concierge support.

## 🚀 Overview

The application is built on the **Base44 platform**, utilizing a React-based frontend and an AI-driven backend logic. It focuses on a "mobile-first" experience, providing a seamless transition from preference gathering to a fully realized travel plan.

## 🏗️ App Structure

The project follows a modular architecture:

| Directory | Description |
| :--- | :--- |
| `src/pages` | Core views: `Home`, `OnboardingQuiz`, `TripDetail`, and `Assistant`. |
| `src/components` | Reusable UI: `ItineraryTimeline`, `BlockDetailSheet`, and `MessageBubble`. |
| `src/lib` | Business logic: `trip/generator.js` (AI itinerary engine). |
| `src/api` | Data fetching and real-time synchronization with Base44 entities. |

## 🧠 Core Logic

1.  **Onboarding Quiz**: Collects user preferences such as budget, travel style, and dates.
2.  **AI Itinerary Engine**: An LLM processes the quiz results and generates a structured JSON itinerary.
3.  **Data Persistence**: The itinerary and curated spots are stored in real-time `Trip` and `Place` entities.
4.  **AI Concierge**: The `tabipro_guide` agent provides contextual support based on the user's saved data.

## 📅 Roadmap

### Phase 2: Smart Layers
- **Weather Integration**: Dynamic rainy-day swaps and outfit suggestions.
- **Budget Tracker**: Real-time expense monitoring within the itinerary.

### Phase 3: Learning & Identity
- **Feedback Loop**: User ratings to influence future AI generations.
- **Travel Passport**: A gamified profile view showing travel history and stamps.

### Phase 4: Safety & Polish
- **Emergency Card**: High-accessibility local emergency info in Japanese.
- **Live Map**: Interactive map view of all itinerary locations.

---

*This repository contains the documentation and architectural analysis of the Tabipro project. For the live editor environment, visit the [Base44 Project Link](https://app.base44.com/apps/6a56e1b7e44e84a7969c758d/editor/workspace/overview).*
