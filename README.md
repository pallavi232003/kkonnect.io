
**Approach**
1. DATA GENERATION

    Since the assignment required generating the dataset, a synthetic dataset of 150 CNC-machined parts was created using domain logic:
    Randomly generated dimensions (Length_mm, Width_mm, Height_mm)
    Computed Volume_mm3
    Added realistic noise to calculate Estimated_Cost_USD and Estimated_Time_min based on volume, feature count, and material type.

3. DATA CLEANING
 
   The data was loaded into a Pandas DataFrame. Checks for null values, data types, and duplicates were done. No cleaning issues were found due to clean synthetic data.

5. Feature Engineering

   Two key features were engineered:
   Cost_per_mm3: Normalized cost based on part size
   SA_to_Volume: Surface-area-to-volume ratio to simulate machining complexity

7. EXPLORATORY DATA ANALYSIS (EDA)
 
   Various plots were used to uncover relationships:
   Boxplot: Cost vs Material
   Scatterplot: Cycle time vs Feature count
   Heatmap: Correlation between numeric features

8. Model Training

    Used RandomForestRegressor to predict Estimated_Cost_USD
    One-hot encoding for Material
    Model trained using train_test_split
    Evaluated with MAE and RMSE
    Feature importances were visualized




**Summary of Results**

Model: Random Forest Regressor

Target: Estimated_Cost_USD

Train/Test Split: 80/20

Evaluation Metrics:

   MAE (Mean Absolute Error): ~150 USD
   RMSE (Root Mean Squared Error): ~187 USD

   
Top Predictors (based on feature importance):

   Volume_mm3
   Feature_Count
   Cost_per_mm3
Material_Brass, Material_Titanium



 **Key Insights**
1. Volume and Feature Count are Major Cost Drivers
   
     Larger parts and more machining features directly increase both cycle time and cost.
     Volume shows a strong positive correlation with cost (from the heatmap and scatterplot).

2.Material Significantly Affects Cost

   Titanium and Brass are consistently more expensive, seen clearly in the cost vs material boxplot.
     Lighter or easier-to-machine materials like Plastic tend to have lower costs.

3.Surface-Area-to-Volume Ratio Matters

   Parts with high SA/V ratios are likely more intricate and require more tool paths or changes, affecting cost and 
      time — this insight can help in further refining future models.
   
