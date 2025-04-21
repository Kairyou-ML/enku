# Enku Vocabulary Trainer

## Overview

**Enku Vocabulary Trainer** is a web-based application designed to help users learn and memorize vocabulary effectively. Built using **Streamlit**, the app allows users to practice vocabulary through a quiz format, with support for uploading custom CSV files containing word lists. It tracks progress, provides hints, and uses a spaced repetition algorithm to reinforce learning.  
The application is containerized using **Docker**, making it easy to deploy and run in various environments.

## Features

- **Interactive Quiz**: Users are presented with a word and must select the correct meaning from multiple-choice options.
- **Custom Wordlists**: Supports uploading CSV files with columns for words and their meanings (e.g., English and Vietnamese).
- **Spaced Repetition**: Words are reintroduced based on the user's performance, with a focus on those answered incorrectly.
- **Progress Tracking**: Tracks the number of words learned and saves progress to a pickle file (`output.pkl`).
- **Hints**: Users can add custom hints for words after incorrect answers to aid memorization.
- **Docker Support**: The app is packaged in a Docker container for easy setup and deployment.

## Project Structure

```
enku-vocab-trainer/
├── app.py                  # Main Streamlit application
├── data/                   # Directory for input/output files
│   ├── input.csv           # Sample CSV file with wordlist (English, Vietnamese)
│   └── output.pkl          # File to store user progress (generated at runtime)
├── requirements.txt        # Python dependencies
├── Dockerfile              # Docker configuration for containerizing the app
└── README.md               # Project documentation
```

## Prerequisites

- **Docker**: Required to build and run the application in a container.
- **Python 3.9+ (optional)**: Only needed if running the app locally without Docker.
- A CSV file with at least two columns (e.g., English and Vietnamese) for the wordlist.

## Installation and Setup

### Using Docker

1. Clone the repository:

```bash
git clone <repository-url>
cd enku-vocab-trainer
```

2. Build the Docker image:

```bash
docker build -t enku-vocab-trainer .
```

3. Run the Docker container:

```bash
docker run -p 8501:8501 -v $(pwd)/data:/app/data enku-vocab-trainer
```

4. Access the app:  
Open a browser and navigate to [http://localhost:8501](http://localhost:8501).

---

### Without Docker (Local Setup)

1. Clone the repository:

```bash
git clone <repository-url>
cd enku-vocab-trainer
```

2. Install dependencies:

```bash
pip install -r requirements.txt
```

3. Run the Streamlit app:

```bash
streamlit run app.py
```

4. Access the app:  
Open a browser and navigate to [http://localhost:8501](http://localhost:8501).

---

## Usage

### Upload a CSV file (optional)

- The CSV should have at least two columns: one for the word (e.g., English) and one for its meaning (e.g., Vietnamese).
- Example format:

```
English,Vietnamese
apple,táo
book,sách
```

### Take the quiz

- The app displays a word and four answer options.
- Select the correct meaning and submit your answer.
- If incorrect, you can add a hint to help remember the word.

### Track progress

- The progress bar shows how many words you've mastered (correctly answered twice).
- Progress is saved to `data/output.pkl`.

### Reset progress

- Use the "Reset Progress" button to clear saved progress and start over.

---

## Notes

- **Data Persistence**:  
  When using Docker, mount the `data/` directory as a volume to persist `output.pkl` between container runs:
  
  ```bash
  docker run -p 8501:8501 -v $(pwd)/data:/app/data enku-vocab-trainer
  ```

- **File Permissions**:  
  Ensure the `data/` directory has write permissions for saving `output.pkl`.

- **Custom CSV**:  
  If no CSV is uploaded, the app expects `data/input.csv` to exist.

---

## Troubleshooting

- **Error: `input.csv` not found**:  
  Ensure `data/input.csv` exists or upload a valid CSV file via the app.

- **App not loading at `localhost:8501`**:  
  Verify the Docker container is running (`docker ps`) and port `8501` is not in use.

- **Progress not saving**:  
  Check if the `data/` directory is writable.  
  Add `chmod -R 777 data` in the Dockerfile if needed.

---

## Future Improvements

- Add support for multiple languages and word categories.
- Implement user authentication for personalized progress tracking.
- Enhance UI with additional features like word pronunciation or example sentences.
- Optimize the spaced repetition algorithm for better learning efficiency.

---

## License

This project is licensed under the MIT License. See the `LICENSE` file for details.

---

## Contact

For questions or feedback, please contact the project maintainer at **[smashizulegend@gmail.com]** or **[anhlq.23bi14025@usth.com]** .
