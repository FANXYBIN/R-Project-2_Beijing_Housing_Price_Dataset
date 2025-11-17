# R-Project 2: Beijing Housing Price Analysis & Hypothesis Testing (R)

This project analyzes **housing prices in Beijing** using R.  
The workflow includes extensive **data cleaning**, **EDA visualizations**, **correlation analysis**, and **hypothesis testing** to understand the key factors influencing house prices.

* **Dataset:** Beijing Housing Price (Kaggle – 318,851 observations, 26 variables)  
* **Tools:** R, tidyverse, ggplot2, corrplot, dplyr  
* **Techniques:** Data cleaning, variable recoding, histograms, correlation analysis, boxplots, scatterplots, t-tests  
* **Goal:** Explore the structure of Beijing’s housing market and validate insights using statistical hypothesis testing.

---

### 📁 Dataset Overview

The dataset contains housing transaction records from Beijing, including:

- Pricing (totalPrice, price per m²)  
- House characteristics (square, rooms, floor, buildingType, structure)  
- Location information (Lng/Lat, district, communityAverage)  
- Accessibility indicators (elevator, subway)

<div align="center">
  <img src="images/beijing_dataset_structure.png" width="600"/>
  <p><em>Dataset structure overview.</em></p>
</div>

---

### 🧹 Data Cleaning & Preparation

From the raw dataset (318,851 rows), the following steps were taken:

#### ✔ Selected Relevant Variables  
(id, tradeTime, totalPrice, price, square, rooms, floor, communityAverage, elevator, subway, buildingType, buildingStructure)

#### ✔ Converted Categorical Variables to Factors  
Based on dataset documentation:

- **buildingType** → Tower, Bungalow, Plate/Tower, Plate  
- **buildingStructure** → Mixed, Brick/Wood, Steel, Concrete, etc.  
- **elevator** → 0/1  
- **subway** → 0/1  

<div align="center">
  <img src="images/beijing_datatype_before.png" width="600"/>
  <p><em>Original column types.</em></p>
</div>

<div align="center">
  <img src="images/beijing_datatype_after.png" width="600"/>
  <p><em>Cleaned factor levels.</em></p>
</div>

#### ✔ Removed Missing Values  
2,580 rows containing NA were removed.

<div align="center">
  <img src="images/beijing_na_count.png" width="600"/>
  <p><em>NA count before filtering.</em></p>
</div>

#### ✔ Selected Numerical Features for Correlation  
(totalPrice, price, square, rooms, bathRoom, drawingRoom, communityAverage, floor)

<div align="center">
  <img src="images/beijing_numerical_df.png" width="600"/>
  <p><em>Numerical dataset for correlation analysis.</em></p>
</div>

---

### 📊 Exploratory Data Analysis (EDA)

#### 📈 Histograms: Price & Total Price  
Both price per m² and total price show **right-skewed distributions**, with most prices concentrated between 20,000–60,000.

<div align="center">
  <img src="images/beijing_hist_price.png" width="600"/>
  <p><em>Histogram of price per m².</em></p>
</div>

<div align="center">
  <img src="images/beijing_hist_totalprice.png" width="600"/>
  <p><em>Histogram of total price.</em></p>
</div>

---

### 🔗 Correlation Analysis

Strong positive correlations were found among:

- **totalPrice** ↔ price, square, communityAverage  
- **square** ↔ rooms, bathRoom, drawingRoom  

<div align="center">
  <img src="images/beijing_cor_matrix.png" width="600"/>
  <p><em>Correlation matrix.</em></p>
</div>

<div align="center">
  <img src="images/beijing_corrplot.png" width="600"/>
  <p><em>Corrplot visualization.</em></p>
</div>

---

### 📦 Boxplots: Price by Categorical Variables

#### Building Type  
🏆 Bungalows are the most expensive building type.

<div align="center">
  <img src="images/beijing_box_buildingType.png" width="600"/>
  <p><em>Price vs. Building Type.</em></p>
</div>

#### Building Structure  
Steel/Concrete buildings tend to be more expensive.

<div align="center">
  <img src="images/beijing_box_buildingStructure.png" width="600"/>
  <p><em>Price vs. Building Structure.</em></p>
</div>

#### Elevator  
Homes with elevators → significantly higher prices.

<div align="center">
  <img src="images/beijing_box_elevator.png" width="600"/>
  <p><em>Price vs. Elevator.</em></p>
</div>

#### Subway  
Homes near subway stations → higher average prices.

<div align="center">
  <img src="images/beijing_box_subway.png" width="600"/>
  <p><em>Price vs. Subway Access.</em></p>
</div>

---

### 🔍 Scatterplots

#### Price vs Total Price (by building type & structure)

<div align="center">
  <img src="images/beijing_scatter1.png" width="600"/>
  <p><em>Price vs total price by building type.</em></p>
</div>

<div align="center">
  <img src="images/beijing_scatter2.png" width="600"/>
  <p><em>Price vs total price by building structure.</em></p>
</div>

#### Group-based Regression Slopes

<div align="center">
  <img src="images/beijing_scatter_group1.png" width="600"/>
  <p><em>Square vs Price — grouped by building type.</em></p>
</div>

<div align="center">
  <img src="images/beijing_scatter_group2.png" width="600"/>
  <p><em>Square vs Price — grouped by building structure.</em></p>
</div>

---

### 📅 Average Housing Price by Month

Shows seasonal patterns & monthly variation in housing prices.

<div align="center">
  <img src="images/beijing_monthly_avg_price.png" width="600"/>
  <p><em>Monthly average housing prices.</em></p>
</div>

---

### 🧪 Hypothesis Testing

#### **Question 1:**  
Is the sample mean of housing prices equal to 43,549.6?

Result: **Fail to reject H₀**  
➡ Price is statistically similar to the given value.

<div align="center">
  <img src="images/beijing_ttest_q1.png" width="600"/>
</div>

---

#### **Question 2:**  
Is there a difference in price between **Bungalows** vs **Towers**?

Result: **Reject H₀**  
➡ Bungalows significantly more expensive.

<div align="center">
  <img src="images/beijing_ttest_q2.png" width="600"/>
</div>

---

#### **Question 3:**  
Are 2016 prices greater than 2017 prices?

Result: **Reject H₁**  
➡ 2017 prices are significantly higher.

<div align="center">
  <img src="images/beijing_ttest_q3.png" width="600"/>
</div>

---

### 🧠 Key Insights

- Housing prices in Beijing are strongly influenced by **square meters**, **community average price**, and **building structure**.  
- Homes near subways or with elevators have higher valuations.  
- Bungalows are the most expensive housing type.  
- Prices increased **significantly** from 2016 → 2017.  
- All hypotheses were validated through t-tests (one-sample and two-sample).

---

### 🧠 Skills Demonstrated
- Data wrangling and cleaning in R  
- Visualization with ggplot2 and corrplot  
- Statistical hypothesis testing (one-sample, two-sample t-tests)  
- Interpretation of descriptive and inferential statistics  
- Exploratory data analysis workflows  

