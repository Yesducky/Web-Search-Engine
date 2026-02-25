# Web-Search-Engine

A full-stack web search engine built with Python and Flask. This system features a custom web crawler, an inverted indexer with Porter Stemming, and a ranked search engine based on the Vector Space Model (TF-IDF). It also includes an AI-powered chatbot integrated with the search index.

## Features

*   **Web Crawler**: Breadth-first search crawler that fetches pages within a specific domain. Includes real-time progress updates via Socket.IO.
*   **Indexing**: Robust text processing featuring tokenization, stopword removal, and Porter Stemming. Stores term positions and frequencies.
*   **Ranked Search**:
    *   Utilizes **TF-IDF** weighting and **Cosine Similarity**.
    *   **Title Bias**: Prioritizes matches found in page titles (3x weight).
    *   **Phrase Search**: Supports exact phrase matching using double quotes (e.g., `"CNN News"`).
*   **AI Chatbot**: Uses the DeepSeek API to interpret natural language questions, search the internal database for context, and answer queries using only indexed data.
*   **Get Similar Pages**: Recommends related documents by extracting keywords from a specific search result.
*   **Search History**: Client-side storage of recent unique queries.

## Tech Stack

*   **Backend**: Python 3.12.0, Flask, Flask-SocketIO
*   **Database**: SQLite with SQLAlchemy ORM
*   **NLP**: NLTK (Porter Stemmer), BeautifulSoup, Regular Expressions
*   **External API**: DeepSeek API (for Chatbot)

## Project Structure

*   `app.py`: Main Flask application, routes, and WebSocket logic.
*   `spider.py`: Web crawler implementation.
*   `indexer.py`: Text processing and database indexing.
*   `search.py`: Query parsing, scoring algorithms, and ranking logic.
*   `model.py`: SQLAlchemy database models (Page, InvertedIndex, DocumentStats).

## Installation

1.  **Clone the repository**
    ```bash
    git clone https://github.com/Yesducky/Web-Search-Engine.git
    ```

2.  **Create and Activate Virtual Environment**
    ```bash
    # Windows
    python -m venv venv
    venv\Scripts\activate
  
    # Linux/MacOS
    python -m venv venv
    source venv/bin/activate
    ```

3.  **Install Dependencies**
    ```bash
    pip install -r requirements.txt
    # Or use the setup script (Linux/Mac):
    # chmod +x setup.sh && ./setup.sh
    ```

4.  **Download NLTK Data**
    ```bash
    python -c "import nltk; nltk.download('punkt')"
    ```

5.  **Configuration**
    Ensure `stopwords.txt` exists in the project root directory.

6.  **Initialize Database**
    ```bash
    flask init-db
    ```

7.  **Run the Application**
    ```bash
    python app.py
    ```
    The web interface will be available at `http://localhost:5000`.

## Usage

### 1. Crawling
*   Navigate to the **Spider** tab.
*   Click **Start Crawl** to begin fetching and indexing pages from the configured seed URL.
*   Monitor the real-time log for crawled URLs and indexing status.

### 2. Searching
*   Use the **Search** bar to enter keywords.
*   Use quotes (e.g., `"artificial intelligence"`) for phrase searches.
*   Click the yellow **"Get Similar Pages"** button on any result to find related documents.

### 3. Chatbot
*   Go to the **Chat** tab.
*   Ask a natural language question. The system will extract keywords, search the index, and generate an answer based on the retrieved content.

## Screenshots

### User Interface & Crawling
<img width="2048" height="1280" alt="image" src="https://github.com/user-attachments/assets/eeb254b5-cca2-4a2d-b717-00e6c43c7e85" />
*Spider page initialization.*

<img width="2048" height="1280" alt="image" src="https://github.com/user-attachments/assets/6df9aefe-082a-4e73-9408-5f6ee7dd5759" />
*Crawling progress updated via SocketIO (approx. 50 seconds for 297 pages).*

### Database & Indexing
<img width="2048" height="946" alt="image" src="https://github.com/user-attachments/assets/c9599e54-7882-4f6c-83e5-ebc292e19652" />
*View of the database after indexing.*


### Search Results
<img width="2048" height="1280" alt="image" src="https://github.com/user-attachments/assets/b29a31f5-1674-4b5b-bd67-3b00a3d63cea" />
*Ranked results showing title matches with higher scores.*

<img width="2048" height="1280" alt="image" src="https://github.com/user-attachments/assets/c98991bd-bb6d-4b0f-857e-0ae809405581" />
*Exact phrase matching using double quotes.*

<img width="2048" height="1280" alt="image" src="https://github.com/user-attachments/assets/cfc78a88-5039-4d39-8c3a-549a9a3d8e4d" />
*Results found using the "Get Similar Pages" feature based on top keywords.*

<img width="2048" height="1280" alt="image" src="https://github.com/user-attachments/assets/e985e263-9252-4d33-b25c-cc2120fa6fe0" />
*Search engine handling complex queries from document content.*

### Bonus Features
<img width="1482" height="1390" alt="image" src="https://github.com/user-attachments/assets/b12b80eb-5add-428a-970b-09e36feb4238" />
*Chatbot interface responding to user inquiries using indexed context.*

### Demo
https://www.youtube.com/watch?v=ZAYu4pSWqa4

This project is part of the COMP4321 Course Project.
