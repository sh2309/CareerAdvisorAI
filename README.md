# Career Advisor AI

**A Machine Learning-Based Career Recommendation System**

Career Advisor AI is a Python-based machine learning project that explores career recommendations using user profile information, including interests, skills, educational background, and qualifications. It combines TF-IDF text feature extraction, a Random Forest classifier, and an interactive Gradio interface to suggest potential career paths.

## Overview

Choosing a career can be challenging when individuals have different interests, educational backgrounds, and skill sets. Career Advisor AI demonstrates how machine learning can support career exploration by predicting suitable job-title categories from profile information.

The application processes user profile data, generates career recommendations, and displays available job descriptions and career-related questions and answers when matching records are found.

This project is an educational prototype. Its recommendations are not validated career assessments and should not be treated as definitive guidance.

## Key Features

* **Profile-Based Recommendations:** Uses available profile information to predict potential career paths.
* **Machine Learning Pipeline:** Combines TF-IDF vectorization with a Random Forest classifier.
* **Multiple Recommendations:** Displays up to three predicted career categories.
* **Career Information:** Retrieves matching job descriptions from the supplied dataset.
* **Career-Related Q&A:** Displays relevant sample questions and answers when available.
* **Interactive Interface:** Uses Gradio for profile input and recommendation display.
* **Multiple Data Sources:** Includes datasets for user profiles, career descriptions, career-related Q&A, and MI scores.

## Technologies Used

| Technology   | Purpose                                               |
| ------------ | ----------------------------------------------------- |
| Python       | Core programming language                             |
| Pandas       | Data loading and preprocessing                        |
| NumPy        | Numerical operations                                  |
| Scikit-learn | TF-IDF vectorization and Random Forest classification |
| Gradio       | Interactive user interface                            |
| OpenPyXL     | Reading Excel datasets                                |
| Google Colab | Notebook execution environment                        |
| pyngrok      | Optional public tunnel for the application            |

## How It Works

1. **Data Loading:** Loads the supplied CSV and Excel datasets.
2. **Profile Preparation:** Combines selected profile fields into a text representation and encodes job-title labels.
3. **Feature Extraction:** Converts profile text into numerical features using TF-IDF.
4. **Model Training:** Trains a Random Forest classifier to predict job-title categories.
5. **Career Prediction:** Generates and ranks potential career recommendations for the submitted profile.
6. **Supporting Information:** Searches the career-description and Q&A datasets for matching records.
7. **Result Display:** Presents recommendations and available supporting information through Gradio.

The notebook uses a train/test split with a fixed random seed. Comprehensive model evaluation is still required before making claims about predictive accuracy.

## Dataset Descriptions

| File            | Purpose                                                             |
| --------------- | ------------------------------------------------------------------- |
| `Dataset1.csv`  | Career-related questions and answers                                |
| `Dataset2.csv`  | User profiles and job-title labels; primary training dataset        |
| `Dataset3.xlsx` | MI scores; loaded but not currently used in the prediction pipeline |
| `Dataset4.xlsx` | Career and job descriptions                                         |

**Data note:** Verify dataset ownership, licensing, privacy, and redistribution permissions before publishing files in a public repository.

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
└── screenshots/
    ├── home.png
    └── career-recommendation.png
```

The `screenshots/` folder is optional and should only be included if screenshots are added.

## Installation and Setup

### Prerequisites

* Python environment or Google Colab
* Access to the project datasets
* Git, to clone the repository

### 1. Clone the Repository

```bash
git clone https://github.com/sh2309/CareerAdvisorAI.git
cd CareerAdvisorAI
```

### 2. Install Dependencies

For local execution, create and activate a virtual environment:

```bash
python -m venv .venv
```

On Windows PowerShell:

```powershell
.\.venv\Scripts\Activate.ps1
python -m pip install -r requirements.txt
```

**Note:** The current notebook imports `google.colab.userdata`, so it is designed for Google Colab. Running it locally may require changes to Colab-specific code and application launch configuration.

### 3. Open in Google Colab

[Open Career Advisor AI in Google Colab](https://colab.research.google.com/github/sh2309/CareerAdvisorAI/blob/main/main.ipynb)

### 4. Prepare the Datasets

Ensure the required CSV and Excel files are accessible from the notebook's working directory before running the data-loading cells.

### 5. Configure ngrok (Optional)

If the notebook uses ngrok to expose the Gradio interface:

1. Obtain an authentication token from your ngrok account.
2. Add it to Google Colab Secrets as `NGROK_AUTH_TOKEN`.
3. Allow the notebook to access the secret.
4. Run the relevant notebook cells.

Never hard-code authentication tokens or commit secrets to GitHub. An ngrok URL is temporary and is not a permanent deployment.

## How to Run

1. Open `main.ipynb` in Google Colab.
2. Make sure the datasets are available.
3. Run the dependency installation and import cells.
4. Execute the data-loading and preprocessing cells.
5. Train the machine learning model.
6. Launch the Gradio interface.
7. Enter a sample profile and review the recommendations.

Use fictional profile data when demonstrating the application publicly.

## Limitations

* Model performance depends on the quality and representativeness of the training data.
* Predictive accuracy has not been established through a complete evaluation.
* Some profile fields may be collected by the interface but are not currently used by the prediction function.
* The MI scores dataset is loaded but is not integrated into the current prediction pipeline.
* Career descriptions and Q&A results depend on matching records being available.
* The notebook relies on Google Colab-specific functionality and may require adaptation for local execution.
* Recommendations should not be the sole basis for education, recruitment, or career decisions.

## Future Improvements

* Evaluate the model using appropriate classification metrics and a separate test set.
* Compare alternative classifiers and tune model parameters.
* Review class imbalance and the number of examples for each career category.
* Improve recommendation explanations and handling of missing data.
* Integrate the MI scores dataset if its methodology and relevance are verified.
* Support reproducible local execution and secure deployment.
* Add automated tests, error handling, and privacy-conscious input processing.

## Credits and Acknowledgements

This project demonstrates the application of Python, machine learning, and open-source libraries to career exploration. Add verified contributor details, dataset sources, and applicable licences where appropriate.

## Disclaimer

Career Advisor AI is an educational prototype. Its outputs are data-driven suggestions, not guaranteed career outcomes, professional career counselling, or validated psychometric assessments.

## License

Add a `LICENSE` file specifying the licence under which this project may be used and distributed.
