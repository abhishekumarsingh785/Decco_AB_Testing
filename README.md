# A/B Testing for Promotional In-App Notification

## Background

Decco, an online retailer, recently added a new product category, **Lamps**. To boost awareness and sales, Decco plans to use **in-app notifications** with promotional offers. However, they want to ensure this approach does not negatively impact app uninstallation rates, as customer lifetime value (LTV) from app users is significantly higher.

## Objective

The objective of this experiment is to determine if sending an in-app notification promoting the Lamp category leads to an increase in purchases from this category, while monitoring other important metrics like uninstall rate.

## Hypothesis

- **Null Hypothesis (H0):** Sending an in-app notification does not increase the transaction rate for Lamps.
- **Alternative Hypothesis (H1):** Sending an in-app notification increases the transaction rate for Lamps.

## Metrics

### Primary Metric:

- **Transaction Rate**: Percentage of users making a purchase.

### Secondary Metrics:

- **Purchase Value**: Revenue generated from purchases.
- **Uninstall Rate**: Percentage of users uninstalling the app after receiving the notification.

## Experiment Design

### Treatment and Control Groups:

- Users are randomly assigned to either the **treatment group** (receiving the in-app notification) or the **control group** (not receiving the notification).

### Key Variables:

- **Response Variables:**
  - `addtocart_flag`
  - `transaction_flag`
  - `purchase_value`
- **Baseline Variables:**
  - `active_6m`: User activity in the last 6 months.
  - `days_since`: Days since app installation.
- **Other Metrics:**
  - `uninstall_flag`

### Sample Size Calculation:

Using the `pwr` package in R, the minimum sample size was calculated based on:

- **Control transaction rate:** 10.1%.
- **Expected uplift:** 20%.
- **Significance level:** 0.05.
- **Power:** 0.8.

## Steps Taken in the Analysis

1. **Define the Hypothesis**:
   - Null Hypothesis (\(H_0\)): Sending an in-app notification does not increase the transaction rate for Lamps.
   - Alternative Hypothesis (\(H_1\)): Sending an in-app notification increases the transaction rate for Lamps.

2. **Define Metrics**:
   - **Primary Metric**: Transaction Rate (percentage of users making a purchase).
   - **Secondary Metrics**: Average Purchase Value and Uninstall Rate.

3. **Calculate Sample Size**:
   - Used the `pwr` package in R to determine the required sample size based on the expected uplift, control transaction rate, significance level, and power.

4. **Prepare the Dataset**:
   - Loaded `a_b_Test_Data.csv`.
   - Selected key variables: `active_6m`, `addtocart_flag`, `transaction_flag`, `purchase_value`, `uninstall_flag`, and `days_since`.
   - Summarized and inspected the dataset for completeness and potential issues.

5. **Perform Exploratory Data Analysis (EDA)**:
   - Plotted the distribution of `purchase_value` using `ggplot2`.
   - Explored relationships between key variables (optional based on dataset).

6. **Analyze Results**:
   - Calculated the difference in transaction rate between the treatment and control groups.
   - Measured secondary metrics: Average Purchase Value and Uninstall Rate for both groups.

7. **Interpret Results**:
   - Found that the transaction rate increased by 15% in the treatment group.
   - Observed an increase in uninstall rate from 2% to 4%.
   - Average Purchase Value was $45 for the treatment group compared to $38 for the control group.


## Conclusion

The experiment demonstrated a significant uplift in transaction rate after sending the in-app notification. However, this came at the cost of a higher uninstall rate, which doubled from **2%** to **4%**. While the campaign succeeded in increasing sales, the potential negative impact on customer retention needs to be carefully evaluated before implementing such notifications broadly.

