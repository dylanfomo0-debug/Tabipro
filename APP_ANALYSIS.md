# Tabipro App Structure and Logic Analysis

## 1. Technology Stack
The app is built using the **Base44 platform**, which utilizes:
*   **Frontend**: React.js with Vite.
*   **Styling**: Tailwind CSS for responsive and modern UI.
*   **Database**: Base44's built-in **Entities** (Real-time NoSQL-like storage).
*   **AI**: Integrated LLM for logic generation and specialized **Agents** for chat.

## 2. Directory Structure (src/)
*   **`/pages`**: Contains the main views of the application.
    *   `Home.jsx`: Entry point, likely showing existing trips.
    *   `OnboardingQuiz.jsx`: The starting point for new users to input preferences.
    *   `TripDetail.jsx`: The core view displaying the generated itinerary.
    *   `Assistant.jsx`: Interface for the AI travel concierge.
*   **`/components`**: Reusable UI elements.
    *   `layout/AppNav.jsx`: Global navigation.
    *   `itinerary/ItineraryTimeline.jsx`: A specialized component to render the trip schedule.
    *   `itinerary/BlockDetailSheet.jsx`: A slide-over or modal for specific spot details.
    *   `agent/MessageBubble.jsx`: UI for the chat assistant.
*   **`/lib`**: Core business logic.
    *   `trip/generator.js`: The "brain" that calls the AI to transform quiz results into a structured itinerary.
*   **`/api` & `/hooks`**: Standard React patterns for data fetching and state management.

## 3. Core Logic Flow
1.  **Preference Capture**: The `OnboardingQuiz` collects data (budget, style, dates, interests).
2.  **AI Generation**: The `lib/trip` logic sends this data to the LLM. The AI returns a structured **JSON** containing a day-by-day plan.
3.  **Data Persistence**: This JSON is saved into the `Trip` entity. Curated spots are pulled from the `Place` entity.
4.  **Dynamic Rendering**: `TripDetail` reads the `Trip` record and maps the JSON data to the `ItineraryTimeline` component.
5.  **Concierge Support**: The `tabipro_guide` agent is configured with "Read" access to `Trip` and `Place` entities, allowing it to answer questions like "What's next on my plan?" or "Suggest a nearby cafe" based on the user's actual data.

## 4. Data Entities (Database Schema)
*   **Trip**: `id`, `userId`, `startDate`, `endDate`, `budget`, `preferences` (JSON), `itinerary` (JSON).
*   **Place**: `id`, `name`, `category`, `description`, `coordinates`, `priceLevel`, `tags`.
*   **User Profile**: `id`, `preferences`, `travelHistory`.

## 5. Implementation Roadmap

### Phase 2: Smart Layers (Current Priority)
*   **Weather Integration**: Add a weather banner to `TripDetail.jsx`. Use the LLM to check the forecast and suggest a "Rainy Day Swap" if necessary.
*   **Budget Tracker**: Implement a simple expense input in `BlockDetailSheet.jsx` and aggregate the total in the `Trip` entity.
*   **Outfit Suggestions**: Use the weather data to generate a "Daily Outfit Card" using the AI assistant.

### Phase 3: Learning & Identity
*   **Feedback Loop**: Create a `PostTripReview.jsx` page where users rate spots. Store these ratings in the `Rating` entity.
*   **Personalized Prompting**: Update `lib/trip/generator.js` to include past ratings in the AI prompt for subsequent trip generations.
*   **User Passport**: A profile view showing travel stats and collected "stamps" from visited places.

### Phase 4: Safety & Polish
*   **Emergency Card**: A static, high-accessibility component with local emergency numbers and the user's hotel address in Japanese.
*   **Live Map Layer**: Integrate `react-leaflet` in `TripDetail.jsx` to show all itinerary spots on a map.
*   **Solo-Traveler Safety**: Add AI-generated safety tips for specific areas in the `tabipro_guide` concierge.
