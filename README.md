# Airbnb Availability Prediction — Hackathon A1

This project develops an end-to-end data pipeline to create a unified ML-ready dataset for predicting whether an Airbnb listing will be available on a given date. The project uses InsideAirbnb data consisting of calendar.csv.gz, listings.csv.gz, and reviews.csv.gz.

---

## Team Responsibilities

| Member | Branch | Responsibilities |
|--------|--------|-------------------|
| **Max Voss** | `feat/max` | Support in Calendar dataset: cleaning, temporal features and design of the read.me |
| **Jan Philipp Gnau** | `feat/janp` | Listings dataset: property & host features, categorical encoding, missing-value strategy |
| **Mohamed Aymen Elmezouari** | `feat/mohamedaymen` | Reviews dataset: review aggregates, recency metrics, optional text/NLP features |
| **Lorenzo Giovanni Costa** | `feat/lorenzo` | Reviews dataset: review aggregates, recency metrics, optional text/NLP features |
| **Alessandro Mezzanotte** | `feat/alessandro` | Calendar dataset: cleaning, temporal features, booking horizon, rolling booking rate, price features |
| **All** | `main` | Final dataset merge, QA checks, documentation |

---

## Project Structure

```
hackathon_a1/
│
├── data/
│   ├── calendar.csv.gz
│   ├── listings.csv.gz
│   ├── reviews.csv.gz
│
├── notebooks/
│   ├── data_cleaning.ipynb          ← main full pipeline: cleaning + feature engineering + merging
│   ├── data_analysis.ipynb          ← exploratory analysis & visual insights
│   ├── Data_cleaning_Listings.ipynb ← listings-specific preprocessing
│
├── .ipynb_checkpoints/
│
├── H1.ipynb
├── README.md
├── environment.yml
├── .gitignore
├── calendar.csv.gz
├── listings.csv.gz
└── Untitled.ipynb
```

---

## Workflow Overview

### 1. Raw Data Inspection  
Performed in data_analysis.ipynb and H1.ipynb:
- Inspect column types  
- Detect missing values  
- Identify duplicates  
- Explore initial patterns (availability, prices)  

---

### 2. Data Cleaning & Feature Engineering  
Implemented in notebooks/data_cleaning.ipynb.

#### Calendar dataset  
Features created:
- available_flag  
- price_num, log_price  
- year, month, day_of_week, week_of_year  
- is_weekend, is_high_season  
- days_ahead  
- booked_rate_last7  
- price_relative  

#### Listings dataset  
Prepared in Data_cleaning_Listings.ipynb:
- Host features  
- Property characteristics  
- Neighbourhood fields  
- Missing value handling  
- Categorical encoding  

#### Reviews dataset  
Processed inside the main cleaning pipeline:
- Review counts  
- Review recency  
- Optional text-based features  

---

### 3. Unified Dataset Assembly  
Inside data_cleaning.ipynb, the datasets are merged:

```
calendar_prepared
+ listings_prepared
+ reviews_prepared
→ unified_ml_dataset
```

Merged using listing_id and date.

Final dataset includes:
- Availability target  
- Temporal features  
- Host & property information  
- Price features  
- Review indicators  
- Demand trends  

---

## Exploratory Data Analysis (EDA)

Performed in data_analysis.ipynb:
- Weekly availability cycles  
- Seasonal booking trends  
- Price sensitivity  
- Heatmaps of weekday × month patterns  
- Minimum-night rules  

---

## Environment Setup

```
conda env create -f environment.yml
conda activate hackathon_env
```

---

## Git & Collaboration Workflow

```
git checkout feat/max
git add README.md
git commit -m "Update README with team and structure"
git push origin feat/max
```

Merging:

```
git checkout main
git pull origin main
git merge feat/max
git push origin main
```

Workflow principles:
- Dedicated feature branches  
- Clear commit messages  
- Pull requests into main  
- Conflict resolution  
- .gitignore coverage  

---

## Final Deliverables

- Unified ML-ready dataset  
- Cleaning pipeline → notebooks/data_cleaning.ipynb  
- Listings cleaning → Data_cleaning_Listings.ipynb  
- EDA notebook → data_analysis.ipynb  
- README  
- environment.yml  

---

## Acknowledgments

Thanks to InsideAirbnb for open data and ESADE faculty for providing the Git-based collaboration framework.





