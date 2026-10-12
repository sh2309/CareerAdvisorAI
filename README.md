# Career Advisor AI

**A Machine Learning-Based Career Recommendation System**

Career Advisor AI is a machine learning project that explores how a user's interests, skills, educational background, and qualifications can be used to suggest potential career paths. The project combines text-based feature extraction, a classification model, and an interactive Gradio interface to generate career recommendations.

## Overview

Choosing a career can be challenging when people have different interests, academic backgrounds, and skill sets. Career Advisor AI aims to make career exploration more accessible by providing recommendations based on information entered by the user.

The application processes a user's profile, predicts suitable job-title categories using a trained machine learning pipeline, and presents the top suggested careers along with available job descriptions, sample career-related questions and answers, and alternative recommendations.

This project is an educational prototype intended to demonstrate the application of machine learning to career exploration. Its recommendations should not be treated as definitive career assessments.

## Key Features

- **Profile-based recommendations:** Uses interests, skills, education, specialization, and certification information as text inputs for career prediction.
- **Machine learning pipeline:** Combines TF-IDF text vectorization with a Random Forest classifier.
- **Multiple career suggestions:** Displays up to three predicted career categories.
- **Career information:** Retrieves matching job descriptions from the supplied career-description dataset when a match is available.
- **Career-related Q&A:** Displays sample questions and answers associated with the recommended role when matching records exist.
- **Interactive interface:** Uses Gradio to provide a form-based interface for entering profile information and viewing recommendations.
- **Modular data sources:** Uses separate datasets for career-related Q&A, user profiles, MI scores, and job descriptions.

## Technologies Used

| Technology | Purpose |
|---|---|
| Python | Main programming language |
| Pandas | Data loading and preprocessing |
| NumPy | Numerical operations and prediction ranking |
| Scikit-learn | TF-IDF vectorization, label encoding, train/test splitting, and Random Forest classification |
| Gradio | Interactive application interface |
| OpenPyXL | Reading Excel datasets |
| Google Colab | Notebook execution environment |
| pyngrok | Optional public tunnel to the running application |

## How It Works

1. **Data loading:** Loads the four supplied CSV and Excel datasets.
2. **Profile preparation:** Uses the user-profile dataset to combine selected profile fields into a single text representation. Job titles are normalized and encoded into numeric labels.
3. **Feature extraction:** TF-IDF converts the combined profile text into numerical features.
4. **Model training:** A Random Forest classifier learns to predict job-title categories from the prepared profile data.
5. **Career prediction:** The application processes a submitted profile and ranks the predicted career categories.
6. **Supporting information:** The application searches the career-description and Q&A datasets for information matching the top recommendation.
7. **Result display:** Gradio displays the recommendation and any available supporting information.

The current implementation uses a train/test split with a fixed random seed. A comprehensive evaluation of model performance is still required before making claims about predictive accuracy.

## Dataset Descriptions

The project contains four datasets:

| File | Purpose | Current usage |
|---|---|---|
| `Dataset1.csv` | Career-related questions and answers | Retrieves sample Q&A matching the recommended role |
| `Dataset2.csv` | User profiles and job-title labels | Primary dataset used to prepare training examples |
| `Dataset3.xlsx` | MI scores dataset | Loaded by the notebook but not used in the current prediction pipeline |
| `Dataset4.xlsx` | Career and job descriptions | Retrieves additional information about a recommended career |

**Data note:** Dataset availability, ownership, licensing, and redistribution permissions should be verified before publishing the files publicly. Do not commit personal or confidential information.

## Project Structure

```text
CareerAdvisorAI/
├── README.md
├── main.ipynb
├── requirements.txt
├── Dataset1.csv
├── Dataset2.csv
├── Dataset3.xlsx
├── Dataset4.xlsx
└── screenshots/              # Optional
    ├── home.png
    └── career-recommendation.png
```

## Installation and Setup

### Prerequisites

