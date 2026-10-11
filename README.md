# 🎮 Horizon: Early Detection of Player Disengagement

**A Deep Learning Approach to Player Engagement Classification, Behavioral Analytics, and Game Developer Decision Support**

Horizon analyzes observed online gaming behavior and classifies player engagement as **Low, Medium, or High**. It compares a Multilayer Perceptron (MLP) with traditional machine-learning models and generates genre-level analytics to help developers identify patterns worth investigating.

> **Important limitation:** The current dataset supports classification of observed engagement categories. Without repeated observations of individual players over time, the model cannot prove that a player's engagement is gradually declining or establish why their engagement is low.

## 1. Problem Statement

Online game developers need better ways to understand player behavior and identify engagement patterns that may warrant investigation. Frustration, repetitive gameplay, unclear progression, and reduced enjoyment may contribute to disengagement, but observed engagement labels alone do not establish these causes.

Horizon uses machine-learning and deep-learning models to classify engagement categories, compare predictive performance, and summarize engagement patterns across game genres. Its reports provide decision-support suggestions for further investigation rather than automatic proof of a problem or its cause.

## 2. Project Objectives

- Analyze player behavior and engagement patterns.
- Classify engagement into Low, Medium, and High categories.
- Develop a Multilayer Perceptron (MLP) neural network.
- Compare the MLP with Logistic Regression, Random Forest, and XGBoost.
- Evaluate models using accuracy, precision, recall, F1-score, macro F1-score, and confusion matrices.
- Analyze engagement distributions across Simulation, Strategy, Sports, Action, and RPG genres.
- Generate visualizations and a developer-oriented PDF report.
- Analyze misclassified predictions and document experiment settings for reproducibility.
- Establish a foundation for future early-warning research using longitudinal player data.

## 3. Dataset

