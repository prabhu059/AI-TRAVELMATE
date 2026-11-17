# ✈️ AI TravelMate

An AI-powered travel planning web app built with Python and Streamlit. Enter your route, dates, travel style, and budget, and AI TravelMate generates a complete trip plan: cheapest flights, hotel and restaurant suggestions, a day-by-day itinerary, and a weather forecast for your travel dates.

> **Live demo:** [add your Streamlit Cloud link here]

## Screenshots

<!-- Add 2-3 screenshots here, for example: -->
<!-- ![Flights tab](screenshots/flights.png) -->
<!-- ![Itinerary tab](screenshots/itinerary.png) -->

## Features

- **Flights:** Shows the 3 cheapest flight options (airline, price in INR, timings, duration) using Google Flights data through SerpAPI.
- **Stays & Eats:** Suggests 3 hotels and 3 restaurants based on your travel theme, budget, and preferred hotel rating. Each card shows an image, address, and website link.
- **Itinerary:** Generates a day-by-day plan with morning, afternoon, and evening activities, with a photo and link for each place.
- **Weather:** Shows the forecast for your trip dates (temperature, precipitation, wind), and falls back to current weather if a forecast is not available.
- **Personalization:** Choose a travel theme (couple, family, adventure, solo), a budget level (economy, standard, luxury), and your own activity interests.

## Tech Stack

| Area | Technology |
|---|---|
| Language | Python |
| Web app | Streamlit |
| LLM | Groq API (Llama 3.3 70B Versatile) |
| Search data | SerpAPI (Google Flights, Google Images, Google Local, Google search) |

## How It Works

1. The user enters departure and destination airport codes (IATA, e.g. `BOM`, `DEL`), travel dates, theme, budget, and interests in the sidebar.
2. **SerpAPI** fetches live flight results and the destination city name.
3. The **Groq LLM** researches the destination, then generates hotel and restaurant recommendations and a day-by-day itinerary as structured JSON.
4. The app parses the JSON and uses **SerpAPI** to add images, addresses, websites, and weather data.
5. Results are shown in four tabs: Flights, Stays & Eats, Itinerary, and Weather.

**Reliability:** API calls to the LLM retry automatically when the rate limit is hit, and the JSON parser handles responses wrapped in code blocks or extra text.

## Getting Started

### Prerequisites

- Python 3.9 or higher
- A [SerpAPI](https://serpapi.com/) API key
- A [Groq](https://console.groq.com/) API key

### Installation

```bash
git clone https://github.com/prabhu059/ai-travelmate.git
cd ai-travelmate
pip install -r requirements.txt
```

### Add your API keys

Create a file at `.streamlit/secrets.toml` in the project folder:

```toml
SERPAPI_KEY = "your-serpapi-key"
GROQ_API_KEY = "your-groq-key"
```

Never commit this file. It is listed in `.gitignore`.

### Run the app

```bash
streamlit run finalproject.py
```

The app opens at `http://localhost:8501`.

## Project Structure

```
ai-travelmate/
├── finalproject.py      # Streamlit app (UI, API calls, parsing)
├── requirements.txt     # Python dependencies
├── .gitignore           # Keeps secrets out of Git
└── README.md
```

## Limitations

- Flight data is live from SerpAPI, but hotel and restaurant names, ratings, and descriptions are AI-generated. Check details before booking.
- Departure and destination must be entered as IATA airport codes.
- Free API plans have usage limits, so many searches in a short time may be slow or fail.

## Future Improvements

- Accept city names instead of IATA codes
- Add live hotel prices and booking links
- Add an events section for the destination
- Let users download the itinerary as a PDF

## Author

**Tanimki Prabhudas**
[LinkedIn](https://linkedin.com/in/prabhudas-tanimki) · [GitHub](https://github.com/prabhu059) · prabhudastanimki@gmail.com
