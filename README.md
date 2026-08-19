# Student Outcomes and Withdrawal-Risk Prediction

A machine-learning project developed using sensitive, anonymised student data supplied by the **University of Portsmouth**. The project investigates whether academic performance, engagement and demographic indicators can help predict:

* A student’s final academic award
* Student registration or withdrawal status
* Factors associated with academic outcomes and withdrawal risk

> **Data confidentiality:** The underlying institutional dataset is not included in this repository because it contains sensitive student information. All public code and documentation are being prepared in accordance with privacy, ethical and data-governance requirements.

## Project Aim

The aim of this project is to explore how machine-learning models could support the early identification of students who may be at risk of withdrawal or poor academic outcomes.

The analysis compares a multi-output neural network with ensemble-learning methods to assess their ability to predict student outcomes from academic, engagement and demographic information.

This work is intended as an analytical proof of concept. It is not designed to make automated decisions about individual students.

## Dataset

The original dataset was provided for academic research by the University of Portsmouth and contains historical student records from multiple institutional sources.

The analysis brings together information including:

* Module and assessment results
* First- and second-sitting performance
* Attendance information
* Virtual-learning-environment activity
* Course and enrolment information
* Placement and foundation-year indicators
* Demographic and widening-participation attributes
* Final awards and withdrawal information

Following cleaning, encoding and feature engineering, **43 features** were selected for modelling.

The raw data, student identifiers, postcodes and record-level predictions are excluded from this public repository.

## Methodology

The project workflow includes:

1. Loading and combining data from multiple institutional tables
2. Cleaning missing and inconsistent values
3. Removing unnecessary or sensitive fields
4. Encoding categorical variables
5. Conducting exploratory data analysis
6. Engineering and selecting predictive features
7. Creating training, validation and test sets
8. Training and comparing multiple classification models
9. Evaluating final-award and withdrawal-status predictions
10. Reviewing limitations, privacy risks and responsible-use considerations

## Models

### Multi-Output Neural Network

A feed-forward neural network was developed with shared hidden layers and two prediction outputs:

* Final academic award
* Student registration or withdrawal status

Dropout and early stopping were used to reduce overfitting during training.

### Random Forest

A Random Forest classifier was used as an interpretable ensemble baseline for final-award prediction and feature-importance analysis.

### XGBoost

A multi-output XGBoost classifier was used to model both student outcomes simultaneously and compare boosted-tree performance with the neural network and Random Forest approaches.

## Preliminary Results

The original notebook reported the following test-set results:

| Model          | Prediction task         | Reported accuracy |
| -------------- | ----------------------- | ----------------: |
| Neural network | Final award             |             65.0% |
| Random Forest  | Final award             |             88.9% |
| Neural network | Student status          |             99.6% |
| XGBoost        | Multi-output prediction |             90.2% |

These are preliminary results from the original academic implementation. Before treating them as evidence of real-world performance, the public version will introduce stronger validation controls, including student-level grouped splitting and checks for target leakage, class imbalance and duplicated records.

## Responsible Data Science

Educational predictions can affect real people and should be treated with particular care. Sensitive characteristics may reveal unequal outcomes but should not automatically be used to determine interventions.

Important considerations include:

* Protecting student privacy and confidentiality
* Preventing data leakage between training and testing
* Evaluating performance separately across student groups
* Examining class imbalance and minority-class recall
* Using model outputs to support—not replace—human judgement
* Avoiding punitive or discriminatory interventions
* Monitoring models for changing student populations and data drift

## Technologies

* Python
* Pandas and NumPy
* Matplotlib and Seaborn
* scikit-learn
* TensorFlow/Keras
* XGBoost
* Google Colab
* Jupyter Notebook

## Repository Structure

```text
student-outcomes-withdrawal-prediction/
├── notebooks/
│   └── student_outcomes_withdrawal_prediction.ipynb
├── README.md
├── requirements.txt
└── .gitignore
```

## Reproducibility

The confidential University of Portsmouth dataset cannot be redistributed. The public notebook will therefore:

* Remove private Google Drive paths
* Remove student-level outputs and identifying fields
* Document the expected input schema
* Provide clear preprocessing and modelling stages
* Use fixed random seeds where appropriate
* Include either synthetic demonstration data or instructions for authorised users

## Limitations

* The data represents a specific historical institutional context.
* Some outcome classes contain substantially fewer examples than others.
* Multiple records may belong to the same student.
* High accuracy may be affected by class imbalance, duplicated observations or target leakage.
* Accuracy alone is insufficient for evaluating withdrawal-risk models.
* Results should not be generalised to other universities without external validation.
* Sensitive institutional data cannot be included for independent reproduction.

## Future Improvements

* Perform student-level grouped train-test splitting
* Build a leakage-resistant preprocessing pipeline
* Add precision, recall, macro F1 and balanced-accuracy comparisons
* Evaluate withdrawal recall and precision-recall curves
* Introduce class weighting or resampling where appropriate
* Assess fairness across relevant demographic groups
* Add SHAP-based model explanations
* Provide a synthetic dataset for full public reproducibility
* Develop an ethical early-support dashboard prototype

## Author

**Mohammed Elata**
BSc Data Science & Analytics
MSc Data Analytics with Distinction
