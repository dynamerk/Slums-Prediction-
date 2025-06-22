📈 Future Slum Growth Prediction — Kibera & Katanga

This project uses linear regression to analyze and predict land use and land cover (LULC) changes in two major urban slums: Kibera in Nairobi, Kenya, and Katanga in Kampala, Uganda. It forecasts future slum growth based on historical LULC data and visualizes trends with clear comparative plots.

🎯 Objective
To model and predict LULC change (2000–2030) focusing on:

Built-up Area (BA)

Bare Land (BL)

Vegetation Cover (VC)

Water Density (WD)

in Kibera and Katanga using historical data and regression analysis.

🧠 Aim of the Project
Understand historical trends of LULC change in slum areas

Predict future LULC proportions through 2030

Inform urban planning, slum upgrading, and environmental management

Provide a reproducible tool for:

Urban planners

GIS analysts

Environmental researchers

📊 Data Requirements
Parameter	Description
Years	2000, 2003, ..., 2024 (historical data points)
LULC Classes	BL, BA, VC, WD percentages
Locations	Kibera (Nairobi), Katanga (Kampala)

Step-by-Step Workflow
Import Libraries
Required: matplotlib, numpy, pandas, scikit-learn

Define Input Data
Historical LULC percentages for each class and year for both locations

Train Linear Regression Models
Fit models for each LULC class using historical years as independent variables

Generate Predictions
Predict LULC percentages for the year 2030

Visualization
Create grouped plots showing observed data, trendlines, and 2030 predictions

Save Outputs
Export plots as .png images for reporting and presentation

Example to Save Plot Image
python code: 
plt.savefig("Kibera_2030_predictions.png", dpi=300)
print("Plot saved as Kibera_2030_predictions.png")
