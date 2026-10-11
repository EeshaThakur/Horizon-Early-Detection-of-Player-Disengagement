# 🎮 Horizon: Early Detection of Player Disengagement

### A Deep Learning Approach to Player Engagement Classification, Behavioral Analytics, and Game Developer Decision Support

---

## 📌 1. Problem Statement

Online game developers often lack effective methods for identifying players who are gradually becoming disengaged due to frustration, repetitive gameplay, lack of progression, or reduced enjoyment. Detecting these behavioral changes early can help improve game design and player experience.

Traditional approaches may not provide sufficient insight into player behavior patterns or explain which areas of a game may require further investigation. Understanding engagement levels can help developers make more informed decisions about progression systems, difficulty balancing, rewards, and gameplay design.

**Horizon** addresses this challenge by applying deep learning and machine learning techniques to player behavioral data to classify engagement levels and generate actionable insights for game developers.

## 💡 2. Proposed Solution

Horizon uses a deep learning-based classification approach to analyze player behavior and classify engagement into three categories:

- **Low Engagement:** Players whose observed behavioral patterns correspond to the Low engagement category.
- **Medium Engagement:** Players whose observed behavioral patterns correspond to the Medium engagement category.
- **High Engagement:** Players whose observed behavioral patterns correspond to the High engagement category.

The project also compares the deep learning model with traditional machine learning algorithms and analyzes engagement distributions across different game genres.

Based on these observations, the system generates a developer-oriented report containing visualizations, genre-level comparisons, and recommendations for investigating potential engagement problems and planning future game improvements.

The objective is to support data-driven decisions that contribute to more engaging and enjoyable gaming experiences.

## 🎯 3. Project Objectives

- Analyze player behavioral data to understand engagement patterns.
- Classify player engagement into Low, Medium, and High categories.
- Develop a Multilayer Perceptron (MLP) neural network for classification.
- Compare the MLP model against traditional machine learning models.
- Evaluate model performance using appropriate classification metrics.
- Examine engagement distributions across Simulation, Strategy, Sports, Action, and RPG genres.
- Visualize model performance and genre-wise engagement patterns.
- Generate a downloadable PDF report containing analytics and developer recommendations.
- Provide actionable guidance for investigating lower engagement and extending successful gameplay experiences.
- Establish a foundation for future early-warning systems using longitudinal player data.

## 📊 4. Dataset

**Dataset:** Predict Online Gaming Behavior Dataset

