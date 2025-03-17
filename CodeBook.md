# 📖 Codebook: Stand-up Comedy Transcript Analysis  

## 1️⃣ Dataset Overview  
This dataset consists of **transcripts from 20 stand-up comedians**, scraped from [Scraps from the Loft](https://scrapsfromtheloft.com/stand-up-comedy-transcripts/). It is used to analyze vocabulary, common words, and profanity usage across different comedians.  

## 2️⃣ Variables & Features  

### **🔹 Raw Data Variables**
- **comedians** – Name of the stand-up comedian.  
- **transcript** – Full text of their stand-up routine. 
- **transcripts** – Dictionary Containing Transcript of all Comics(keys).    

### **🔹 Processed Data Variables**  
- **cleaned_transcript** – Text after removing special characters and extra spaces.  
- **word_count** – Total number of words in the transcript.  
- **unique_words** – Number of unique words used.  
- **f_word_count** – Number of times the comedian used the **F-word**.  
- **s_word_count** – Number of times the comedian used the **S-word**.  
- **one_hot_encoding** – A binary matrix representing the presence of words in the transcript.  
- **Pickling** was used to **store and reload processed data efficiently**.
- 
---

## 3️⃣ Data Cleaning & Processing  
- **Regular Expressions** were used to remove unwanted characters, punctuation, and extra spaces.  
- **One-Hot Encoding** was applied to convert words into binary format for analysis.  
- **WordCloud** was generated to visualize frequently used words.  
- **Stop Words Removal** was performed to filter out common words like *the, is, and*.  
- **Profanity Analysis** counted the occurrences of specific swear words.  

---

## 4️⃣ Analysis Methods  
- **Word Frequency Analysis** to find the most used words by each comedian.  
- **WordCloud Visualization** for an overview of the comedian’s vocabulary.  
- **Profanity Analysis** to determine how frequently each comedian uses explicit words.  

---

## 5️⃣ Output Files  
- **corpus.pkl** – Preprocessed transcripts after cleaning.
- **dtm.stop.pkl** – Preprocessed transcripts after removing stopwords.  
- **wordclouds/** – Folder containing WordCloud images for each comedian.  
- **profanity_counts.csv** – A CSV file with the count of explicit words for each comedian.  
- **final_analysis.csv** – Processed dataset with all extracted features.  

---

## 📌 Notes  
- This analysis focuses only on text processing and does not account for **speech tone or delivery style**.  
- Stop words removal affects word frequency counts, so some common words are excluded.  
- The dataset is limited to publicly available transcripts, so coverage may vary.  

