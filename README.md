# A/B Test Analysis & Automation (Python + SQL + Tableau)

## Project Overview
This project automates the analysis of A/B test results for an e-commerce platform. It moves beyond basic Excel calculations by using **Python** for statistical rigor and **SQL** for efficient data extraction. The final results are visualized in an interactive **Tableau Dashboard**.

**View the Dashboard:** [Tableau Public](https://public.tableau.com/app/profile/artemii.zubriichuk/viz/ProjectABTesting/Dashboard1)

## Objectives
* **Automate** the extraction and processing of raw session/event data from Google BigQuery.
* **Calculate** key conversion metrics: `add_payment_info`, `add_shipping_info`, `begin_checkout`, `new_account`.
* **Validate** results using statistical hypothesis testing (**Z-test**) to distinguish real impact from random noise.
* **Visualize** the results clearly for stakeholders.

## Tech Stack
* **SQL (BigQuery):** Complex queries using CTEs and UNION ALL to aggregate sessions, orders, and events.
* **Python (Pandas, Statsmodels):**
    * Data cleaning and aggregation.
    * Statistical significance calculation (Z-test for proportions, p-value, confidence intervals).
* **Tableau:** Visualization of Lift% and Statistical Significance.
* **Google Colab:** Cloud-based environment for executing the pipeline.

## Methodology
1.  **Data Extraction:** Wrote a query to fetch session logs, filtering for 4 key funnel steps.
2.  **Aggregation:** Grouped data by `Test ID` and `Test Group` (Control vs. Variant) to ensure correct statistical comparison.
3.  **Statistical Analysis:**
    * Applied **Z-test for proportions** (95% confidence level, $\alpha = 0.05$).
    * Calculated **Lift** (Relative difference between Test and Control).
4.  **Result:** Flagged metrics as `Significant` (True/False) based on p-value.

## Key Findings (Example from Test 1)
 **Add Payment Info:** +12.5% Lift (Statistically Significant)
 **Begin Checkout:** +6.2% Lift (Statistically Significant)
 **New Account:** No significant change detected.

## Repository Structure
* `notebook.ipynb`: The main Google Colab notebook containing SQL queries and Python logic.
* `abtest_results.csv`: The processed dataset used for visualization.