**Source:** [Kaggle — Predict Online Gaming Behavior Dataset](https://www.kaggle.com/datasets/rabieelkharoua/predict-online-gaming-behavior-dataset)

The dataset contains player behavioral attributes and an `EngagementLevel` target used to train and evaluate the classification models.

The project uses the available dataset fields to study the relationship between player characteristics, behavioral metrics, game genres, and engagement categories.

### Target Variable

The target variable is `EngagementLevel`, which contains the engagement categories:

- Low
- Medium
- High

### Data Preparation

The notebook includes preprocessing and dataset preparation before model training. This includes preparing input features, encoding the target labels, applying the configured preprocessing transformations, and separating the data into training, validation, and test sets.

The preprocessing pipeline is fitted using training data to reduce the risk of information leakage into model evaluation.

> **Dataset limitation:** The available engagement labels support classification of observed engagement categories. Unless repeated observations of the same players over time are available, the dataset alone cannot establish that an individual player's engagement is gradually declining.

## 🔍 5. Exploratory Data Analysis

Exploratory data analysis is used to understand the structure of the dataset and identify patterns relevant to engagement classification.

The notebook includes analysis such as:

- Dataset inspection and feature examination.
- Engagement class distribution.
- Data preparation and split distribution checks.
- Genre-wise engagement distribution.
- Visual comparison of engagement categories.

These analyses help establish the dataset's characteristics before interpreting model results.

## 🧠 6. Machine Learning and Deep Learning Models

Horizon compares four classification approaches.

### 6.1 Multilayer Perceptron (MLP)

The MLP is the primary deep learning model in the project. It learns nonlinear relationships between input features and the target engagement categories through interconnected neural network layers.

The model is trained on the prepared training data and evaluated using validation and held-out test data.

### 6.2 Logistic Regression

Logistic Regression serves as the baseline classification model. It provides a reference point for determining whether more complex models improve predictive performance.

### 6.3 Random Forest

Random Forest combines predictions from multiple decision trees. It provides a nonlinear machine learning comparison and can capture feature interactions that a simple linear baseline may not represent effectively.

### 6.4 XGBoost

XGBoost is a gradient-boosted tree-based model used to compare the neural network against a powerful alternative for structured tabular data.

### Why Compare Multiple Models?

Comparing models helps determine whether the deep learning approach provides a meaningful improvement over traditional machine learning techniques.

The final model should be selected using held-out evaluation results, macro F1-score, class-wise performance, and the project's objectives rather than accuracy alone.

## ⚙️ 7. Project Methodology

The project follows this workflow:

1. **Dataset acquisition:** Obtain the online gaming behavior dataset from Kaggle.
2. **Data inspection:** Examine the dataset structure, columns, and engagement labels.
3. **Exploratory analysis:** Analyze class distributions and genre-wise patterns.
4. **Preprocessing:** Prepare features, encode labels, and apply required transformations.
5. **Data splitting:** Separate training, validation, and test data.
6. **Baseline training:** Train Logistic Regression as a baseline.
7. **Deep learning development:** Define and train the MLP model.
8. **Comparative modeling:** Train Random Forest and XGBoost models.
9. **Validation:** Compare model performance using validation data.
10. **Final evaluation:** Evaluate the selected models on held-out test data.
11. **Visualization:** Generate training curves, confusion matrices, and engagement charts.
12. **Developer analytics:** Analyze genre-level engagement and create recommendations.
13. **Report generation:** Export the analytics and developer action plan into a PDF report.

## 📈 8. Model Evaluation

The project uses classification metrics to assess predictive performance.

| Metric           | Purpose                                                          |
| ---------------- | ---------------------------------------------------------------- |
| Accuracy         | Measures the proportion of correctly classified observations.    |
| Precision        | Measures how many predictions for a class are correct.           |
| Recall           | Measures how many actual observations of a class are identified. |
| F1-score         | Balances precision and recall.                                   |
| Macro F1-score   | Gives equal weight to each engagement category.                  |
| Confusion matrix | Shows correct and incorrect predictions for each class.          |

Training and validation curves are also used to investigate potential overfitting or underfitting.

A large gap between training and validation performance may indicate overfitting, while poor performance on both may indicate underfitting or inadequate predictive features.

Final model performance should be reported using the actual results from the completed notebook. No performance figure should be treated as final until it has been verified on the held-out test set.

## 📉 9. Visual Analytics

The project includes visualizations to help interpret the classification results and engagement patterns.

### Model Performance Visualizations

- Training and validation loss curves.
- Training and validation performance curves, where available.
- Confusion matrix for classification errors.
- Comparative model evaluation.

### Genre-Wise Engagement Visualizations

The developer report compares observed engagement distributions across:

- Simulation
- Strategy
- Sports
- Action
- RPG

The report includes a high-engagement-by-genre chart and an engagement distribution chart comparing Low, Medium, and High categories.

These visualizations help identify patterns worth further investigation. Small differences between genres should not be interpreted as proof that one genre inherently produces better engagement.

## 🛠️ 10. Technologies Used

| Technology       | Purpose                                                                          |
| ---------------- | -------------------------------------------------------------------------------- |
| Python           | Main programming language                                                        |
| Pandas           | Data loading, manipulation, and analysis                                         |
| NumPy            | Numerical operations                                                             |
| Scikit-learn     | Preprocessing, MLP, Logistic Regression, Random Forest, and evaluation utilities |
| XGBoost          | Gradient-boosted classification                                                  |
| Matplotlib       | Data visualization and training curves                                           |
| Seaborn          | Statistical visualization, where used                                            |
| ReportLab        | PDF report generation                                                            |
| Jupyter Notebook | Interactive development environment                                              |
| Google Colab     | Cloud-based notebook execution                                                   |
| Git and GitHub   | Version control and project hosting                                              |

## ✨ 11. Key Features

- Deep learning-based engagement classification.
- Comparison of neural networks and traditional machine learning models.
- Data preprocessing and exploratory analysis.
- Training and validation performance visualization.
- Classification metrics and confusion matrices.
- Genre-wise engagement analysis.
- Automated generation of a PDF analytics report.
- Genre-specific developer recommendations.
- Guidance for investigating potential engagement issues.
- Recommendations for testing optional content and gameplay improvements.

## 🎮 12. Developer Decision Support

Horizon translates observed engagement patterns into suggestions that developers can investigate and validate.

### When Engagement Appears Relatively High

- Identify gameplay mechanics and progression patterns associated with stronger engagement.
- Preserve existing mechanics that appear to work well.
- Explore optional missions, new scenarios, meaningful milestones, and replayable challenges.
- Prototype new content before committing to large-scale development.
- Evaluate proposed changes through playtests and controlled experiments.

### When Low Engagement Is Relatively High

- Preserve the existing game and core gameplay initially.
- Investigate progression barriers and unclear objectives.
- Review difficulty balancing and onboarding.
- Examine repetitive gameplay and reward pacing.
- Collect player feedback before making major redesigns.
- Test targeted improvements and measure their effects.

### When Results Are Mixed

- Continue monitoring engagement patterns.
- Avoid making major design decisions based on small percentage differences.
- Gather additional player feedback.
- Validate proposed changes using measurable outcomes.

These recommendations are decision-support suggestions, not automatic proof of the causes of player disengagement.

## 📄 13. Generated Report

The project generates a PDF report titled:

**Game Developer Engagement Report**

The report contains:

- Executive summary.
- Genre-wise engagement charts.
- Engagement percentages and player counts.
- Genre-specific developer recommendations.
- Recommended evaluation steps.
- Interpretation notes and dataset limitations.

The report is intended to help developers review observed patterns and plan further investigation.

## 🚀 14. Getting Started

### Prerequisites

- Python environment or Google Colab.
- Access to the Kaggle dataset.
- Project notebook.
- Required Python dependencies.

### Step 1: Clone the Repository

```bash
git clone https://github.com/EeshaThakur/Online-Gaming-Player-Engagement-Analysis.git
cd Horizon-Early-Detection-of-Player-Disengagement

```

### Step 2: Install Dependencies

```bash
pip install -r requirements.txt
```

### Step 3: Download the Dataset

Download the [Predict Online Gaming Behavior Dataset from Kaggle](https://www.kaggle.com/datasets/rabieelkharoua/predict-online-gaming-behavior-dataset).

Place the CSV in the expected location or update the notebook's dataset path.

### Step 4: Open the Notebook

Open `Online_Gaming_Player_Engagement_Analysis.ipynb` in Google Colab or Jupyter Notebook.

### Step 5: Execute the Notebook

Run the notebook cells in order to load the data, preprocess features, train the models, evaluate predictions, generate visualizations, and create the developer report.

## 📁 15. Repository Structure

```text
Online-Gaming-Player-Engagement-Analysis/
│
├── Online_Gaming_Player_Engagement_Analysis.ipynb
├── Game_Developer_Engagement_Report_Final.pdf
├── requirements.txt
└── README.md
```

The filenames above should match the actual files uploaded to the repository.

## 🔮 16. Future Enhancements

Potential future improvements include:

- Collecting longitudinal player-session data.
- Tracking changes in engagement for individual players over time.
- Building an early-warning system for sustained declines in engagement.
- Evaluating calibrated disengagement-risk scores.
- Adding more detailed session-level behavioral features.
- Integrating player feedback and in-game event data.
- Testing developer interventions through controlled experiments.
- Developing an interactive dashboard for exploring engagement patterns.
- Monitoring model performance as player behavior changes.

These are proposed extensions and are not claimed as implemented features.

## ⚠️ 17. Limitations and Responsible Interpretation

The current system classifies engagement labels available in the dataset. It does not independently establish the causes of low engagement or confirm that a player is experiencing burnout.

A reliable early-detection system requires repeated observations over time, clearly defined disengagement outcomes, and evaluation of how early the system can identify meaningful changes.

Predictions should support investigation and player-experience improvements rather than automatically trigger punitive actions or intrusive interventions.

## 👥 18. Project Team

**Team Members / Roll Numbers:**

- CSE0016
- CSE0050
- CSE0052

## 📚 19. References

- [Predict Online Gaming Behavior Dataset — Kaggle](https://www.kaggle.com/datasets/rabieelkharoua/predict-online-gaming-behavior-dataset)
- [Scikit-learn Documentation](https://scikit-learn.org/stable/)
- [XGBoost Documentation](https://xgboost.readthedocs.io/)

---

**Horizon — Turning Player Engagement Data into Actionable Game Design Insights.**
