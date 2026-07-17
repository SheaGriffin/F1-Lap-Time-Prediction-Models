# F1 Lap Time Prediction Models

In this project, I built two sets of Formula 1 lap time prediction models.

- **Pace Degradation Model:** A set of linear regression models (one for each track/tire compound pair) that predict change in lap time based on tire age.
- **Driver XGBoost Model:** A set of XGBoost models (one for each driver/track pair) that predict change in lap time based on telemetry from the current and previous two laps.

<img width="614" height="559" alt="Model Overview" src="https://github.com/user-attachments/assets/d3ec034b-e40e-4104-9cf1-cde45ced569f" />

<br>

## Models Evaluated

I built models for the following drivers and tracks:

### Drivers
- Max Verstappen
- Pierre Gasly
- Lewis Hamilton
- Charles Leclerc
- Lando Norris

### Tracks
- Abu Dhabi
- Bahrain
- Mexico

<br>

## Testing Results
I tested both models on 2024 sessions

### Both models performed similarly well on 2024 lap data 
- The Pace Degradation model predicted lap time within .284 seconds on average, while the XGBoost model predicted lap time within .289 seconds on average. 
### The two models' performances were highly correlated across different races 
-	PaceDeg and XGBoost MAE had a Pearson correlation of 0.91 across all 15 sessions
- Both PaceDeg and XGBoost had their best performance in the Lando Norris Bahrain session with MAEs of .144 and .179 respectively
- Both PaceDeg and XGBoost had their worst performance in the Pierre Gasly Mexico session with MAEs of .440 and .389 respectively
### Efforts to ensemble the two models had no effects
- Adding PaceDeg model predictions as a feature to the XGBoost model had no impact on performance
- A meta learner that assigns linear weights to the two models gave all weight to the XGBoost model
- The high correlation in performance and the ineffectiveness of ensembling both suggest that, despite having very different model architectures, the models capture the same signals from their respective data sources
