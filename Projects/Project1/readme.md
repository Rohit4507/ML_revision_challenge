# 📰 News Text Classification App

A simple machine learning web app that classifies news headlines or short
descriptions into one of four categories — **World**, **Sports**, **Business**,
or **Sci/Tech** — using a Multinomial Naive Bayes model trained on the
[AG News Classification Dataset](https://www.kaggle.com/datasets/amananandrai/ag-news-classification-dataset).

Built with **scikit-learn** for the model and **Streamlit** for the interactive
web interface.

## 🚀 Demo

Once deployed, add your live Streamlit Cloud link here:

`https://<your-app-name>.streamlit.app`

## 🧠 How It Works

1. The AG News dataset (`train.csv`) is loaded and split into training (80%)
   and testing (20%) sets.
2. Text is converted into numerical features using `CountVectorizer`
   (bag-of-words).
3. A `MultinomialNB` (Naive Bayes) classifier is trained on the vectorized
   text.
4. The trained model and vectorizer are cached (`@st.cache_resource`) so
   training only happens once when the app starts.
5. Users type in a headline or description, and the app predicts the most
   likely news category along with the model's confidence for each class.

## 📁 Project Structure

```
text-classification-app/
├── app.py                  # Streamlit application
├── requirements.txt        # Python dependencies
├── data/
│   ├── train.csv           # AG News dataset (add this yourself, see below)
│   └── README.md           # Instructions for the dataset file
├── text-classification.ipynb  # Original notebook (EDA + model prototyping)
└── README.md
```

## 🗂️ Dataset

This project uses the **AG News Classification Dataset**, which contains
news articles labeled into 4 classes:

| Class Index | Category |
|-------------|----------|
| 1           | World    |
| 2           | Sports   |
| 3           | Business |
| 4           | Sci/Tech |

Download the dataset from Kaggle and place `train.csv` inside the `data/`
folder:

🔗 https://www.kaggle.com/datasets/amananandrai/ag-news-classification-dataset

> The raw CSV isn't included in this repo due to its size. Kaggle datasets
> can be downloaded directly, or via the `kagglehub` / `kaggle` CLI.

## 💻 Running Locally

1. Clone this repository:
   ```bash
   git clone https://github.com/<your-username>/<your-repo>.git
   cd <your-repo>
   ```

2. Create a virtual environment (optional but recommended):
   ```bash
   python -m venv venv
   source venv/bin/activate   # on Windows: venv\Scripts\activate
   ```

3. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

4. Add the dataset: place `train.csv` inside the `data/` folder (see
   [Dataset](#-dataset) above).

5. Run the app:
   ```bash
   streamlit run app.py
   ```

6. Open the local URL Streamlit prints (usually `http://localhost:8501`) in
   your browser.

## ☁️ Deploying on Streamlit Community Cloud

1. Push this project to a public GitHub repository, including:
   - `app.py`
   - `requirements.txt`
   - `data/train.csv` (if the file is small enough for your GitHub plan;
     otherwise see the note below)
2. Go to [share.streamlit.io](https://share.streamlit.io) and sign in with
   GitHub.
3. Click **New app**, select your repository, branch, and set the main file
   path to `app.py`.
4. Click **Deploy**. Streamlit Cloud will install dependencies from
   `requirements.txt` and launch the app automatically.

> **Note on the dataset file:** GitHub has a 100 MB file size limit and
> works best with smaller files. If `train.csv` is too large to commit
> directly, consider using [Git LFS](https://git-lfs.com/), hosting the file
> on Google Drive/Kaggle and downloading it at runtime with `kagglehub`
> inside `app.py`, or committing a trimmed/sampled version of the dataset.

## 📊 Model Performance

The sidebar in the app displays the live test-set accuracy for the model
currently deployed, along with an optional confusion matrix heatmap.

## 🛠️ Tech Stack

- Python
- pandas / numpy
- scikit-learn (CountVectorizer, MultinomialNB)
- Streamlit
- matplotlib / seaborn (confusion matrix visualization)

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

## 🙋 Acknowledgements

- Dataset: [AG News Classification Dataset](https://www.kaggle.com/datasets/amananandrai/ag-news-classification-dataset) on Kaggle
