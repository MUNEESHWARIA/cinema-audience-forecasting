# 🎬 Cinema Audience Forecasting

**Predicting daily theatre attendance using machine learning — so cinema operators can plan smarter instead of guessing.**

---

## Why I built this

Cinema operators deal with a surprisingly common problem: they don't know how many people are going to show up on any given day. Too many staff on a slow Tuesday, not enough food stocked for a packed Saturday — it adds up. Most of the time, decisions around scheduling, inventory, and promotions are made based on gut feel or last year's numbers.

I wanted to see if I could build something that actually helps with that. This project builds a forecasting model that predicts daily audience counts across multiple theatre locations using historical attendance data and time-based patterns. The goal is simple: give operations teams a reliable number to plan around.

---

## What the project does

At its core, this is a **demand forecasting problem**. Given past attendance data and date-related features (day of the week, month, season, etc.), the model predicts how many people are likely to show up at a theatre on any given day.

The output can be used to:
- Plan how many staff to schedule
- Stock the right amount of F&B inventory
- Decide when to run promotions
- Spot patterns across different locations

---

## Dataset

The dataset contains daily audience count records across multiple theatre locations. There's no single magic column that predicts everything — the signal lives in the time patterns, which is why feature engineering was the most important part of this work.

| Field | Description |
|---|---|
| Date | The specific day of attendance |
| Location | Theatre branch/outlet |
| Audience Count | Number of attendees (the target variable) |
| Engineered Features | Day of week, week number, month, quarter, is_weekend flag |

---

## Tools used

- **Python** — data processing, modelling, and visualisation
- **Pandas & NumPy** — cleaning and transforming the data
- **Scikit-learn** — building and evaluating the Random Forest model
- **Matplotlib & Seaborn** — charts and visual analysis
- **Jupyter Notebook** — development and documentation

---

## How I approached it

**Step 1 — Explore the data**
Before building anything, I spent time understanding the data: what it looked like, where the gaps were, and what patterns were already visible just from plotting the raw numbers.

**Step 2 — Clean and prepare**
Standardised the date formats, handled missing values, and made sure each location's records were consistent before doing anything else.

**Step 3 — Feature engineering**
This was the most impactful step. Raw dates don't tell a model much. So I extracted features like day of week, month, quarter, weekend flag, and week number — things that actually carry meaning when it comes to predicting footfall.

**Step 4 — Build and train the model**
I used a **Random Forest Regressor**. It handles non-linear patterns well, doesn't need a lot of tuning to get reasonable results, and is easy to interpret — which matters when you're trying to explain predictions to a non-technical team.

I split the data chronologically (not randomly) to simulate how the model would actually be used in practice — train on the past, predict the future.

**Step 5 — Evaluate**
Used **Mean Absolute Error (MAE)** as the main metric because it's the most intuitive: it tells you, on average, how far off the predictions are in actual audience count units. The model tracked the real attendance trends well, including the weekly ups and downs and seasonal spikes.

**Step 6 — Visualise and interpret**
Built charts to show actual vs. predicted counts, which features mattered most, and how attendance varied across days and locations.

---

## What I found

- **Weekends drive significantly higher attendance** — Friday through Sunday consistently outperform the rest of the week, sometimes by 30–40%. Day of week turned out to be the strongest predictor by a wide margin.
- **Mondays are reliably the slowest day** across almost all locations. That's a pattern that can directly inform staffing decisions.
- **Q4 and school vacation periods are peak seasons.** Attendance spikes are predictable enough that operators could start planning 2–3 weeks ahead.
- **Different locations behave differently.** A blanket strategy doesn't work well — each location has its own rhythm, and the model picks that up.
- **Weekly cycles are very stable**, which is actually good news for forecasting. It means the model doesn't need years of data to start being useful.

---

## Model performance

| Detail | Info |
|---|---|
| Model | Random Forest Regressor |
| Evaluation Metric | Mean Absolute Error (MAE) |
| Split Method | Chronological train/test (no data leakage) |
| Result | Predictions closely tracked real attendance trends across locations and time periods |

The model isn't perfect — no forecasting model is — but the predictions are within a margin that makes them genuinely useful for day-to-day planning decisions.

---

## Visualisations

- **Actual vs. Predicted (line chart)** — shows how closely the model follows real attendance over time. Peaks and troughs line up well.
- **Feature importance (bar chart)** — day of week and month come out on top, which aligns with what the data analysis showed.
- **Attendance by day of week (box plot)** — makes the Friday–Sunday effect very clear at a glance.
- **Monthly trend chart** — shows the seasonal pattern across the year, including the Q4 surge.
- **Location comparison (bar chart)** — highlights how much footfall varies between branches, useful for resource allocation decisions.

---

## Business impact

If I were presenting this to an operations team at a cinema chain, here's what I'd highlight:

- **Smarter staffing:** Instead of scheduling based on last week or intuition, managers can use predicted attendance to right-size their teams. On low-traffic days, that means fewer overstaffing costs. On peak days, it means being prepared.
- **Better inventory management:** Concession stands can stock based on expected footfall rather than average assumptions. Less waste on slow days, fewer stockouts on busy ones.
- **Targeted promotions:** When you know Monday is always slow, you can run a Monday deal to bring people in — instead of running blanket discounts that eat into margins on days people were already going to come.
- **Multi-location planning:** Regional managers can see which locations are expected to spike and shift floating staff or resources accordingly.

This is the kind of analysis that typically lives in a company's BI or operations analytics team. The pipeline I've built here could be adapted and plugged into an existing reporting workflow fairly quickly.

---

## What I'd improve next

- **Add external data** — new film release dates, public holidays, and local events are major footfall drivers that aren't in the current dataset. Adding them would meaningfully improve accuracy.
- **Try XGBoost or LightGBM** — Random Forest is a solid baseline, but gradient boosting models often squeeze out better performance on tabular data with enough tuning.
- **Explore time-series specific models** — Facebook's Prophet or an LSTM network could capture long-term trends and seasonality more explicitly.
- **Build a simple dashboard** — a Streamlit app where operations staff can select a location and date range and see predicted attendance without opening a notebook.
- **Extend to weekly/monthly forecasts** — single-day predictions are useful, but 7-day and 30-day rolling forecasts would be more practical for planning cycles.

---

## Conclusion

This project started with a real operational question: *how do you make better decisions about a cinema when you don't know how many people are coming?* The answer turned out to be mostly in the data that was already there — specifically in the time patterns that repeat week after week.

The model works, the insights are clear, and the logic behind it is simple enough to explain to a non-technical stakeholder. That last part matters just as much as the accuracy.

---

## Resume highlights

> *Built a machine learning pipeline in Python to forecast daily cinema attendance across multiple locations, using Random Forest regression and time-based feature engineering — with direct applications in staffing, inventory, and revenue planning.*

> *Identified key demand drivers (day of week, seasonality, location) through EDA and predictive modelling, translating model outputs into operational recommendations for theatre management teams.*

> *Designed a chronological train/test split strategy to prevent data leakage, ensuring model evaluation reflected realistic deployment conditions.*

---

## Author

**Muneeshwari N**
[GitHub](https://github.com/MUNEESHWARIA)

---

`Python` `Pandas` `NumPy` `Scikit-learn` `Random Forest` `Matplotlib` `Seaborn` `Feature Engineering` `EDA` `Time-Series` `Demand Forecasting` `Machine Learning`
