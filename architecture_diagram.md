# Architecture Diagram for Mood-Based Recommendation System

## High-Level Components

1. **User Interface (Frontend)**:
   - HTML templates (index.html)
   - CSS styling (style.css)
   - JavaScript for client-side interactions (e.g., capturing image from webcam)

2. **Flask Web Application (Backend)**:
   - Main app.py handling routes and logic
   - Routes:
     - `/` : Serves the main page
     - `/detect_mood` : Processes image to detect emotion
     - `/get_recommendations` : Fetches recommendations based on mood
     - `/chat` : Handles chatbot interactions

3. **Emotion Detection Module**:
   - emotion_detector.py
   - Uses pre-trained model (emotiondetector.h5 and emotiondetector.json)
   - Processes image input to predict emotion (happy, sad, angry, etc.)

4. **Recommendation Modules**:
   - song_recommender.py : Recommends songs based on mood
   - movie_recommender.py : Recommends movies based on mood
   - book_recommender.py : Recommends books based on mood
   - Uses mood keywords mapping for song recommendations

5. **Chatbot Module**:
   - chatbot.py : Processes chat messages and provides responses based on mood

6. **Data Storage**:
   - CSV files: songs.csv, movie.csv, books.csv
   - Models: emotiondetector.h5, emotiondetector.json

7. **Session Management**:
   - Stores current mood and confidence in Flask session

## Data Flow

1. User accesses the web app via browser.
2. User captures an image (e.g., via webcam) and sends it to `/detect_mood`.
3. Emotion Detector processes the image and returns detected emotion.
4. User requests recommendations via `/get_recommendations`, using the detected mood.
5. Recommenders query respective CSV data and return top recommendations.
6. User can interact with the chatbot via `/chat`, which uses mood context.

## Mermaid Diagram Code

```mermaid
graph TD
    A[User] --> B[Browser]
    B --> C[Flask App (app.py)]
    C --> D[Emotion Detector (emotion_detector.py)]
    D --> E[Pre-trained Model (emotiondetector.h5)]
    C --> F[Song Recommender (song_recommender.py)]
    C --> G[Movie Recommender (movie_recommender.py)]
    C --> H[Book Recommender (book_recommender.py)]
    F --> I[Songs Data (songs.csv)]
    G --> J[Movies Data (movie.csv)]
    H --> K[Books Data (books.csv)]
    C --> L[Chatbot (chatbot.py)]
    L --> M[Mood Context]
    C --> N[Session Storage]
    N --> O[Current Mood & Confidence]
```

## Steps to Create the Diagram

1. Use a diagramming tool like draw.io, Lucidchart, or Mermaid live editor.
2. Copy the Mermaid code above into the tool.
3. Customize colors, shapes, and labels as needed.
4. Export as PNG/PDF for documentation.
