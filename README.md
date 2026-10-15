# Emotion Detection

## 🌐 Live Demo

Try the deployed application here: [Emotion Detection Web App](https://emotion-detection-system-dkuixb8c2o3ea5umiwszjv.streamlit.app/)

A machine-learning web application that predicts the dominant emotion
expressed in English text. The interface is built with Streamlit, and
the classifier uses TF-IDF features with Logistic Regression.

## Features

-   Predicts one of six emotions: **Joy, Sadness, Anger, Fear, Love,**
    or **Surprise**.
-   Provides example sentences for quick testing.
-   Displays the predicted emotion and model confidence when available.
-   Uses a dark-themed, responsive Streamlit interface.
-   Loads a trained model, TF-IDF vectorizer, and label mapping from
    local files.

## Technology Stack

-   Python
-   Streamlit
-   scikit-learn
-   NLTK
-   Pandas
-   Matplotlib

## Project Structure

``` text
Emotion-Detection/
├── app.py
├── logistic_model.pkl
├── tfidf_vectorizer.pkl
├── emotion_label_mapping.json
├── requirements.txt
├── train.txt
├── Emotion_analysis.ipynb
└── assets/
    ├── joy.png
    ├── sadness.png
    ├── anger.png
    ├── fear.png
    ├── love.png
    └── surprise.png
```

The filenames above are the expected layout. Use the exact filenames
your application configuration references. The model and vectorizer must
come from the same training run.

## Setup

### 1. Clone or download the project

Open a terminal in the project directory.

### 2. Create and activate a virtual environment (recommended)

**Windows**

``` bash
python -m venv .venv
.venv\Scripts\activate
```

### 3. Install dependencies

If `requirements.txt` is available:

``` bash
python -m pip install -r requirements.txt
```

Ensure the dependencies include Streamlit, scikit-learn, NLTK, Pandas,
and Matplotlib as required by your `app.py`.

### 4. Download NLTK stopwords

The app's preprocessing uses NLTK English stopwords:

``` bash
python -m nltk.downloader stopwords
```

### 5. Add model and asset files

Place the trained Logistic Regression model, its matching TF-IDF
vectorizer, and `emotion_label_mapping.json` in the project directory.
Place emotion images in the `assets/` directory using the expected
filenames.

### 6. Run the app

``` bash
streamlit run app.py
```

Streamlit will print a local URL in the terminal. Open that URL in your
browser.

## Training and Evaluation

Use `Emotion_analysis.ipynb` and the training dataset
(`train.txt`) to train and evaluate the classifier. Review the
classification report, including precision, recall, and F1-score for
each emotion, and the macro F1-score.

If you retrain the model, save the model and TF-IDF vectorizer together
and replace both files in the app. Also update the label mapping if it
changes. To avoid scikit-learn compatibility warnings, train and load
the saved artifacts with the same scikit-learn version. Check the active
version with:

``` bash
python -c "import sklearn; print(sklearn.__version__)"
```

Do not claim a fixed accuracy unless you report the value measured by
your latest notebook run.

## Important Notes

-   Emotion classification is a prediction, not a definitive
    interpretation of a person's feelings.
-   Confidence scores are model outputs and should not be treated as
    calibrated probabilities unless calibration has been evaluated.
-   Preprocessing used in the app should match the preprocessing used
    during training.
-   Keep the model and vectorizer paired; mismatched files can cause
    errors or unreliable predictions.

## Troubleshooting

**Missing NLTK stopwords**

``` bash
python -m nltk.downloader stopwords
```

**Model/vectorizer feature mismatch**\
Use the model and vectorizer saved from the same training run.

**scikit-learn version warning**\
Check the version used to train the artifacts and the version used by
Streamlit. Prefer matching versions, or retrain and resave both
artifacts in the current environment.

**Images not appearing**\
Check that the `assets/` folder exists and that filenames match those
referenced in `app.py`.

## Future Improvements

-   Improve performance on underrepresented emotion classes.
-   Add more examples and evaluate with a held-out test set.
-   Compare Logistic Regression with additional classifiers.
-   Add a confusion matrix and class-wise evaluation summary to the
    training notebook.
