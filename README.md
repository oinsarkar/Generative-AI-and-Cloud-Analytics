# Generative-AI-and-Cloud-Analytics
Built an AI-powered health analytics platform using Streamlit, Google BigQuery, and Vertex AI to compare population health outcomes across 3,000+ U.S. counties. ● Integrated multiple CDC/CMS datasets into a unified BigQuery data warehouse and deployed Gemini-powered comparative analysis generating actionable recommendations for healthcare

# 🏥 Population Health Analytics Dashboard

An AI-powered analytics platform that compares county-level health outcomes across the United States, providing automated policy insights and recommendations using Google Cloud's Vertex AI and BigQuery.

![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![Streamlit](https://img.shields.io/badge/Streamlit-1.49+-red.svg)
![Google Cloud](https://img.shields.io/badge/Google%20Cloud-BigQuery%20%26%20Vertex%20AI-yellow.svg)
![License](https://img.shields.io/badge/License-MIT-green.svg)

## 📋 Table of Contents
- [Overview](#overview)
- [Features](#features)
- [Architecture](#architecture)
- [Technology Stack](#technology-stack)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Usage](#usage)
- [Data Sources](#data-sources)
- [Project Structure](#project-structure)
- [Screenshots](#screenshots)
- [Future Enhancements](#future-enhancements)
- [License](#license)
- [Contact](#contact)

## 🎯 Overview

This project addresses the challenge of analyzing and comparing complex population health data across 3,000+ U.S. counties. By integrating multiple public health datasets into a unified data warehouse and leveraging Generative AI, the platform enables healthcare policymakers and researchers to:

- **Compare health outcomes** between any two counties in real-time
- **Identify health disparities** across socioeconomic and behavioral factors
- **Generate AI-powered insights** with evidence-based policy recommendations
- **Visualize key health metrics** including life expectancy, chronic disease prevalence, and social determinants

## ✨ Features

### 🔍 Interactive County Comparison
- Search and select from 3,000+ U.S. counties
- Real-time data loading from Google BigQuery
- Side-by-side comparison of health indicators

### 📊 Comprehensive Health Metrics
- Life expectancy and mortality rates
- Chronic disease prevalence (obesity, diabetes, smoking)
- Socioeconomic indicators (income, education, employment)
- Healthcare access and environmental factors
- Drug overdose and firearm fatality statistics

### 🤖 AI-Powered Analysis
- Automated comparative analysis using Vertex AI Gemini
- Executive summaries highlighting key differences
- Evidence-based policy recommendations
- Health outcome correlations and contributing factors

### 📈 Data Visualization
- Quick comparison preview metrics
- Interactive expandable data panels
- Downloadable analysis reports in Markdown format

## 🏗️ Architecture

```
┌─────────────────┐
│   Streamlit     │  ← User Interface
│   Frontend      │
└────────┬────────┘
         │
         ├─────────────────────────────────┐
         │                                 │
         ▼                                 ▼
┌─────────────────┐              ┌─────────────────┐
│   BigQuery      │              │   Vertex AI     │
│  Data Warehouse │              │  Gemini Model   │
│                 │              │                 │
│  • Unified View │              │  • Analysis     │
│  • 50+ Metrics  │              │  • Insights     │
│  • 3000+ Counties│             │  • Recommendations│
└─────────────────┘              └─────────────────┘
         ▲                                 
         │                                 
┌─────────────────┐
│  Public Health  │
│   Data Sources  │
│                 │
│  • CDC PLACES   │
│  • County Health│
│    Rankings     │
│  • CMS Data     │
└─────────────────┘
```

## 🛠️ Technology Stack

### Cloud Infrastructure
- **Google Cloud Platform (GCP)**
  - BigQuery: Data warehousing and SQL queries
  - Vertex AI: Generative AI model deployment
  - IAM: Authentication and access control

### Backend & Data Processing
- **Python 3.8+**
- **Pandas**: Data manipulation and analysis
- **google-cloud-bigquery**: BigQuery Python client
- **google-cloud-aiplatform**: Vertex AI integration

### AI/ML
- **Vertex AI Gemini 1.5 Flash**: Large language model for analysis generation
- **Generative AI**: Policy recommendation synthesis

### Frontend
- **Streamlit**: Interactive web application framework
- **Markdown**: Report formatting

### Data Engineering
- **SQL**: Data querying and transformation
- **BigQuery SQL**: View creation and data integration
- **ETL**: Unified data view from multiple sources

## 📋 Prerequisites

- Python 3.8 or higher
- Google Cloud Platform account
- GCP Project with:
  - BigQuery API enabled
  - Vertex AI API enabled
  - Service Account with appropriate permissions

### Required GCP Permissions
Your service account needs:
- BigQuery Data Viewer
- BigQuery Job User
- Vertex AI User

## 🚀 Installation

### 1. Clone the Repository
```bash
git clone https://github.com/oinsarkar/population-health-ai-analytics.git
cd population-health-ai-analytics
```

### 2. Install Dependencies
```bash
pip install -r requirements.txt
```

### 3. Set Up Google Cloud Authentication

Download your service account key from GCP Console:
1. Go to IAM & Admin → Service Accounts
2. Create or select a service account
3. Create a new JSON key
4. Download and save securely

Set the environment variable:

**Windows (PowerShell):**
```powershell
$env:GOOGLE_APPLICATION_CREDENTIALS="path\to\your\service-account-key.json"
```

**macOS/Linux:**
```bash
export GOOGLE_APPLICATION_CREDENTIALS="path/to/your/service-account-key.json"
```

### 4. Configure Project Settings

Update the configuration in `app.py`:
```python
PROJECT_ID = "your-gcp-project-id"
LOCATION = "us-west1"  # or your preferred region
DATASET_ID = "pop_health_dataset"
TABLE_ID = "unified_health_view"
```

### 5. Set Up BigQuery Data

Create your unified health view in BigQuery:
```sql
CREATE OR REPLACE VIEW `your-project.pop_health_dataset.unified_health_view` AS
SELECT
  fips,
  state,
  county,
  life_expectancy,
  -- Add your health metrics columns
FROM
  `your-project.pop_health_dataset.health_data_table`
```

## 💻 Usage

### Running the Application

```bash
streamlit run app.py
```

The application will open in your default web browser at `http://localhost:8501`

### Using the Dashboard

1. **Select Location A**: Choose the first county from the dropdown
2. **Select Location B**: Choose the second county for comparison
3. **Review Metrics**: Expand the "Key Health Indicators" to see detailed metrics
4. **View Comparison Preview**: Check quick comparison metrics
5. **Generate AI Analysis**: Click the "Generate AI Analysis" button
6. **Download Report**: Save the analysis as a Markdown file

### Example Workflow

```python
# The app automatically handles:
# 1. Data retrieval from BigQuery
# 2. Metric calculation and visualization
# 3. AI prompt construction
# 4. Analysis generation via Vertex AI
# 5. Results formatting and display
```

## 📊 Data Sources

This project integrates data from:

- **CDC PLACES**: County-level health measures
- **County Health Rankings**: Social and environmental factors
- **CMS**: Healthcare access and utilization data
- **Census Bureau**: Demographic and socioeconomic data

### Data Coverage
- **Geographic**: 3,000+ U.S. counties
- **Metrics**: 50+ health indicators
- **Categories**:
  - Health outcomes (mortality, life expectancy)
  - Health behaviors (smoking, obesity, physical activity)
  - Clinical care (healthcare access, quality)
  - Social & economic factors (income, education, employment)
  - Physical environment (air quality, housing)

## 📁 Project Structure

```
population-health-ai-analytics/
│
├── app.py                          # Main Streamlit application
├── requirements.txt                # Python dependencies
├── README.md                       # Project documentation
├── LICENSE                         # MIT License
│
├── data/
│   └── sample_data.csv            # Sample dataset (optional)
│
├── screenshots/
│   ├── dashboard_overview.png
│   ├── county_comparison.png
│   └── ai_analysis_sample.png
│
└── docs/
    ├── architecture.md            # Detailed architecture
    ├── data_dictionary.md         # Health metrics descriptions
    └── deployment_guide.md        # Production deployment guide
```

## 📸 Screenshots

### Dashboard Overview

![Screenshot of the dashboard](Screenshot%202025-10-21%20164849.png)
*Main interface showing county selection and dataset overview*

### County Comparison
![Screenshot of the dashboard](Screenshot%202025-10-21%20172318.png)
*Side-by-side health metrics comparison*

### AI-Generated Analysis
![Screenshot of the dashboard](Screenshot%202025-10-21%20172404.png)
*Automated comparative analysis with policy recommendations*

## 🚀 Future Enhancements

- [ ] **Historical Trend Analysis**: Multi-year data comparison
- [ ] **Predictive Modeling**: ML models for health outcome forecasting
- [ ] **Geographic Visualization**: Interactive maps with health overlays
- [ ] **Custom Report Templates**: Configurable analysis formats
- [ ] **API Development**: RESTful API for programmatic access
- [ ] **Multi-County Comparison**: Compare 3+ counties simultaneously
- [ ] **Export Options**: PDF and Excel report generation
- [ ] **User Authentication**: Personalized dashboards and saved analyses

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👤 Contact

**Oindrila Sarkar**

- LinkedIn: [linkedin.com/in/oindrila-sarkar](https://linkedin.com/in/oindrila-sarkar)
- Email: oindrilasarkar07@gmail.com
- GitHub: [@oinsarkar](https://github.com/oinsarkar)

## 🙏 Acknowledgments

- Google Cloud Platform for BigQuery and Vertex AI services
- CDC for PLACES dataset
- County Health Rankings & Roadmaps for comprehensive health data
- Streamlit for the amazing web framework

---

**⭐ If you find this project useful, please consider giving it a star!**