- **Dataset:** Predict Online Gaming Behavior Dataset
- **Source:** [Kaggle — Predict Online Gaming Behavior Dataset](https://www.kaggle.com/datasets/rabieelkharoua/predict-online-gaming-behavior-dataset)
- **Target variable:** `EngagementLevel`
- **Classes:** Low, Medium, High

The notebook prepares input features, encodes target labels, applies preprocessing transformations, and separates the data into training, validation, and test sets. Preprocessing is fitted on training data to reduce information leakage into model evaluation.

### Recorded Dataset Details

| Property | Value |
|---|---|
| Rows after duplicate removal | 40,034 |
| Dataset columns | 13 |
| Processed features | 21 |
| Target variable | `EngagementLevel` |
| Training split | 70% |
| Validation split | 15% |
| Test split | 15% |

These values are from the latest recorded reproducibility output and should be regenerated if the dataset or preprocessing changes.

## 4. Exploratory Data Analysis

The notebook includes:

- Dataset inspection and feature examination.
- Engagement class distribution.
- Data preparation and split distribution checks.
- Genre-wise engagement distribution.
- Visual comparisons of engagement categories.

These analyses help establish the dataset's characteristics before interpreting model results.

Genre differences should be treated as observed patterns that warrant further investigation, not proof that a particular genre inherently causes better or worse engagement.

## 5. Machine Learning and Deep Learning Models

Horizon compares four classification approaches.

### 5.1 Multilayer Perceptron (MLP)

The MLP is the primary deep-learning classifier. Its recorded configuration is:

| Parameter | Configuration |
|---|---|
| Hidden layers | 64 and 32 neurons |
| Hidden activation | ReLU |
| Output activation | Softmax |
| Optimizer | Adam |
| Learning rate | 0.001 |
| Loss function | Sparse categorical cross-entropy |
| Batch size | 64 |
| Maximum epochs | 100 |
| Dropout rates | 0.30 and 0.20 |
| L2 regularization | 0.001 |
| Early stopping | Validation loss, patience 10 |
| Restore best weights | Enabled |
| Learning-rate reduction | Factor 0.5, patience 4 |
| Minimum learning rate | 0.000001 |

The architecture and training settings are documented from the recorded experiment. Results can vary with hardware, framework versions, and nondeterministic operations.

### 5.2 Logistic Regression

Logistic Regression serves as the baseline classifier. It provides a reference point for determining whether more complex models improve predictive performance.

### 5.3 Random Forest

Random Forest combines predictions from multiple decision trees and can capture nonlinear relationships and feature interactions.

### 5.4 XGBoost

XGBoost is a gradient-boosted tree-based model used to compare the neural network against a strong alternative for structured tabular data.

### Why Compare Multiple Models?

Comparing different approaches helps determine whether the deep-learning model provides a meaningful improvement over traditional machine-learning techniques.

The preferred model should be selected using held-out test performance, macro F1-score, class-wise metrics, and project objectives—not accuracy alone.

## 6. Project Methodology

The project follows this workflow:

1. **Dataset acquisition:** Obtain the online gaming behavior dataset from Kaggle.
2. **Data inspection:** Examine the dataset structure, columns, and engagement labels.
3. **Exploratory analysis:** Analyze class distributions and genre-wise patterns.
4. **Preprocessing:** Prepare features, encode labels, and apply required transformations.
5. **Data splitting:** Separate training, validation, and test data.
6. **Baseline training:** Train Logistic Regression.
7. **Deep learning development:** Define and train the MLP model.
8. **Comparative modeling:** Train Random Forest and XGBoost.
9. **Model evaluation:** Compare classification performance on held-out data.
10. **Error analysis:** Review misclassified observations and actual-versus-predicted class pairs.
11. **Visualization:** Generate training curves, confusion matrices, and engagement charts.
12. **Developer analytics:** Analyze genre-level engagement and prepare recommendations.
13. **Report generation:** Export analytics and the developer action plan into a PDF report.
14. **Reproducibility:** Save experiment settings and package-version information.

## 7. Model Evaluation and Error Analysis

The project uses the following classification metrics:

| Metric | Purpose |
|---|---|
| Accuracy | Measures the proportion of correctly classified observations. |
| Precision | Measures how many predictions for a class are correct. |
| Recall | Measures how many actual observations of a class are identified. |
| F1-score | Balances precision and recall. |
| Macro F1-score | Gives equal weight to each engagement category. |
| Confusion matrix | Shows correct and incorrect predictions for each class. |

### Error Analysis

The error-analysis step reviews:

- Actual engagement categories.
- Predicted engagement categories.
- Correct and incorrect predictions.
- Actual-versus-predicted class combinations.
- Prediction confidence, where available.
- Misclassification summaries.

The generated CSV files can help identify which engagement categories are most often confused and where the model may require improvement.

Misclassification analysis is diagnostic. A confident prediction can still be wrong, and these results do not establish the cause of a player's engagement level.

### Overfitting and Underfitting

Training and validation curves should be reviewed to investigate potential overfitting or underfitting.

- **Possible overfitting:** Training performance is substantially better than validation performance.
- **Possible underfitting:** Both training and validation performance are poor.

Dropout, L2 regularization, early stopping, and learning-rate reduction are included in the recorded MLP configuration to support training stability and generalization.

Final performance values should be reported from the actual completed notebook run rather than assumed or hard-coded into this README.

## 8. Reproducibility

The notebook records experiment metadata in:

`outputs/results/reproducibility_details.json`

The report includes:

- Python version and platform information.
- Random seed (`42`).
- Dataset dimensions and target classes.
- Training, validation, and test split percentages.
- MLP architecture and training settings.
- Installed package versions.

A package snapshot is also saved as:

`outputs/results/environment_requirements.txt`

These files document the environment used for an experiment and help other developers reproduce the setup.

For best reproducibility, run notebook cells in order, preserve the dataset version, and use the recorded package versions. Identical results are not guaranteed across different hardware and software environments.

## 9. Architecture and Workflow Diagrams

The notebook includes code to generate the following diagrams:

- `outputs/charts/mlp_architecture.png` — illustrates the MLP architecture.
- `outputs/charts/project_workflow.png` — illustrates the end-to-end project workflow.

These images are available after the diagram-generation cell runs successfully. Copy the generated images into the repository's `charts/` directory if you want them displayed on GitHub.

## 10. Visual Analytics and Developer Decision Support

Horizon analyzes observed engagement distributions across:

- Simulation
- Strategy
- Sports
- Action
- RPG

The developer report is designed to include:

- Executive summary.
- Genre-wise engagement charts.
- Engagement percentages and player counts.
- Genre-specific developer recommendations.
- Suggested evaluation steps.
- Interpretation notes and dataset limitations.

### When Engagement Appears Relatively High

- Investigate gameplay mechanics and progression patterns associated with stronger observed engagement.
- Preserve mechanics that appear to work well.
- Explore optional missions, meaningful milestones, new scenarios, and replayable challenges.
- Prototype new content before committing to large-scale development.
- Evaluate changes through playtests or controlled experiments.

### When Low Engagement Is Relatively High

- Investigate progression barriers and unclear objectives.
- Review difficulty balancing and onboarding.
- Examine repetitive gameplay and reward pacing.
- Collect player feedback before making major redesigns.
- Test targeted improvements and measure their effects.

### When Results Are Mixed

- Continue monitoring engagement patterns.
- Avoid major decisions based on small percentage differences.
- Gather additional player feedback.
- Validate proposed changes using measurable outcomes.

These recommendations are suggestions for investigation, not causal conclusions.

## 11. Technologies Used

| Technology | Purpose |
|---|---|
| Python | Main programming language |
| Pandas | Data manipulation and analysis |
| NumPy | Numerical operations |
| Scikit-learn | Preprocessing, baseline modeling, Random Forest, and evaluation |
| TensorFlow / Keras | Deep-learning model development |
| XGBoost | Gradient-boosted classification |
| Matplotlib | Data visualization |
| Seaborn | Statistical visualization, where used |
| ReportLab | PDF report generation |
| Jupyter Notebook | Interactive development |
| Google Colab | Cloud-based notebook execution |
| Git and GitHub | Version control and project hosting |

## 12. Repository Structure

The repository currently organizes project files into these main areas:

```text
Horizon-Early-Detection-of-Player-Disengagement/
├── Models/
├── charts/
├── notebook/
├── results/
├── requirements.txt
└── README.md
```

Keep this structure synchronized with the files actually committed to GitHub. Generated models, charts, reports, and results should be included only when they exist and are intended to be shared.

## 13. Getting Started

### Prerequisites

- Python environment or Google Colab.
- Access to the Kaggle dataset.
- Git, if cloning the repository.

### Step 1 — Clone the Repository

```bash
git clone https://github.com/EeshaThakur/Horizon-Early-Detection-of-Player-Disengagement.git
cd Horizon-Early-Detection-of-Player-Disengagement
```

### Step 2 — Install Dependencies

```bash
pip install -r requirements.txt
```

### Step 3 — Download the Dataset

Download the [Predict Online Gaming Behavior Dataset from Kaggle](https://www.kaggle.com/datasets/rabieelkharoua/predict-online-gaming-behavior-dataset).

Place the CSV where the notebook expects it, or update the dataset path in the notebook. Do not commit private credentials or unnecessary copies of the dataset.

### Step 4 — Open the Notebook

Open `Online_Gaming_Player_Engagement_Analysis.ipynb` from the `notebook/` folder in Google Colab or Jupyter Notebook, depending on the current repository layout.

### Step 5 — Run the Notebook

Run the cells in order to load and preprocess data, train models, evaluate predictions, conduct error analysis, save reproducibility details, and generate diagrams and the developer report.

Confirm that output files were generated before committing them to GitHub.

## 14. Limitations and Responsible Interpretation

- The current target classifies observed engagement; it does not directly measure a decline over time.
- Available labels alone do not prove why a player has low engagement.
- Genre-level differences are descriptive and do not establish causality.
- Test metrics must be verified on held-out data.
- Predictions should support investigation and player-experience improvements rather than punitive or intrusive actions.

A stronger early-warning system would require repeated session-level observations, a clearly defined disengagement outcome, temporal validation, and evaluation of how early the system identifies meaningful changes.

## 15. Future Enhancements

Potential future improvements include:

- Collecting longitudinal player-session data.
- Tracking changes in individual engagement over time.
- Defining and evaluating disengagement-risk scores.
- Adding detailed session-level behavioral features and player feedback.
- Evaluating calibrated predictions and temporal validation strategies.
- Testing developer interventions through controlled experiments.
- Developing an interactive analytics dashboard.
- Monitoring model performance as player behavior changes.

These are proposed extensions and are not claims that the features are already implemented.

## 16. Project Team

Update this section with the **confirmed team members and roll numbers** before submission.

## 17. References

- [Predict Online Gaming Behavior Dataset — Kaggle](https://www.kaggle.com/datasets/rabieelkharoua/predict-online-gaming-behavior-dataset)
- [Scikit-learn Documentation](https://scikit-learn.org/stable/)
- [TensorFlow Documentation](https://www.tensorflow.org/)
- [XGBoost Documentation](https://xgboost.readthedocs.io/)
