                 **#Pulse Crop Recommendation Demo**
 
            ##Project Team members (Participants)
  
  This project was developed collaboratively by Group 4.
1. Tsion Yohanes –    Team Leader
2. Birhanu Simachew – Member
3. Yeshiwas Tilahun – Member
4. Maru Endale –     Member
5. Samuel Medhin –   Member
6. Woldie Takele –   Member

                                          ### An AI-Powered Web Application for Pulse Crop Recommendation Based on Soil and Climate Conditions

Pulse Crop Recommendation Demo is a Streamlit-based web application that allows users to obtain machine-learning-based pulse crop recommendations using soil nutrient measurements and environmental conditions. The application provides a simple, interactive interface through which users can enter agricultural parameters and receive crop predictions from a trained Random Forest classification model through a deployed FastAPI backend.

**Live Demo:** https://pulse-crop-recommendation-demo.streamlit.app/
---
                                              ## 1. Project Overview

The Pulse Crop Recommendation Demo is the user-facing application of the Pulse Crop Recommendation System. It connects a Streamlit frontend to a FastAPI backend, which processes user inputs using a trained Random Forest machine learning model.
The application accepts seven numerical input parameters:
 Input Parameter  |  Description 
| Nitrogen (N)  |  Nitrogen content in the soil |
| Phosphorus (P)  |  Phosphorus content in the soil |
| Potassium (K)  |  Potassium content in the soil |
| Temperature  |  Environmental temperature (°C) |
| Humidity  |  Relative humidity (%) |
| Soil pH  |  Soil acidity or alkalinity |
| Rainfall  |  Rainfall measurement (dataset unit) |
After submitting the inputs, users receive a predicted pulse crop, a model confidence score, and the model version.
### Supported Crop Classes
The machine learning model supports four pulse crop categories:
- Chickpea
- Kidney beans
- Lentil
- Mungbean
---
                                                      ## 2. Key Features
The application provides the following features:

- **Interactive User Interface:** Simple and accessible interface developed using Streamlit.
- **Seven Agricultural Inputs:** Users can provide soil nutrient and environmental measurements.
- **Input Guidance:** Displays training-data ranges to help users understand the values represented in the dataset.
- **Input Range Warnings:** Identifies inputs that fall outside the observed training-data ranges.
- **Machine Learning Predictions:** Connects to the FastAPI backend to obtain crop predictions.
- **Prediction Confidence:** Displays the model confidence score returned by the backend.
- **Model Version Information:** Displays the version of the model used for prediction.
- **Real-Time API Communication:** Sends prediction requests to the deployed backend through an HTTP connection.

### How It Works
1. The user opens the Streamlit application.
2. The user enters the seven soil and environmental parameters.
3. The application checks the inputs and displays relevant range warnings.
4. The user clicks **Get Crop Recommendation**.
5. The Streamlit application sends the input values to the FastAPI prediction endpoint.
6. The backend processes the inputs using the trained Random Forest model.
7. The backend returns the prediction results.
8. The application displays the recommended crop, confidence score, and model version.
---

                                               ## 3. System Architecture
The project follows a frontend-backend architecture.
| Component | Technology | Responsibility |
|---|---|---|
| Frontend | Streamlit | User interface and input collection |
| Backend | FastAPI | Prediction request processing |
| Machine Learning | Random Forest Classifier | Pulse crop classification |
| HTTP Communication | Requests | Communication between frontend and backend |
| Model Persistence | Joblib | Loading the trained model in the backend |
| Backend Hosting | Render | Hosting the FastAPI service |
| Frontend Hosting | Streamlit Community Cloud | Hosting the interactive demo |

### Application Architecture
```text
          USER
            |
            v
   STREAMLIT WEB APPLICATION
            |
            | User inputs:
            | N, P, K, Temperature,
            | Humidity, pH, Rainfall
            |
            v
       HTTP REQUEST
            |
            v
       FASTAPI BACKEND
            |
            v
   RANDOM FOREST CLASSIFIER
            |
            v
      CROP PREDICTION
            |
            v
       API RESPONSE
            |
            v
   STREAMLIT WEB APPLICATION
            |
            v
       USER RESULTS
```
The Streamlit application handles the user interface, while the FastAPI backend handles model inference.
---
                                                      ## 4. Dataset and Machine Learning Model
The application uses a trained Random Forest classification model developed using a filtered agricultural dataset.

### Dataset Summary
| Characteristic | Description |
|---|---:|
| Original dataset | Approximately 2,200 records |
| Filtered dataset | 400 records |
| Input features | 7 |
| Target classes | 4 |
| Records per class | 100 |
| Training records | 320 (80%) |
| Testing records | 80 (20%) |
| Data splitting | Stratified |
| Random state | 42 |

### Model Information
| Property | Description |
|---|---|
| Algorithm | Random Forest Classifier |
| Task | Multiclass Classification |
| Number of estimators | 100 |
| Model version | 1.0.0 |

### Recorded Model Evaluation
The final model's recorded evaluation results were:
| Evaluation Metric | Result |
|---|---:|
| Test Accuracy | 100% |
| Macro Precision | 100% |
| Macro Recall | 100% |
| Macro F1-score | 100% |
| Weighted F1-score | 100% |
| Five-fold Cross-validation Macro F1 | 100% |
These results were obtained using the available 400-record filtered dataset. They should not be interpreted as evidence of equivalent performance on independent agricultural data or real-world farming conditions.
---
                                         ## 5. Repository Structure
