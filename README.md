# SwiftLog Logistics Analytics & AI Transformation — Week 5

**Track:** Data Science  
**Intern:** Takudzwa Jeffrey Gumbo (TJ)  
**Mission:** DS05 — Supply Chain Intelligence & Feature Engineering for Predictive Logistics  
**Programme:** AnalystLab Africa Experience Lab — Batch E

## Executive result

This project builds a reproducible analytical and feature-engineering foundation for future predictive logistics using the supplied SwiftLog datasets.

| Headline | Result |
|---|---:|
| Orders preserved | 5,000 |
| Orders with item/revenue detail | 4,764 |
| Orders missing item detail | 236 |
| Observed revenue | $21,668,065.85 |
| Average observed order value | $4,548.29 |
| Delayed-delivery rate | 63.7% |
| Average delay | 3.57 days |
| Returned-order rate | 9.5% |
| Top revenue category | Fashion |
| Peak demand month | August (654 orders) |

## Key findings

- Delivery performance is the clearest operational concern: **63.7%** of 5,000 shipments are labelled delayed.
- **August** records the highest order volume and observed revenue.
- **Fashion** is the highest-revenue product category, contributing about **$8,059,602.65**.
- **P040** is the highest-revenue individual product at approximately **$191,463.68**.
- High-Value Loyal customers contribute the largest customer-segment revenue.
- All three inferential tests fail to reject their null hypotheses. Observed warehouse delay differences, return-related delay differences and city-level revenue differences should therefore not be overstated.

## Critical data limitations

1. **Suppliers are standalone.** `SupplierID` appears only in `SwiftLog_Suppliers.csv`; no supplier-performance relationship is fabricated.
2. **Warehouse capacity is absent.** Inventory quantity, product breadth and shipment volume are used only as clearly labelled load proxies.
3. **Inventory has no date.** Repeated Warehouse–Product records are retained as stock movements and aggregated only for reporting.
4. **Returns are order-level.** `ProductID` / `OrderItemID` is absent, so true product return rates cannot be calculated.
5. **236 Orders have no Order_Items rows.** They remain in the 5,000-order dataset and are explicitly flagged.
6. September data ends on 8 September and is treated as a partial month.

## Statistical analysis

| Hypothesis | Test | p-value | Decision |
|---|---|---:|---|
| Delivery delay distribution differs across warehouses | Kruskal-Wallis | 0.759 | Fail to reject |
| Delivery delay differs for returned vs non-returned orders | Mann-Whitney U | 0.983 | Fail to reject |
| Order revenue distribution differs across customer cities | Kruskal-Wallis | 0.330 | Fail to reject |

Null findings are reported as results rather than removed.

## Feature-engineered dataset

`Data/Feature_Engineered_Dataset.csv` contains one row per order and preserves all 5,000 orders. Important engineered variables include:

- order revenue, units, product/category breadth and dominant category;
- strictly prior customer order/spend features;
- month, quarter, day-of-week and demand indicators;
- warehouse stock/product/shipment/staffing load proxies;
- delay and return outcomes for future supervised-learning targets.

Outcome-derived fields such as `DelayDays`, `DeliveryStatus`, `IsDelayed` and `DeliveryEfficiencyScore` must not be used as predictors when modelling delivery delay.

## Project structure

```text
Week5_DataScience_SwiftLog_TakudzwaGumbo/
├── Data/
│   ├── Original_Datasets/
│   ├── Cleaned_Datasets/
│   └── Feature_Engineered_Dataset.csv
├── Notebook/
│   └── Week5_DataScience.ipynb
├── Reports/
│   ├── Data_Profiling_Report.html
│   ├── Technical_Report.pdf
│   ├── Technical_Report.docx
│   ├── Executive_Summary.pdf
│   └── Executive_Summary.docx
├── Visualizations/
│   ├── Charts/
│   └── Dashboards/
├── Presentation/
│   ├── Executive_Presentation.pptx
│   └── Presentation_Script.pdf
├── Analysis/
├── References/
├── README.md
├── requirements.txt
├── WEEK5_SUBMISSION_CHECKLIST.md
└── social_posts_week5.md
```

## Reproduce in Google Colab

The notebook searches recursively under:

```text
/content/drive/MyDrive/Analyst Lab Africa
```

Place the supplied SwiftLog CSVs anywhere below that folder, open `Notebook/Week5_DataScience.ipynb` in Colab, then use **Runtime → Restart session and run all**. The notebook creates an output folder named `SwiftLog Week 5 (TJ Gumbo)` in the same Drive root when running in Colab.

## Main recommendations

- Establish a delivery-delay reduction programme and monitor delay KPIs weekly.
- Review W05/W09/W03 operational processes first, while recognising warehouse differences are not statistically significant.
- Plan additional operational capacity for the August demand peak.
- Protect High-Value Loyal customers through service-level monitoring and retention activity.
- Use product segments to differentiate replenishment and portfolio management.
- Add `SupplierID` to operational records, true warehouse-capacity fields, dated inventory snapshots and product/line identifiers to returns.
- Resolve missing order-item records before production revenue/product models are deployed.

## Future machine-learning opportunities

- Delivery delay classification/regression.
- Product/category demand forecasting.
- Order-level return-risk prediction.
- Supplier reliability modelling once SupplierID relationships are available.
- Warehouse optimisation once capacity and time-stamped inventory are available.

## Reproducibility

Random seed **42** is used for K-Means segmentation. All numerical claims in the report and presentation come from code executed against the supplied CSV files. No supplier relationship or warehouse capacity value was invented.
