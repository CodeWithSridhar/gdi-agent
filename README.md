# gdi-agent

# GDI-Agent: Government Data Insight Agent

## Overview
GDI-Agent is a multi-agent AI system designed to help Indian government departments instantly analyze datasets, generate insights, visualize trends, and produce policy recommendations. It solves the critical problem of manual, time-consuming data analysis workflows by automating the entire analytics pipeline in minutes.

## Problem Statement
Indian government departments produce enormous amounts of data in education, health, sanitation, and other sectors. However:
- Officials lack time for deep analysis
- Many depend on outdated Excel workflows  
- Reports take weeks to months to generate
- Decision-making is delayed
- Data remains siloed and underutilized

## Solution Architecture

### 6-Agent Multi-Agent System

```
┌─────────────────────────────────────────────────────┐
│          Orchestrator Agent (Router)                │
│  Routes tasks to specialized agents & manages flow  │
└────────────┬────────────────────────────────────────┘
             │
      ┌──────┴──────┬──────────┬──────────┬──────────┐
      ▼             ▼          ▼          ▼          ▼
 ┌────────┐   ┌─────────┐   ┌───────┐ ┌────────┐ ┌──────────┐
 │ Data   │   │ Insight │   │ Viz   │ │ Policy │ │ Report   │
 │ Unders │   │ Agent   │   │ Agent │ │ Agent  │ │Generator │
 │ Agent  │   │ (ML)    │   │       │ │        │ │  Agent   │
 └────────┘   └─────────┘   └───────┘ └────────┘ └──────────┘
```

### Agent Responsibilities

**Agent 1: Orchestrator Agent**
- Routes tasks to specialized agents
- Maintains workflow consistency  
- Manages data flow between components

**Agent 2: Data Understanding Agent**
- Analyzes data types and structure
- Identifies missing values
- Creates initial data profile


**Agent 3: Insight Agent**
- Performs exploratory data analysis (EDA)
- Generates statistical insights
- Detects trends and patterns
- Identifies outliers and anomalies

**Agent 4: Visualization Agent**
- Generates interpretable charts
- Creates multi-format visualizations
- Executes Python visualization code

**Agent 5: Policy Recommendation Agent**
- Converts insights into governance actions
- Provides domain-specific recommendations
- Tailored for education, health, sanitation sectors

**Agent 6: Report Generator Agent**
- Compiles comprehensive reports
- Converts technical insights to human-friendly language
- Produces structured, actionable outputs

## Features Implemented

✅ **Multi-Agent System**: 6 specialized agents working in coordination
✅ **LLM-Powered**: Powered by Google Gemini 2.0 Flash
✅ **Tools Integration**: Custom tools for data analysis
✅ **Parallel Processing**: Multiple agents process data simultaneously
✅ **Sequential Workflows**: Orchestrated agent pipeline
✅ **Memory & State Management**: Session-based context tracking
✅ **Long-Running Operations**: Supports file uploads and batch processing
✅ **Observability**: Logging and tracing of agent actions
✅ **Cloud Deployment**: Cloud Run compatible

## Technical Stack

- **Framework**: Google ADK (Agent Development Kit)
- **LLM**: Gemini 2.0 Flash
- **Backend**: Flask + Python
- **Data Processing**: Pandas, NumPy, SciPy
- **Visualization**: Matplotlib
- **Deployment**: Google Cloud Run
- **API**: RESTful Flask API

## Installation & Setup

### Prerequisites
- Python 3.9+
- Google Cloud Account with Gemini API access
- pip package manager

### Step 1: Clone Repository
```bash
git clone https://github.com/yourusername/gdi-agent.git
cd gdi-agent
```

### Step 2: Create Virtual Environment
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

### Step 3: Install Dependencies
```bash
pip install -r requirements.txt
```

### Step 4: Set Environment Variables
```bash
echo "GEMINI_API_KEY=your-api-key-here" > .env
```

### Step 5: Run Application
```bash
python app.py
```

API will be available at `http://localhost:8000`

## Usage

### API Endpoint: POST /analyze

**Request:**
```bash
curl -X POST -F "file=@education_data.csv" \
  -F "domain=education" \
  http://localhost:8000/analyze
```

