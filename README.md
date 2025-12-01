# 🏡 Airbnb Availability Prediction — Hackathon A1  

This project builds an end-to-end data pipeline to prepare a unified ML-ready dataset for predicting whether an Airbnb listing will be **available on a given date**.  
We work with InsideAirbnb data for one city, consisting of:

- calendar.csv  
- listings.csv  
- reviews.csv  

The assignment emphasizes:
- Good Git & GitHub practice  
- Clear and meaningful commits  
- Balanced teamwork using feature branches  
- Exploratory data analysis with thoughtful reasoning  
- Strong feature engineering  
- A clean, unified dataset ready for future machine learning  

---

## 👥 Team & Responsibilities

Each teammate prepared one dataset and contributed to the final merge.

| Member        | Branch      | Responsibilities |
|--------------|-------------|------------------|
| **Max Voss**                  | `feat/max`                    | Support in Calendar dataset: cleaning, temporal features and design of the read.me |
| **Jan Philipp Gnau**          | `feat/janp`                   | Listings dataset: property & host features, categorical encoding, missing-value strategy |
| **Mohamaed Aymen Elmezouari** | `feat/mohamedaymen`  | Reviews dataset: review aggregates, recency metrics, optional text/NLP features |
| **Lorenzo Giovanni Costa**    | `feat/lorenzo`          | Reviews dataset: review aggregates, recency metrics, optional text/NLP features |
| **Alessandro Mezzanotte**     | `feat/alessandro`        | Calendar dataset: cleaning, temporal features, booking horizon, rolling booking rate, price features |
| **All**                       | `main`      | Final dataset merge, QA checks, documentation |

---

## 📁 Project Structure
hackathon_a1/
│
├── data/
│ ├── calendar.csv
│ ├── listings.csv
│ ├── reviews.csv
│ └── calendar_prepared.csv
│
├── H1.ipynb
├── README.md
├── environment.yml
└── .gitignore

---

## 🔄 Workflow Overview

### 1. Load & Inspect Raw Data
We begin by:
- Checking data types  
- Inspecting missing values  
- Detecting duplicates  
- Understanding data distributions  

---

### 2. Feature Engineering (per dataset)

#### Calendar Dataset (Max)
Engineered features:
- `available_flag` (1 = available, 0 = booked)  
- Cleaned price fields: `price_num`, `log_price`  
- Temporal features: `year`, `month`, `day_of_week`, `week_of_year`, `is_weekend`, `is_high_season`  
- Booking horizon feature: `days_ahead`  
- Rolling demand trend: `booked_rate_last7`  
- Price competitiveness: `price_relative = price_num / median_price_per_listing`  
- Exported cleaned file: `calendar_prepared.csv`

#### Listings Dataset
- Host and property characteristics  
- Neighborhood grouping  
- Missing-value treatment  
- Encoding categorical variables  

#### Reviews Dataset
- Aggregated review counts  
- Review recency  
- Optional sentiment/text-derived metrics  

---

### 3. Unified Dataset Assembly

Final merge:
calendar_prepared

listings_prepared

reviews_prepared
→ unified_ml_dataset

Join keys:
- `listing_id`
- `date`

The final dataset contains:
- Target (`available_flag`)  
- Temporal and price features  
- Host and property characteristics  
- Review-based features  

---

## 📊 Exploratory Data Analysis (EDA)

Insights include:
- Target imbalance in `available_flag`  
- Weekly patterns (weekend vs weekday availability)  
- Monthly/seasonal variation  
- Price elasticity (higher price → lower availability)  
- Combined weekly + seasonal patterns (month × weekday heatmap)  

Each visualization answers a clear analytical question to guide feature engineering.

---

## 🔧 Environment Setup
conda env create -f environment.yml
conda activate hackathon_env

---

## 🔐 Git & Collaboration Workflow

We follow a structured branching workflow:

- One feature branch per teammate  
- Frequent, meaningful commits  
- Pull Requests into `main`  
- `.gitignore` used to exclude unnecessary files  
- Clean project history reflecting collaboration  

Example workflow:
git checkout feat/max
git add README.md H1.ipynb
git commit -m "Add calendar EDA and README"
git push origin feat/max

---

## 📦 Final Deliverables

- Complete notebook: `H1.ipynb`  
- Cleaned & engineered calendar dataset  
- Listings & Reviews engineered datasets  
- Unified ML-ready dataset  
- README.md  
- environment.yml  

---





