# Breast-Cancer-Prediction

![](https://github.com/KoreJosh/Breast-Cancer-Prediction/assets/97749198/bafd0a58-dab9-472d-b262-6d3faf639885)

## Problem Statement
**Problem Statement: Breast Cancer Analysis and Prediction**

Breast cancer is one of the most prevalent cancers affecting women worldwide, with early detection significantly improving treatment outcomes. However, identifying malignant tumors from benign ones based on traditional diagnostic methods can be challenging and prone to errors. Therefore, the need arises for a robust and accurate predictive model that can analyze patient data and classify breast tumors effectively.

The objective of this project is to develop a machine learning model capable of accurately predicting breast cancer diagnosis based on clinical and imaging data. By leveraging features such as tumor stage, Histology, Proteins, HR@ status, Er status, PR status, and patient demographics, the model aims to determine if the patient would be alive after the surgery procedure with high sensitivity and specificity. Additionally, the model should provide interpretable insights into the key factors contributing to the classification decision, facilitating better understanding and trust among healthcare practitioners.

Through this analysis and prediction endeavor, we aim to empower healthcare providers with a reliable tool for early detection and risk assessment, ultimately improving patient outcomes and reducing the burden of breast cancer morbidity and mortality..

## Data Source
The dataset contains 334 rows( each rows represent a patient), and 16 columns of various medical condtions. [See Here](https://github.com/KoreJosh/Breast-Cancer-Prediction/files/14451353/BRCA.csv)

## Tools
- Python's Jupter notebook, Scikit-Learn

## Data Cleaning / Preparation

- Data Loading and Inspection
  - Using the .shape(), it shows that the dataset has 334 rows and 16 columns
- Handling missing values and duplicates
  - Using .isnull().sum() function, the number of missing values areinsignificant to affect the number of dataset available for our prediction. Hence ,theyb were dropped, also using the .duplicated().sum() function, no duplicate values was recorded.
    
## Exploratory Data Analysis
Exploratory analysis condudted on the data to derive insights such as:

### Gender count of Patients:
![Gender count](https://github.com/KoreJosh/Breast-Cancer-Prediction/assets/97749198/e9f95a34-a954-4ef9-ad2b-63d8d4ea253c)

### Tumour Stages Of Patients
![Tumour Stage](https://github.com/KoreJosh/Breast-Cancer-Prediction/assets/97749198/ac8b8d03-8a94-4161-b730-00ca5ecc43c7)

### Histology Of Patients
![Histology](https://github.com/KoreJosh/Breast-Cancer-Prediction/assets/97749198/950a15ed-8b2a-4810-af54-02de3a41217f)

Looking at the histology of breast cancer patients. 
(Histology is a description of a tumour based on how abnormal the cancer cells and 
 tissue look under a microscope and how quickly cancer can grow and spread


### Type of surgery Underwent by patients



### Mapping Categorical Variable
To carry out the prediction, the categorical dependent features were mapped out, to be better understood by the model

```
df["Tumour_Stage"] = df["Tumour_Stage"].map({"I": 1, "II": 2, "III": 3})
df["Histology"] = df["Histology"].map({"Infiltrating Ductal Carcinoma": 1, 
                                           "Infiltrating Lobular Carcinoma": 2, "Mucinous Carcinoma": 3})
df["ER status"] = df["ER status"].map({"Positive": 1})
df["PR status"] = df["PR status"].map({"Positive": 1})
df["HER2 status"] = df["HER2 status"].map({"Positive": 1, "Negative": 2})
df["Gender"] = df["Gender"].map({"MALE": 0, "FEMALE": 1})
df["Surgery_type"] = df["Surgery_type"].map({"Other": 1, "Modified Radical Mastectomy": 2, 
                                                 "Lumpectomy": 3, "Simple Mastectomy": 4})
```



### Splitting the dataset to dependent and independe nt variable.

```
#Illustrating with a trained model

X = df[['Age', 'Gender', 'Protein1', 'Protein2', 'Protein3','Protein4', 
                   'Tumour_Stage', 'Histology', 'ER status', 'PR status', 
                   'HER2 status', 'Surgery_type']]
y = df['Patient_Status']

xtrain, xtest, ytrain, ytest = train_test_split(X, y, test_size=0.10, random_state=42)

# Training using a Support Vector Clasifier Model.

model = SVC()
model.fit(xtrain,ytrain)
```


## Result / Findings

With inputed details of the dependent features the price of thr house rent can be predicted.

```
# features = [['Age', 'Gender', 'Protein1', 'Protein2', 'Protein3','Protein4', 'Tumour_Stage', 'Histology', 'ER status', 'PR status', 'HER2 status', 'Surgery_type']]
features = np.array([[36.0, 1, 0.080353, 0.42638, 0.54715, 0.273680, 3, 1, 1, 1, 2, 2,]])
print(model.predict(features))
```
With the insights gained from breast cancer analysis and prediction, we are equipped to devise more effective strategies for managing and treating this disease compared to traditional surgical approaches. By leveraging predictive models, we can enhance early detection, personalize treatment plans, and ultimately elevate survival rates. This advances our journey toward finding comprehensive solutions for breast cancer and improving outcomes for individuals affected by this condition.