The Streamlit demo repository has the following structure:
```text
Pulse-Crop-Recommendation-Demo/
│
├── streamlit_app.py
│
├── requirements.txt
│
├── .gitignore
│
└── README.md
```
### File Descriptions
| File | Description |
|---|---|
| `streamlit_app.py` | Main Streamlit application and user interface |
| `requirements.txt` | Python dependencies required to run the application |
| `.gitignore` | Specifies files and directories excluded from Git tracking |
| `README.md` | Project documentation and usage instructions |
The trained machine learning model is maintained and loaded by the separate FastAPI backend. It is not required in this frontend repository.
---
                                                ## 6. Requirements
To run the application locally, you need:
- Python 3.13 or a compatible Python version.
- pip package manager.
- Internet connection when communicating with the deployed API.
- Access to the deployed FastAPI backend or a locally running instance.
- The Python dependencies listed in `requirements.txt`.
---
                                               ## 7. Installation and Execution

### Option A: Run Locally 
**Step 1: Clone the repository**
```bash
git clone https://github.com/Birhanu21-AI/Pulse-Crop-Recommendation-Demo.git
```

**Step 2: Navigate to the project directory**
```bash
cd Pulse-Crop-Recommendation-Demo
```

**Step 3: Create a virtual environment**
```bash
python -m venv .venv
```

**Step 4: Activate the virtual environment**

Windows PowerShell:

```powershell
.venv\Scripts\Activate.ps1
```

Windows Command Prompt:

```bat
.venv\Scripts\activate.bat
```

Linux/macOS:
```bash
source .venv/bin/activate
```

**Step 5: Install dependencies**
```bash
python -m pip install --upgrade pip
pip install -r requirements.txt
```

**Step 6: Configure the API connection**
Set the `API_URL` environment variable to the base URL of the deployed FastAPI backend.

Windows PowerShell:
```powershell
$env:API_URL="https://pulse-crop-recommendation-app.onrender.com"
```

Linux/macOS:
```bash
export API_URL="https://pulse-crop-recommendation-app.onrender.com"
```

**Step 7: Run the Streamlit application**
```bash
streamlit run streamlit_app.py
```
The application will normally open in your browser at:
```text
http://localhost:8501
```

### Option B: Use the Live Application
You can access the deployed application directly without installing Python or downloading the repository.

**Live Demo:**

https://pulse-crop-recommendation-demo.streamlit.app/

---

                                                        ## 8. Backend API Connection
The Streamlit application communicates with the FastAPI backend through HTTP requests.
The backend exposes the following endpoints:
| Method | Endpoint | Purpose |
|---|---|---|
| GET | `/health` | Checks backend service health |
| POST | `/predict` | Processes crop prediction requests |

### Deployed Backend
API Base URL:
```text
https://pulse-crop-recommendation-app.onrender.com
```
Health Check:
```text
https://pulse-crop-recommendation-app.onrender.com/health
```
Prediction Endpoint:
```text
https://pulse-crop-recommendation-app.onrender.com/predict
```
The application uses the `API_URL` configuration to identify the backend service. This allows the frontend and backend to be maintained and deployed independently.
---

                                                   ## 9. Limitations and Responsible Use
The application is an educational and preliminary agricultural decision-support prototype.
Users should consider the following limitations:
- The model was trained using a filtered dataset containing only 400 records.
- The dataset's representativeness of Ethiopian agricultural conditions has not been independently established.
- Only four pulse crop categories are supported.
- The model does not predict crop yield, profitability, diseases, pests, or fertilizer requirements.
- Predictions may be less reliable for input values outside the ranges observed in the training data.
- A high model confidence score does not necessarily indicate a high probability of real-world crop suitability.
- Perfect evaluation results on the available dataset do not guarantee equivalent performance on independent agricultural data.

**Disclaimer:** This application is intended for educational and preliminary decision-support purposes. Its predictions should not be used as the sole basis for agricultural decisions. Users should consult agricultural extension professionals, qualified agronomists, and soil-testing services before making crop-selection decisions.
---

                                                ## 10. Future Improvements
Potential improvements include:
- Integrating larger and more representative agricultural datasets from Ethiopian farming regions.
- Improving input validation and user guidance.
- Expanding the number of supported pulse crops after appropriate model validation.
- Improving prediction explanations and uncertainty communication.
- Incorporating feedback from farmers and agricultural professionals.
- Conducting independent validation using real-world agricultural data.
- Improving application accessibility and user experience.
---

                                                 ## 12. Related Project Materials
The wider project includes the following materials:
- `Pulse_Crop_Recommendation.ipynb` – Model development, data preparation, and evaluation notebook.
- `Model Card.pdf` – Model purpose, performance, limitations, and technical details.
- `Data Statement.pdf` – Dataset description, preparation, and limitations.
- `Support and Improvement Plan.pdf` – Proposed maintenance and improvement activities.
- FastAPI backend repository – Model-serving API and backend implementation.
---

## Project Information

**Project Title:** Pulse Crop Recommendation System Based on Soil and Climate Conditions

**Application Name:** Pulse Crop Recommendation Demo

**Application Framework:** Streamlit

**Backend Framework:** FastAPI

**Machine Learning Algorithm:** Random Forest Classifier

**Model Version:** 1.0.0

**Project Type:** Educational Machine Learning Prototype

**Application Status:** Deployed Demo