**Parameters:**
- `file`: CSV dataset (required)
- `domain`: Analysis domain - "education", "health", or "sanitation" (default: education)

**Response:**
```json
{
  "status": "success",
  "report": "=== GOVERNMENT DATA INSIGHT REPORT ===\n...",
  "domain": "education"
}
```

### Example Workflows

**Education Sector Analysis:**
```python
from main import OrchestratorAgent

orchestrator = OrchestratorAgent()
report = orchestrator.process_dataset(
    "education_data.csv",
    domain="education"
)
print(report)
```

**Health Sector Analysis:**
```python
orchestrator = OrchestratorAgent()
report = orchestrator.process_dataset(
    "health_metrics.csv",
    domain="health"
)
```

## Deployment

### Deploy to Google Cloud Run

```bash
# Set up Cloud Run authentication
gcloud auth login
gcloud config set project YOUR_PROJECT_ID

# Build and deploy
gcloud run deploy gdi-agent \
  --source . \
  --platform managed \
  --region us-central1 \
  --set-env-vars GEMINI_API_KEY=$GEMINI_API_KEY
```

Agent deployed to a public endpoint with HTTPS.

## Project Structure

```
gdi-agent/
├── main.py              # Core multi-agent implementation
├── app.py              # Flask API wrapper
├── requirements.txt    # Python dependencies
├── README.md          # This file
├── .env               # Environment variables (not in git)
├── Dockerfile         # For Cloud Run deployment
└── sample_data/
    └── education_sample.csv
```

## Key Insights Generated

1. **Data Profiling**: Automatic dataset description
2. **Statistical Analysis**: Correlations, distributions, outliers
3. **Trend Detection**: Temporal patterns in data
4. **Domain Insights**: Sector-specific findings
5. **Policy Recommendations**: Actionable governance suggestions

## Supported File Formats

- CSV files (primary)
- Excel files (.xlsx) - with minor modification
- JSON data - with preprocessing

## Performance

- **Average Processing Time**: 2-5 minutes per dataset
- **Max File Size**: 16 MB
- **Concurrent Requests**: Scalable via Cloud Run
- **Cost**: Minimal (uses efficient Gemini 2.0 Flash model)

## Future Enhancements

- [ ] Support for BigQuery data sources
- [ ] Real-time streaming data analysis
- [ ] Multi-language report generation
- [ ] Interactive dashboard visualization
- [ ] A2A Protocol for agent-to-agent communication
- [ ] Advanced ML model integration
- [ ] Scheduled automated reporting

## Contributing

Contributions welcome! Please follow these steps:
1. Fork repository
2. Create feature branch
3. Make changes with clear commit messages
4. Submit pull request


## Acknowledgments

- Google AI Agents Intensive Course
- Indian Government Data Portals
- Kaggle Community


PROJECT DESCRIPTION:

## Problem
Indian government departments face a critical bottleneck in data analytics. Despite producing enormous datasets in education, healthcare, sanitation, and other sectors, officials struggle with:
1. Fragmented, siloed data sources
2. Limited analytical capacity and expertise
3. Dependence on outdated Excel workflows
4. Report generation delays of weeks to months
5. Slow decision-making cycles leading to inefficient governance

This inefficiency costs government departments time, resources, and ultimately impacts public service delivery.

## Solution: GDI-Agent
GDI-Agent is a multi-agent AI system that automates the entire government data analysis pipeline. By orchestrating 6 specialized AI agents powered by Google Gemini 2.0 Flash, it delivers instant, evidence-based insights that empower officials to make better decisions faster.

## Architecture
The system implements a sophisticated 6-agent orchestration model:

1. **Orchestrator Agent**: Routes tasks, manages workflow consistency, and coordinates data flow
2. **Data Understanding Agent**: Profiles datasets, identifies data types, detects missing values
3. **Insight Agent**: Performs ML-powered exploratory data analysis (EDA), detects trends and patterns
4. **Visualization Agent**: Generates clear, interpretable charts and multi-format visualizations
5. **Policy Recommendation Agent**: Converts technical insights into actionable governance recommendations
6. **Report Generator Agent**: Produces comprehensive, human-friendly reports

## Key Features

