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

## Dataset overview

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

## 3. Methodology

### Association Rule Mining

Applied the Apriori algorithm at the Subcategory level to identify purchasing associations across product groups.

| Metric | Business Meaning	| Threshold |
|---|---|---|
| Support |	% of baskets containing both product groups |	≥ 0.1% |
| Confidence | Probability of purchasing product group B after purchasing A	| ≥ 10% |
| Lift | Association strength beyond random chance | ≥ 1.2 |

### Other terminologies

* **Antecedents:**
* **Consequents:**
* **Association Rule:**

### Action Framework

| Action Group | Determination | Interpretation |Recommended Action |
|---|---|---|---|
| Scale | Support ≥ 0.002 & Confidence ≥ 0.1692 | High-tier Support and Confidence |Bundles and broad recommendations |
| Reach | Support ≥ 0.002 & Confidence ≤ 0.1692 |	High-tier Support but low-tier Confidence | Promotional testing and exploration |
| Precision	| Support ≤ 0.002 & Confidence ≥ 0.1692 | Low-tier Support but high-tier Confidence | Personalized cross-selling |
| Monitor	| Support ≤ 0.002 & Confidence ≤ 0.1692 | Low-tier Support and Confidence | Periodic review |

---

## 4. Key findings: What do current baskets tell us?

* The most common product combinations are centered around personal care categories, including nail care, body care, hand care, bath products, and hair care.

* The strongest associations (high lift) suggest two dominant customer needs:

  * Holistic self-care: hair care, facial skincare, body cleansing, nail care.
  * At-home wellness spa: personal care products purchased alongside candles, diffusers, home fragrance, and spa products.

* Support, Confidence, and Lift capture different dimensions of customer behavior. Yet, little overlap exists between top rules ranked by Support, Confidence, and Lift, confirming that no single metric is sufficient for business decision-making.

<img src='./images/Meaningful assocation rules.png' width=1200>

---

## Các thư viện Python sử dụng phân tích

- Pandas
- Mlxtend (Apriori)
- NumPy
- Matplotlib
- Seaborn

---
## 📁 Cấu trúc dự án

```text
├── data/
│   ├── EcomSales.csv
│   │   └── Dữ liệu giao dịch với 51.290 dòng ở cấp độ Order Line Item
│   └── Product.csv
│       └── Danh mục sản phẩm và thông tin phân loại
├── Market Basket Analysis_Ecommerce dataset.ipynb
│   └── Tiền xử lý dữ liệu, xây dựng mô hình Apriori và phân tích Association Rules
└── README.md
    └── Tổng quan dự án, kết quả phân tích và khuyến nghị kinh doanh
```
