---
title: "📚 Codebook: Stand-up Comedy Transcript Analysis"
author: "Yajur Chaudhary"
date: "``"
output: html_document
---

# 1⃣ Dataset Overview  
This dataset consists of **transcripts from 20 stand-up comedians**, scraped from [Scraps from the Loft](https://scrapsfromtheloft.com/stand-up-comedy-transcripts/). It is used to analyze vocabulary, common words, and profanity usage across different comedians. The analysis focuses on text-based insights rather than tone, delivery, or sentiment.

# 2⃣ Data Collection  
- **Source**: Transcripts were collected from "Scraps from the Loft," a website that provides scripts of various stand-up comedy performances.
- **Method**: Web scraping was used to extract text from comedian-specific pages.
- **Preprocessing**: The raw text was stored and cleaned before analysis.

# 3⃣ Variables & Features  

## 🔹 Raw Data Variables  
- **comedian_name** – Name of the stand-up comedian.  
- **transcript** – Full text of their stand-up routine.  

## 🔹 Processed Data Variables  
- **cleaned_transcript** – Text after removing special characters and extra spaces.  
- **word_count** – Total number of words in the transcript.  
- **unique_words** – Number of unique words used.  
- **f_word_count** – Number of times the comedian used the **F-word**.  
- **s_word_count** – Number of times the comedian used the **S-word**.  
- **one_hot_encoding** – A binary matrix representing the presence of words in the transcript.  
- **most_common_words** – List of most frequently used words by the comedian.  
- **unique_words_per_comedian** – Words that appear frequently for one comedian but rarely for others.  
- **stop_words_removed** – Processed text with common stop words filtered out.

# 4⃣ Data Cleaning & Processing  
- **Regular Expressions** were used to remove unwanted characters, punctuation, and extra spaces.  
- **One-Hot Encoding** was applied to convert words into binary format for analysis.  
- **WordCloud** was generated to visualize frequently used words.  
- **Stop Words Removal** was performed to filter out common words like *the, is, and*.  
- **Profanity Analysis** counted the occurrences of specific swear words.  
- **Pickling** was used to **store and reload processed data efficiently**.  
- **CountVectorizer** was used to extract word frequency counts and analyze trends in word usage.  
- **TF-IDF Analysis** was used to identify important words specific to each comedian.

# 5⃣ Analysis Methods  
- **Word Frequency Analysis** to find the most used words by each comedian.  
- **WordCloud Visualization** for an overview of the comedian’s vocabulary.  
- **Profanity Analysis** to determine how frequently each comedian uses explicit words.  
- **Comparison Across Comedians** to identify stylistic and linguistic patterns.  
- **Unique Word Analysis** to detect words that define each comedian's style.  
- **TF-IDF Analysis** to highlight words uniquely important to each comedian.  

# 6⃣ Output Files  
- **cleaned_transcripts.csv** – Preprocessed transcripts after cleaning.  
- **wordclouds/** – Folder containing WordCloud images for each comedian.  
- **profanity_counts.csv** – A CSV file with the count of explicit words for each comedian.  
- **final_analysis.csv** – Processed dataset with all extracted features.  
- **pickled_data.pkl** – **Pickled Python object storing processed data for faster loading.**  
- **tfidf_results.csv** – TF-IDF scores for words across different comedians.  

# 7⃣ Pickling and Data Storage  
Pickling is used to save intermediate and final processed datasets. This allows quick reloading of the data without re-running the cleaning and preprocessing steps. The `pickle` module in Python was used to serialize data structures such as Pandas DataFrames.  

## Pickled Files  
- **raw_transcripts.pkl**: Stores raw scraped transcripts.  
- **cleaned_transcripts.pkl**: Contains cleaned transcript text.  
- **word_frequencies.pkl**: Saves word count matrices and analysis results.  
- **tfidf_data.pkl**: Stores TF-IDF matrices for word importance analysis.  

# 8⃣ Notes & Considerations  
- This analysis focuses only on text processing and does not account for **speech tone or delivery style**.  
- Stop words removal affects word frequency counts, so some common words are excluded.  
- The dataset is limited to publicly available transcripts, so coverage may vary.  
- **Pickling helps save time** by avoiding redundant data processing when reloading datasets.  
- **Data privacy**: This project only analyzes publicly available transcripts and does not contain sensitive or private data.  

# 9⃣ Future Enhancements  
- Sentiment analysis of transcripts to detect tone and audience reactions.  
- Named entity recognition (NER) to identify commonly mentioned people, places, or topics.  
- Topic modeling to categorize jokes into themes.  
- Additional profanity filtering with a broader word list.  
- Deep learning-based text generation models to identify stylistic patterns.  