- A GitHub account to access the repository.
- A Google account to run the notebook in Google Colab.
- Permission to access and use the project datasets.

### 1. Clone the repository

```bash
git clone https://github.com/sh2309/CareerAdvisorAI.git
cd CareerAdvisorAI
```

### 2. Install dependencies

For a local Python environment, create and activate a virtual environment, then install the listed packages.

```bash
python -m venv .venv
```

On Windows PowerShell:

```powershell
.\.venv\Scripts\Activate.ps1
python -m pip install -r requirements.txt
```

The current notebook imports `google.colab.userdata`, so it is designed for Google Colab and will not run unchanged in a standard local Python environment. Local execution requires adapting the Colab-specific code and configuring the application launch process.

### 3. Open the notebook in Google Colab

Open `main.ipynb` from the repository and select **Open in Colab**, if available. Alternatively, use the following link after the notebook has been moved to the repository root:

[Open Career Advisor AI in Google Colab](https://colab.research.google.com/github/sh2309/CareerAdvisorAI/blob/main/main.ipynb)

### 4. Make the datasets available

Ensure all four dataset files are present in the notebook's working directory in Colab before running the data-loading cells. Download or upload the files as needed, subject to their usage permissions.

### 5. Configure the optional ngrok tunnel

The notebook uses Google Colab Secrets to retrieve an ngrok authentication token.

1. Obtain an ngrok authentication token from your ngrok account.
2. In Google Colab, open the Secrets panel.
3. Add a secret named `NGROK_AUTH_TOKEN`.
4. Enable notebook access to that secret.
5. Run the notebook cells in order.

Never hard-code your token in the notebook, commit it to GitHub, or include it in screenshots or notebook outputs. The public URL generated by ngrok is temporary and should not be treated as a permanent deployment.

## How to Run the Application

1. Open `main.ipynb` in Google Colab.
2. Ensure the four datasets are accessible from the notebook's working directory.
3. Run the dependency-installation and import cells.
4. Run the dataset-loading and preprocessing cells.
5. Train the machine learning pipeline.
6. Run the career prediction function and Gradio interface cells.
7. Enter sample profile information and review the generated recommendations.
8. If using ngrok, configure the required secret before launching the tunnel.

Use fictional sample profiles when demonstrating the application publicly.

## Limitations

- The current model depends on the quality, size, and representativeness of the supplied user-profile dataset.
- Career recommendations reflect learned associations in the training data and may not generalize to every user.
- Predictive accuracy has not been established through a complete evaluation in the current notebook.
- Some form fields are collected but are not currently used in the prediction function. The implementation should be reviewed so that the interface accurately reflects the model's behavior.
- The MI scores dataset is loaded but is not currently integrated into the prediction pipeline.
- Career descriptions and Q&A entries are only displayed when matching records are found.
- The current implementation relies on Google Colab-specific functionality and an optional ngrok tunnel rather than a permanent production deployment.
- The system should not be used as the sole basis for education, recruitment, or career decisions.

## Future Improvements

- Evaluate the model using appropriate classification metrics and a documented test set.
- Compare alternative models and tune hyperparameters using a suitable validation strategy.
- Review class imbalance and the number of training examples available for each job category.
- Incorporate additional profile fields only when their relevance and treatment are justified.
- Improve recommendation explanations and handle missing or unmatched career descriptions gracefully.
- Integrate the MI scores dataset if its methodology, licensing, and relevance are verified.
- Adapt the application for a reproducible local environment or a secure, permanent deployment.
- Add automated tests, clearer error handling, and privacy-conscious input handling.

## Credits and Acknowledgements

This project was developed as a machine learning and career-exploration project using Python and open-source libraries.

Dataset creators, original project collaborators, and other contributors should be acknowledged here once their names and contributions have been verified. Dataset sources and applicable licences should also be documented.

## Disclaimer

Career Advisor AI is an educational prototype. Its outputs are suggestions generated from the available training data and should not be interpreted as guaranteed outcomes, professional career counselling, or validated psychometric assessments.