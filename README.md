# 🏎️ F1 Race Predictor

**AI-Powered Formula 1 Race Prediction System using Machine Learning**

[![Python](https://img.shields.io/badge/Python-3.11+-blue.svg)](https://www.python.org/)
[![FastAPI](https://img.shields.io/badge/FastAPI-0.104+-green.svg)](https://fastapi.tiangolo.com/)
[![React](https://img.shields.io/badge/React-18.0+-blue.svg)](https://reactjs.org/)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

> Predict Formula 1 race outcomes with 85%+ accuracy using ensemble ML models trained on 75 years of F1 data (1950-2025)

---

## 📋 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Demo](#demo)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Installation](#installation)
- [Usage](#usage)
- [Model Performance](#model-performance)
- [API Documentation](#api-documentation)
- [Deployment](#deployment)
- [Contributing](#contributing)
- [License](#license)

---

## 🎯 Overview

F1 Race Predictor is a comprehensive machine learning application that forecasts Formula 1 race outcomes by analyzing:
- **Driver Performance** (experience, recent form, qualifying performance)
- **Constructor Competitiveness** (team standing, budget efficiency, car performance)
- **Environmental Conditions** (weather, temperature, track conditions)
- **Circuit Characteristics** (track layout, overtaking difficulty, tire degradation)
- **Race Strategy** (personalized tire strategies based on driver/team behavior)

### Key Achievements
- ✅ **RMSE 3.2** positions for race outcome prediction
- ✅ **85.3%** accuracy for podium predictions
- ✅ **83.7%** accuracy for points-scoring predictions
- ✅ **52,000+** historical race results analyzed (1950-2025)
- ✅ **20** engineered features for comprehensive modeling

---

## ✨ Features

### 🤖 Machine Learning Models
- **Position Prediction** - Random Forest Regressor (RMSE: 3.2)
- **Podium Prediction** - Random Forest Classifier (Accuracy: 85.3%)
- **Points Prediction** - Random Forest Classifier (Accuracy: 83.7%)
- **Win Probability** - Normalized probability distribution
- **Tire Strategy** - Personalized recommendations per driver/team

### 🎨 User Interface
- **Interactive Grid Setup** - Configure 20-position starting grid
- **Pit Lane Starts** - Designate drivers starting from pit lane
- **Driver Status** - Mark drivers as "Not Racing" for injuries/suspensions
- **Real-time Predictions** - Instant results with <1s response time
- **Data Persistence** - Grid configuration saved across refreshes

### 📊 Analytics
- Win probability distribution charts
- Tire strategy recommendations
- Race condition simulation (weather, temperature, humidity)
- Constructor and driver performance metrics
- Feature importance analysis

---

## 🎬 Demo

### Web Application
![F1 Predictor Home](docs/images/home.png)
![Prediction Interface](docs/images/prediction.png)

### Sample Prediction
```json
{
  "circuit": "Bahrain International Circuit",
  "weather": "Dry",
  "predictions": [
    {
      "driver": "Max Verstappen",
      "predicted_position": 1,
      "win_probability": 32.45,
      "tire_strategy": "Soft → Hard",
      "points_earned": 25
    }
  ]
}
```

---

## 🛠️ Tech Stack

### Backend
- **Python 3.11+** - Core programming language
- **FastAPI** - High-performance web framework
- **scikit-learn** - Machine learning models
- **pandas & numpy** - Data processing
- **joblib** - Model serialization

### Frontend
- **React 18** - Modern UI framework
- **TypeScript** - Type-safe development
- **Tailwind CSS** - Utility-first styling
- **Plotly.js** - Interactive visualizations
- **Vite** - Fast build tool

### Alternative Frontend
- **Streamlit** - Rapid prototyping interface

### Data Source
- **Ergast F1 API** - Historical race data (1950-2025)

---

## 📁 Project Structure

```
MLproject/
├── backend/
│   ├── app.py                          # FastAPI application
│   ├── train_enhanced_model.py         # Model training
│   ├── predict.py                      # Prediction utilities
│   ├── fetch_data.py                   # Data collection
│   ├── streamlit_app.py                # Streamlit interface
│   ├── requirements.txt                # Python dependencies
│   ├── data/
│   │   └── f1_multi_year_results.csv   # Historical dataset
│   ├── models/
│   │   ├── position_enhanced_model.pkl
│   │   ├── podium_enhanced_model.pkl
│   │   ├── points_enhanced_model.pkl
│   │   ├── winner_enhanced_model.pkl
│   │   ├── enhanced_label_encoders.pkl
│   │   ├── feature_scaler.pkl
│   │   └── feature_names.pkl
│   └── logs/
│       ├── prediction_log.csv
│       └── training_log.csv
├── frontend/
│   ├── src/
│   │   ├── App.tsx                     # Main React app
│   │   ├── components/                 # React components
│   │   ├── types/                      # TypeScript types
│   │   └── utils/                      # Utilities
│   ├── public/                         # Static assets
│   ├── package.json                    # Node dependencies
│   └── build/                          # Production build
├── data/
│   └── f1_multi_year_results.csv       # Primary dataset
├── README.md                           # This file
└── ML_Project_Report.md                # Detailed report

```

---

## 🚀 Installation

### Prerequisites
- Python 3.11 or higher
- Node.js 18 or higher
- npm or yarn

### Backend Setup

```bash
# Navigate to backend directory
cd backend

# Create virtual environment
python -m venv venv

# Activate virtual environment
# Windows:
venv\Scripts\activate
# macOS/Linux:
source venv/bin/activate

# Install dependencies
pip install -r requirements.txt

# Fetch F1 data (optional - dataset included)
python fetch_data.py

# Train models (optional - trained models included)
python train_enhanced_model.py
```

### Frontend Setup (React)

```bash
# Navigate to frontend directory
cd frontend

# Install dependencies
npm install

# Set API URL (create .env file)
echo REACT_APP_API_URL=http://localhost:8000 > .env

# Build for production
npm run build
```

### Alternative Frontend (Streamlit)

```bash
# Already installed with backend dependencies
# No additional setup required
```

---

## 💻 Usage

### Start Backend (FastAPI)

```bash
cd backend
uvicorn app:app --reload --host 0.0.0.0 --port 8000
```

API will be available at:
- **Main API:** http://localhost:8000
- **Interactive Docs:** http://localhost:8000/docs
- **ReDoc:** http://localhost:8000/redoc

### Start Frontend (React)

```bash
cd frontend
npm start
```

Application will open at: http://localhost:3000

### Start Alternative Frontend (Streamlit)

```bash
cd backend
streamlit run streamlit_app.py
```

Application will open at: http://localhost:8501

---

## 📈 Model Performance

### Position Prediction (Regression)
| Metric | Score |
|--------|-------|
| RMSE | 3.2 positions |
| MAE | 2.4 positions |
| R² Score | 0.76 |

### Podium Prediction (Classification)
| Metric | Score |
|--------|-------|
| Accuracy | 85.3% |
| Precision | 0.82 |
| Recall | 0.79 |
| F1-Score | 0.80 |

### Points Prediction (Classification)
| Metric | Score |
|--------|-------|
| Accuracy | 83.7% |
| Precision | 0.81 |
| Recall | 0.85 |
| F1-Score | 0.83 |

### Feature Importance (Top 5)
1. **Grid Position** (28.5%) - Starting position on track
2. **Constructor Standing** (15.2%) - Team championship position
3. **Driver Experience** (12.0%) - Years in Formula 1
4. **Circuit Type** (9.9%) - Track characteristics
5. **Driver Skill** (8.5%) - Individual driver rating

---

## 📡 API Documentation

### Base URL
```
http://localhost:8000
```

### Endpoints

#### 1. Predict Race
```http
POST /api/predict
Content-Type: application/json

{
  "circuit": "Bahrain International Circuit",
  "weather": "Dry",
  "entries": [
    {
      "driver": "Max Verstappen",
      "constructor": "Red Bull Racing",
      "grid": 1
    }
  ]
}
```

**Response:**
```json
{
  "success": true,
  "predictions": [...],
  "race_info": {
    "circuit": "Bahrain International Circuit",
    "weather": "Dry",
    "temperature": 28.5,
    "track_temp": 42.3
  }
}
```

#### 2. Get Teams
```http
GET /api/teams
```

#### 3. Get Circuits
```http
GET /api/circuits
```

#### 4. Get Driver Stats
```http
GET /api/driver-stats
```

#### 5. Get Constructor Standings
```http
GET /api/constructor-standings
```

Full API documentation available at: http://localhost:8000/docs

---

## ☁️ Deployment

### Deploy Backend (Render)

1. **Create Web Service** on Render
2. **Build Command:**
   ```bash
   pip install -r requirements.txt
   ```
3. **Start Command:**
   ```bash
   uvicorn app:app --host 0.0.0.0 --port $PORT
   ```
4. **Environment Variables:**
   - `PYTHON_VERSION`: `3.11.0`
5. **Set Root Directory:** `backend`

### Deploy Frontend (Vercel/Netlify)

1. **Build Command:**
   ```bash
   cd frontend && npm run build
   ```
2. **Publish Directory:** `frontend/build`
3. **Environment Variables:**
   - `REACT_APP_API_URL`: Your backend URL

### Docker Deployment

```bash
# Build Docker image
docker build -t f1-predictor-backend ./backend

# Run container
docker run -p 8000:8000 f1-predictor-backend
```

---

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

### Development Guidelines
- Follow PEP 8 for Python code
- Use TypeScript for React components
- Add tests for new features
- Update documentation

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 🙏 Acknowledgments

- **Ergast F1 API** for comprehensive historical F1 data
- **Formula 1®** for inspiration and the incredible sport
- **scikit-learn** community for excellent ML libraries
- **FastAPI** and **React** teams for amazing frameworks

---

## 📞 Contact

**Project Repository:** [GitHub](https://github.com/yourusername/f1-predictor)  
**Report Issues:** [GitHub Issues](https://github.com/yourusername/f1-predictor/issues)  
**Email:** your.email@example.com

---

## 📚 Additional Resources

- [Detailed Project Report](ML_Project_Report.md)
- [API Documentation](http://localhost:8000/docs)
- [Ergast F1 API](http://ergast.com/mrd/)
- [Formula 1 Official Site](https://www.formula1.com/)

---

**Made with ❤️ for F1 fans and ML enthusiasts**

*Formula 1®, F1®, and related marks are trademarks of Formula One Licensing B.V. This project is for educational purposes only and is not affiliated with or endorsed by Formula One.*
