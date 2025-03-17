# 🎤 Stand-Up Comedy Transcript Analysis

## 📌 Project Overview
This project analyzes **stand-up comedy transcripts** from 20 comedians, scraped from [Scraps from the Loft](https://scrapsfromtheloft.com/stand-up-comedy-transcripts/). The goal is to explore linguistic patterns, profanity usage, and unique words used by different comedians.

## 🛠 Features
- **Web Scraping**: Extracted transcripts using automated scripts.
- **Text Cleaning**: Removed special characters, punctuation, and stopwords using regular expressions.
- **One-Hot Encoding**: Converted words into binary matrices for analysis.
- **WordCloud Visualization**: Created word clouds to visualize word frequency.
- **Profanity Analysis**: Counted occurrences of explicit words (F-word, S-word, etc.).
- **CountVectorizer & Stop Words**: Extracted most frequent and unique words.
- **TF-IDF Analysis**: Identified words uniquely important to each comedian.
- **Data Storage**: Used Pickling to save processed data efficiently.

## 📂 Files & Structure
```
├── data/
│   ├── raw_transcripts.pkl
│   ├── cleaned_transcripts.csv
│   ├── profanity_counts.csv
│   ├── tfidf_results.csv
│
├── notebooks/
│   ├── analysis.ipynb   # Main analysis notebook
│
├── wordclouds/          # Folder containing word cloud images
│
├── scripts/
│   ├── scrape_transcripts.py  # Script for web scraping
│   ├── process_data.py        # Script for text preprocessing
│
├── README.md            # Project documentation
├── Codebook.md          # Detailed description of dataset & methodology
```

## 🚀 Installation & Setup
### 1️⃣ Clone the Repository
```sh
git clone https://github.com/yourusername/comedy-transcript-analysis.git
cd comedy-transcript-analysis
```

### 2️⃣ Install Dependencies
```sh
pip install -r requirements.txt
```

### 3️⃣ Run Jupyter Notebook
```sh
jupyter notebook notebooks/analysis.ipynb
```

## 📊 Results & Insights
- **Comedians have distinct vocabulary usage patterns.**
- **Profanity levels vary significantly across comedians.**
- **TF-IDF analysis reveals each comedian’s signature words.**
- **Stop words influence word frequency distributions.**

## 🔮 Future Improve
