# 🎬 Movie Recommendation System

> **Data Mining — Semester 2 Project**
> A movie recommendation system built using **Collaborative Filtering** (Item-Item Cosine Similarity) and **Content-Based Filtering**, implemented in Python on the Kaggle MovieLens dataset.

---

## 📌 About the Project

This project implements two approaches to recommend movies to users:

- **Collaborative Filtering** — Recommends movies based on patterns in user ratings using Item-Item Cosine Similarity
- **Content-Based Filtering** — Recommends movies based on genre attributes and a user's rating profile (demonstrated via `Content_Aware.xlsx`)

---

## 🎯 Objective

To build a working movie recommendation engine that:
- Filters active users (50+ ratings) and popular movies (top 1500)
- Builds a User-Item matrix from millions of ratings
- Computes cosine similarity between movies
- Returns personalised movie recommendations for any input movie(s)

---

## 🗂️ File Structure

```
movie-recommendation-system-python/
│
├── Recommendation_System_-_Collaborative_filtering_Final.ipynb  # 🔑 Main notebook
├── Content_Aware.xlsx        # Content-based filtering demo (manual calculation)
├── links.csv                 # Maps movieId ↔ tmdbId ↔ imdbId
├── movies_metadata.csv       # ⚠️ NOT included (33MB) — download from Kaggle
└── ratings.csv               # ⚠️ NOT included (500MB+) — download from Kaggle
```

---

## 📥 Dataset

The dataset is sourced from **Kaggle — MovieLens Dataset**:
🔗 [https://www.kaggle.com/code/ibtesama/getting-started-with-a-movie-recommendation-system](https://www.kaggle.com/code/ibtesama/getting-started-with-a-movie-recommendation-system)

Download and place the following files in the project folder before running:
- `movies_metadata.csv` — Movie details dataset (~33MB)
- `ratings.csv` — User movie ratings (27M+ rows, ~500MB)

Only `links.csv` is already included in this repository (it's under 1MB).

---

## 🛠️ Tools & Technologies

- **Language:** Python 3.8+
- **Libraries:** `pandas`, `scikit-learn`
- **Algorithm:** Item-Item Cosine Similarity
- **Environment:** Jupyter Notebook

---

## ⚙️ How It Works

### Step 1 — Load & Preprocess Data
- Load `movies_metadata.csv` and `ratings.csv`
- Convert `id` column in metadata to integer
- Merge datasets using `links.csv` (maps tmdbId → movieId)

### Step 2 — Filter Data
- Keep only **active users** (users with more than 50 ratings)
- Keep only **top 1500 most-rated movies**

### Step 3 — Build User-Item Matrix
- Create a pivot table: rows = users, columns = movies, values = ratings

### Step 4 — Compute Cosine Similarity
- Fill NaN values with 0
- Compute cosine similarity across all movie vectors using `sklearn`

### Step 5 — Generate Recommendations
- Input one or more movie names (partial names supported)
- Returns top N most similar movies based on averaged similarity scores

---

## ▶️ How to Run

**1. Install dependencies:**
```bash
pip install pandas scikit-learn jupyter
```

**2. Clone this repository:**
```bash
git clone https://github.com/YOUR_USERNAME/movie-recommendation-system-python.git
cd movie-recommendation-system-python
```

**3. Download both large files from Kaggle** and place them in the project folder:
- `movies_metadata.csv`
- `ratings.csv`

**4. Open the main notebook:**
```bash
jupyter notebook "Recommendation_System_-_Collaborative_filtering_Final.ipynb"
```

**5. Run all cells in order.**

---

## 🎯 Sample Output

```python
recommend(["toy", "mission"], n=10)
```

```
Recommended movies:

1. Toy Story 2
2. A Bug's Life
3. Monsters, Inc.
4. The Incredibles
5. Mission: Impossible II
6. Saving Private Ryan
7. Gladiator
8. The Matrix
9. Forrest Gump
10. Schindler's List
```

---

## 📊 Content-Based Filtering (Content_Aware.xlsx)

The Excel file demonstrates a manual content-based filtering calculation:

- Movies are represented as genre vectors (Adventure, Super Hero, Comedy, Sci-Fi)
- A user profile is built from their rated movies
- Genre weights are calculated and used to predict ratings for unseen movies

| Movie | Predicted Rating |
|---|---|
| Hitchhiker's Guide to Galaxy | 6.67 |
| Spiderman | 6.33 |
| Batman Begins | 3.33 |

---

## 🚀 Possible Extensions

- Add SVD / Matrix Factorisation for better accuracy
- Build a Flask/Streamlit web app for live recommendations
- Combine collaborative + content-based (Hybrid Filtering)
- Use deep learning embeddings for richer representations

---

*Submitted as part of the Data Mining course —  PG Programme*
