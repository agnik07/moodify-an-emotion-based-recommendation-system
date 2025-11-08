# Methodology Flow Diagram for Mood-Based Recommendation System

## Overview
This diagram illustrates the step-by-step methodology or workflow of the mood-based recommendation system, from user interaction to recommendation delivery.

## Key Steps in the Methodology

1. **User Access**: User opens the web application in a browser.
2. **Image Capture**: User captures an image (e.g., facial expression) via webcam or upload.
3. **Emotion Detection**: Image is sent to the backend for emotion analysis using a pre-trained model.
4. **Mood Storage**: Detected emotion and confidence are stored in the session.
5. **Recommendation Request**: User requests recommendations based on the detected mood.
6. **Data Query**: Recommenders query respective datasets (songs, movies, books) using mood keywords or mappings.
7. **Response Generation**: Recommendations are compiled and sent back to the user.
8. **Chat Interaction** (Optional): User can interact with the chatbot, which uses mood context for responses.

## Mermaid Flowchart Code

```mermaid
flowchart TD
    A[User Opens Web App] --> B[Load Main Page]
    B --> C[User Captures Image]
    C --> D[Send Image to /detect_mood Endpoint]
    D --> E[Emotion Detector Processes Image]
    E --> F[Detect Emotion & Confidence]
    F --> G[Store Mood in Session]
    G --> H[User Requests Recommendations]
    H --> I[Send Mood to /get_recommendations Endpoint]
    I --> J[Query Song Recommender]
    I --> K[Query Movie Recommender]
    I --> L[Query Book Recommender]
    J --> M[Fetch Top Songs]
    K --> N[Fetch Top Movies]
    L --> O[Fetch Top Books]
    M --> P[Compile Recommendations]
    N --> P
    O --> P
    P --> Q[Return Recommendations to User]
    Q --> R[User Interacts with Chatbot]
    R --> S[Send Message to /chat Endpoint]
    S --> T[Chatbot Processes Message with Mood Context]
    T --> U[Generate Response]
    U --> V[Return Chat Response to User]
```

## Steps to Create the Diagram

1. Use a diagramming tool like draw.io, Lucidchart, or Mermaid live editor.
2. Copy the Mermaid code above into the tool.
3. Adjust the layout, colors, and labels for clarity.
4. Export as PNG/PDF for documentation.
