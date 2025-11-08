# Methodology Flow Diagram for Mood-Based Recommendation System

This diagram illustrates the step-by-step process (methodology) of how the Mood-Based Recommendation System operates, from user interaction to generating personalized recommendations.

```mermaid
flowchart TD
    A[User accesses the web application<br/>via index.html] --> B[User captures or uploads an image<br/>of their facial expression]
    B --> C[Image data sent to /detect_mood endpoint<br/>via POST request]
    C --> D[EmotionDetector processes the image<br/>using pre-trained model<br/>models/emotiondetector.h5]
    D --> E{Emotion detected?<br/>e.g., happy, sad, angry, etc.}
    E -->|Yes| F[Store detected mood and confidence<br/>in user session]
    E -->|No| G[Return error message<br/>to user]
    F --> H[User requests recommendations<br/>or chatbot interaction]
    H --> I{Request type?}
    I -->|Get Recommendations| J[Call /get_recommendations endpoint<br/>with detected mood]
    I -->|Chat Message| K[Call /chat endpoint<br/>with user message and mood]
    J --> L[SongRecommender generates<br/>top 10 songs for mood<br/>from data/songs.csv]
    J --> M[MovieRecommender generates<br/>top 5 movies for mood<br/>from data/movie.csv]
    J --> N[BookRecommender generates<br/>top 5 books for mood<br/>from data/books.csv]
    L --> O[Compile and return<br/>JSON response with<br/>songs, movies, books]
    M --> O
    N --> O
    O --> P[Display recommendations<br/>on user interface]
    K --> Q[Chatbot processes message<br/>using process_chat_message<br/>with mood context]
    Q --> R[Chatbot may query recommenders<br/>for additional suggestions<br/>if needed]
    R --> S[Generate and return<br/>chat response<br/>as JSON]
    S --> T[Display chat response<br/>on user interface]
    P --> U[End - User can<br/>interact further<br/>or restart]
    T --> U
    G --> U