**Multi-Agent Orchestration**: 6 specialized agents work in parallel and sequential workflows, each with distinct responsibilities. This modular design enables scalability and extensibility.

**Gemini 2.0 Flash Integration**: Leverages the latest LLM for reasoning, analysis, and natural language generation. The model efficiently processes large datasets and generates policy recommendations tailored to government sectors.

**Custom Tools**: Implemented tools for:
- Data type analysis
- Missing value detection
- Statistical correlation analysis
- Trend detection in temporal data
- Multi-format visualization code generation

**RESTful API**: Flask-based API endpoint (/analyze) accepts CSV uploads and returns comprehensive reports with domain-specific recommendations.

**Cloud-Native Design**: Built for deployment on Google Cloud Run with horizontal scalability and automatic load balancing.

**Domain-Specific Insights**: Tailored recommendations for:
- Education sector (resource allocation, teacher training, performance metrics)
- Health sector (disease prevention, resource distribution)
- Sanitation sector (waste management, infrastructure)

## Technical Implementation

**Multi-Agent Pattern**:
The orchestrator implements a sequential agent pipeline with intelligent task routing. Each agent receives context from previous agents and enriches it with domain-specific analysis. This ensures:
- No redundant computations
- Efficient data flow
- Clear separation of concerns
- Easy debugging and monitoring

**Memory & State Management**:
The system maintains session-based context, allowing for:
- Long-running analysis tasks
- User-specific data isolation
- Result caching for repeated queries
- Historical analysis tracking

**Error Handling & Robustness**:
- Graceful degradation for missing data
- Input validation for file uploads
- Exception handling with meaningful error messages
- Logging for observability and debugging

## Results & Impact

**Time Efficiency**: Reduces report generation from weeks to 2-5 minutes

**Scalability**: Handles datasets up to 16MB concurrently

**Cost-Effective**: Uses efficient Gemini 2.0 Flash model, minimizing API costs

**Accessibility**: No-code interface enables officials without technical expertise to conduct advanced analytics

## Use Cases

1. **Education Ministry**: Analyze student performance data to identify underperforming schools and recommend teacher training interventions

2. **Health Department**: Process disease surveillance data to predict outbreaks and allocate medical resources

3. **Sanitation Board**: Analyze hygiene metrics to identify problem areas and recommend targeted behavior-change programs

## Deployment
The application is containerized for Cloud Run deployment with:
- Environment-based configuration
- Health check endpoints
- Graceful error handling
- Production-ready logging

## Course Concepts Applied

This project demonstrates mastery of key course concepts:

1. **Multi-Agent Systems**: 6 orchestrated agents with distinct responsibilities
2. **LLM-Powered Agents**: Gemini 2.0 Flash powers reasoning and analysis
3. **Custom Tools**: Implemented data analysis and visualization tools
4. **Sequential & Parallel Workflows**: Agents process data sequentially with parallel capability
5. **Memory & Sessions**: Maintains context across analysis pipeline
6. **Observability**: Logging and tracing of agent actions
7. **Cloud Deployment**: Cloud Run compatible architecture
8. **A2A Communication**: Agents communicate with structured outputs



## Future Roadmap

1. BigQuery integration for larger datasets
2. Real-time streaming data analysis
3. Multi-language report generation (Hindi, regional languages)
4. Interactive Plotly dashboards
5. A2A Protocol for agent federation
6. Advanced ML model ensemble
7. Scheduled automated reporting

## Alignment with 'Agents for Good'

This project directly addresses the 'Agents for Good' track by:
- **Solving Real Government Challenges**: Directly addresses data analysis bottlenecks in Indian government
- **Public Impact**: Improves efficiency of education, health, and sanitation sectors affecting millions
- **Evidence-Based Policy**: Enables data-driven decision-making for better resource allocation
- **Accessibility**: Democratizes analytics for non-technical government officials
- **Scalability**: Applicable across all government departments and sectors
- **Sustainability**: Reduces manual work, allowing officials to focus on strategic decisions

## Conclusion

GDI-Agent transforms how government departments approach data analytics. By combining multi-agent orchestration with modern AI, it delivers immediate, actionable insights that improve governance efficiency and ultimately enhance public service delivery across India's education, health, and sanitation sectors.
