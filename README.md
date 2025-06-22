# 📈 Future Slum Growth Prediction — Kibera & Katanga

This project uses **linear regression** to analyze and predict land use and land cover (LULC) changes in two major urban slums: **Kibera** in Nairobi, Kenya, and **Katanga** in Kampala, Uganda. It forecasts future slum growth based on historical LULC data and visualizes trends with clear comparative plots.

---

## 🎯 Objective

To model and predict LULC change (2000–2030) focusing on:

- Built-up Area (BA)  
- Bare Land (BL)  
- Vegetation Cover (VC)  
- Water Density (WD)  

in Kibera and Katanga using historical data and regression analysis.

---

## 🧠 Aim of the Project

- Understand historical **trends** of LULC change in slum areas  
- Predict **future LULC proportions** through 2030  
- Inform **urban planning**, **slum upgrading**, and **environmental management**  
- Provide a reproducible tool for:  
  - Urban planners  
  - GIS analysts  
  - Environmental researchers  

---

## 📊 Data Requirements

| Parameter              | Description                        |
|-----------------------|----------------------------------|
| Years                 | 2000, 2003, ..., 2024 (historical data points) |
| LULC Classes          | BL, BA, VC, WD percentages       |
| Locations             | Kibera (Nairobi), Katanga (Kampala) |

---

## Step-by-Step Workflow

1. **Import Libraries**  
   Required: `matplotlib`, `numpy`, `pandas`, `scikit-learn`

2. **Define Input Data**  
   Historical LULC percentages for each class and year for both locations  

3. **Train Linear Regression Models**  
   Fit models for each LULC class using historical years as independent variables  

4. **Generate Predictions**  
   Predict LULC percentages for the year 2030  

5. **Visualization**  
   Create grouped plots showing observed data, trendlines, and 2030 predictions  

6. **Save Outputs**  
   Export plots as `.png` images for reporting and presentation  

---

## Example Code Snippet

```python
import matplotlib.pyplot as plt
import numpy as np
from sklearn.linear_model import LinearRegression

# for Kibera slum - Built-up Area (BA)
years = np.array([2000, 2003, 2006, 2009, 2012, 2015, 2018, 2021, 2024]).reshape(-1, 1)
ba_percent = np.array([82.7, 86.7, 91.2, 93.0, 95.1, 95.8, 96.0, 94.7, 93.0])

model = LinearRegression()
model.fit(years, ba_percent)
year_2030 = np.array([[2030]])
prediction_2030 = model.predict(year_2030)[0]

plt.plot(years, ba_percent, 'o-', label='Observed')
plt.plot(years, model.predict(years), '--', label='Trendline')
plt.plot(2030, prediction_2030, 'ro', label=f'2030 Prediction: {prediction_2030:.2f}%')
plt.title("Built-up Area (BA) in Kibera (2000-2030)")
plt.xlabel("Year")
plt.ylabel("Built-up Area (%)")
plt.legend()
plt.show()
