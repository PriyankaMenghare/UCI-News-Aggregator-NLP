# UCI News Aggregator — LDA Topic Modeling & NLP 📰🔍

An NLP pipeline on the UCI News Aggregator dataset performing EDA, text 
preprocessing, LDA topic modeling on news titles, coherence score evaluation, 
word cloud visualization, and spaCy dependency parsing.

---

## 🧩 Problem Statement

1. Perform EDA and necessary preprocessing on the dataset
2. Use LDA algorithm to create minimum 10 topics from the `TITLE` column
3. Compute coherence score and print extracted topics
4. Visualize topics using word clouds
5. Plot dependency parser for two random sentences (≥10 words) from the corpus

---

## 📦 Dataset

- **File:** `uci-news-aggregator.csv`
- **Rows used:** First 5,000 records
- **Columns:** ID, TITLE, URL, PUBLISHER, CATEGORY, STORY, HOSTNAME, TIMESTAMP
- **Target column:** `TITLE` (used for topic modeling)
- **Missing values:** 1 missing value in `PUBLISHER` column only

### Category Distribution
| Category | Description |
|----------|-------------|
| e | Entertainment |
| b | Business |
| t | Technology |
| m | Medical/Health |

- Total unique publishers: **1,733**
- Total unique categories: **4**
- Total unique stories: **67**

---

## 🔬 Methodology

### 1. EDA
- Dataset shape, dtypes, info
- Missing value check
- Category distribution bar chart

### 2. Text Preprocessing (on `TITLE` column)
| Step | Action |
|------|--------|
| Lowercasing | `.lower()` |
| Punctuation removal | `str.maketrans` |
| Tokenization | NLTK `word_tokenize` |
| Stop words removal | NLTK English stopwords |
| Short word removal | Words with length ≤ 2 removed |

> Note: Stemming/Lemmatization not applied — tokens fed directly to LDA.

### 3. LDA Topic Modeling
- **Library:** Gensim `LdaModel`
- **Topics:** 10
- **Passes:** 15
- **Dictionary & Corpus:** Built from preprocessed titles using `corpora.Dictionary`

### 4. Extracted Topics

| Topic | Top Keywords |
|-------|-------------|
| 0 | bachelor, juan, pablo, season, bieber, justin, finale, selena, galavis, gomez |
| 1 | snowden, sxsw, bank, england, carney, edward, parents, apple, says, ios |
| 2 | lindsay, market, chiquita, penney, loss, swift, news, taylor, outfitters, inc |
| 3 | american, missing, eagle, ukraine, search, night, house, ... |
| 4 | miley, cyrus, ... |
| 5–9 | (various entertainment, business, tech, health topics) |

### 5. Coherence Score
```
Coherence Score (c_v): 0.4530
```
> A score of ~0.45 indicates moderate topic coherence — topics are reasonably 
> interpretable with distinct themes.

### 6. Topic Visualization
- **Word clouds** generated for each of the 10 topics
- Each cloud sized 800×800 with white background
- Word size proportional to topic weight

### 7. Dependency Parsing
- **Library:** spaCy (`en_core_web_sm`)
- **Method:** `displacy.render()` with `style='dep'`
- Two random sentences with ≥10 words selected from `TITLE` column
- Rendered inline in Jupyter with distance=120, color=blue, compact=True

---

## 🛠️ Setup & Usage

### Prerequisites
- Python 3.8+
- Jupyter Notebook / Google Colab

### Install Dependencies
```bash
pip install pandas matplotlib nltk gensim wordcloud spacy
python -m spacy download en_core_web_sm
```

### Download NLTK Resources
```python
import nltk
nltk.download('punkt')
nltk.download('stopwords')
```

### Run
```bash
jupyter notebook UCI_NEWS_AGGREGATOR.ipynb
```

---

## 📁 File Structure

```
UCI-News-Aggregator-LDA-Topic-Modeling/
├── UCI_NEWS_AGGREGATOR.ipynb      # Main notebook
├── uci-news-aggregator.csv        # UCI News dataset
└── README.md
```

---

## 📝 License

MIT License — for academic use.
