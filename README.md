# GenAI Log Analyzer

This project is a **GenAI-powered Log Analyzer** 🐛, designed to help developers and SREs efficiently diagnose bugs by analyzing error logs with a large language model. It also matches new logs against a database of historical logs to identify how much a particular log is similar to another log.

---

### ✨ Features

* **GenAI Bug Prediction**: Uses the Generative AI API to analyze log content and predict potential bugs.
* **Similarity Matching**: Finds and displays the top 5 most similar historical logs to aid in finding known solutions.
* **Secure & Role-Based Access**: Includes user registration, login, and an admin dashboard.
* **Personal and Global History**: Users can view their own log history, and admins can view all submitted logs.

---

### 🚀 Getting Started

To get a local copy up and running, follow these simple steps.

#### *Prerequisites*

* Python 3.9+
* pip
* sqlite3
* spacy

#### *Installation*

1.  **Install dependencies** from the `requirements.txt` file.
    ```sh
    pip install -r requirements.txt
    ```

2.  **Download the SpaCy model**. The NLP engine requires a pre-trained model to function.
    ```sh
    python -m spacy download en_core_web_sm
    ```

3.  **Configure environment variables** by creating a `.env` file in the root directory. This file is crucial for API keys and application configuration.
    ```
    # GenAI API credentials
    AZURE_OPENAI_API_KEY="YOUR_API_KEY"
    AZURE_OPENAI_ENDPOINT="YOUR_API_ENDPOINT"

    # Flask API URL for the frontend to connect to
    FLASK_API_URL="[http://127.0.0.1:5000](http://127.0.0.1:5000)"

    # Flask Secret Key for session security. This must be a long, random string.
    FLASK_SECRET_KEY="a_long_and_random_string_of_characters"
    ```

---

### ▶️ Usage

The application consists of two main parts: the backend API (`api.py`) and the frontend web app (`app.py`).

1.  **Start the Flask backend:**
    ```sh
    set FLASK_APP=backend.api
    flask run
    ```
    (Note: On macOS/Linux, use `export FLASK_APP=backend.api`)

2.  **Start the Streamlit frontend:**
    ```sh
    streamlit run app.py
    ```

3.  **Analyze a log from the terminal:**
    Use the `upload_log.py` utility script to upload a log file directly from your terminal and get a link to the analysis report.

    ```sh
    python backend/upload_log.py <path_to_log_file> <username> <password> --description "A brief summary of the error." --team "Team Name"
    ```

---

### 🛠️ Utilities

* **Promote a User**: Use the `promote_user.py` script to grant a user admin privileges.
    ```sh
    python promote_user.py <username>
    ```

* **Database**: The project uses an SQLite database named `logs.db`.

---
