# Market Basket Analysis for E-commerce Cosmetics Retail


## 1. Business context

The Marketing team has observed that customers frequently purchase multiple products within the same transaction. However, the current product recommendation system does not effectively leverage these purchasing patterns, resulting in missed opportunities for cross-selling and revenue growth.

Management would like to better understand customer buying behavior by analyzing historical transaction data to identify product groups that are commonly purchased together. The insights generated will be used to improve product recommendations, promotional campaigns, and online storefront merchandising.

---

## 2. Analytical objectives

This project applies Market Basket Analysis (MBA) to uncover purchasing patterns and translate them into actionable recommendations that can improve cross-selling performance, Average Order Value (AOV), and customer experience.

* Identify product combinations with the strongest purchase associations.
* Understand customer purchasing behavior and underlying needs.
* Detect cross-category shopping patterns.
* Provide actionable recommendations for:
  * Product recommendations
  * Bundling strategies
  * Cross-selling campaigns
  * Customer targeting

---

## 3. Analytical Workflow

Transaction Data → Basket Transformation → Frequent Itemsets (Apriori) → Association Rules → Rule Evaluation → Action Segmentation → Recommendation Framework

---
## 4. Dataset overview

The analysis is based on 25,728 transaction baskets collected between 2020 and 2023.

The product catalog contains approximately 20,000 SKUs, grouped into 17 subcategories across 5 main categories:

* Face Care
* Hair Care
* Body Care
* Makeup
* Home & Accessories

*To balance behavioral insights and analytical reliability, the analysis was conducted at the **Subcategory level** rather than the SKU level.*

This approach provides:

* Better representation of customer needs.
* More interpretable purchasing patterns.
* Reduced SKU fragmentation caused by brand, color, size, and fragrance variations.

---

## 5. Methodology

### Association Rule Mining

Applied the Apriori algorithm at the Subcategory level to identify purchasing associations across product groups.

| Metric | Business Meaning	| Threshold |
|---|---|---|
| Support |	% of baskets containing both product groups |	≥ 0.1% |
| Confidence | Probability of purchasing product group B after purchasing A	| ≥ 10% |
| Lift | Association strength beyond random chance | ≥ 1.2 |

### Other terminologies

* **Antecedents:** The product category (or categories) that we suppose customers have already purchased.
* **Consequents:** The product category (or categories) that are frequently purchased together with the antecedents.
* **Association Rule:** A purchasing pattern that links antecedents to consequents, showing what customers are likely to buy next.

---

## 6. Key results

* 25,728 baskets analyzed
* ~20,000 SKUs evaluated
* 2,004 association rules identified
* 17 subcategories analyzed
* 4 recommendation action groups created

---

## 7. Final Deliverables

* Market Basket Analysis Notebook
* Association Rule Dataset
* Power BI Recommendation Dashboard
* Business Recommendations

---

## 8. MBA Bubble Chart, Association Rules Matrix & Action Framework

### Strong Associations Are Not Necessarily the Most Scalable Opportunities

***Finding:** Rules with the strongest associations (highest lift values) are distributed across all support-confidence quadrants. This suggests that association strength is largely independent of rule popularity and conversion likelihood in the current dataset.*

<img src='images/Meaningful association rules.png' width=800>


### Association Rules Action Matrix

***Implication:** Lift was used as a qualification criterion to ensure that only rules exhibiting meaningful associations beyond random chance were considered. Subsequent action segmentation was performed using Support and Confidence, representing market reach and conversion potential, respectively.*

<img src='images/Association Rules Action Matrix.png' width=800>


#### Action Framework

| Action Group | Determination | Interpretation |Recommended Action |
|---|---|---|---|
| Scale | Support ≥ 0.002 & Confidence ≥ 0.1692 | High-tier Support and Confidence | Product-page recommendations, bundles, promotions |
| Reach | Support ≥ 0.002 & Confidence ≤ 0.1692 |	High-tier Support but low-tier Confidence | Awareness campaigns, category-level promotions, A/B testing |
| Precision	| Support ≤ 0.002 & Confidence ≥ 0.1692 | Low-tier Support but high-tier Confidence |Personalized recommendations, CRM journeys, targeted cross-selling |
| Monitor	| Support ≤ 0.002 & Confidence ≤ 0.1692 | Low-tier Support and Confidence | Periodic review |


---

## 9. Executive Summary

### Key findings

* SKU-level Market Basket Analysis was ineffective due to the highly fragmented nature of cosmetic products.
* Subcategory-level analysis identified 2,004 meaningful association rules.
* Customer purchases are primarily driven by two needs:
   * Holistic Self-Care
   * At-Home Wellness

> Strong associations are not concentrated within a single support-confidence segment, indicating that no single metric is sufficient for prioritization.

* An Action Framework was developed to translate association rules into recommendation, promotion, and CRM strategies.

### Recommended Next steps

* 

---

## 10. Python Libraries

* Pandas
* NumPy
* Matplotlib
* Seaborn
* Mlxtend (Apriori)


---
## 📁 Repository Structure

```text
├── data/
│   ├── EcomSales.csv
│   │   └── Transaction-level sales data containing 51,290 order line items.
│   └── Product.csv
│       └── Product master data and category hierarchy.
├── Market Basket Analysis_Ecommerce dataset.ipynb
│   └── Data preparation, exploratory analysis, Apriori implementation, and Association Rule Mining.
└── README.md
    └── Project overview, methodology, key findings, and business recommendations.
```
