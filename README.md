# assembly-defect-analysis
SQL project analyzing quality inspection and defect data

# Assembly Defect Analysis — Reducing Rework in Manufacturing

This project uses SQL to analyze defect and inspection data from a fictional manufacturing environment. The goal is to identify the top drivers of rework in assembly components and recommend data-backed actions to reduce rework by 20%.

## 🛠️ Business Context

In many manufacturing settings, rework due to assembly defects can cost significant time and money. As a Quality Manager, it's crucial to identify patterns across shifts, parts, and suppliers that drive non-conformities and inefficiencies.

This project simulates real inspection data to uncover these patterns using SQL.

## 📦 Dataset Overview

Three CSV files simulate data from a quality management system:

- `quality_inspections.csv`: inspection records with defect type, severity, shift, rework required
- `parts.csv`: part details including category and supplier
- `suppliers.csv`: supplier name and location


## 🔍 Key Questions Answered

- What are the most common assembly-related defect types?
- Which shift is associated with the highest number of severe defects?
- Which suppliers contribute most to rework-required defects?
- What is the trend of rework cases over time?


## 💻 Sample SQL Query

```sql
SELECT shift, COUNT(*) AS high_severity_count
FROM quality_inspections
WHERE severity = 'High'
GROUP BY shift
ORDER BY high_severity_count DESC;



---

### ✅ Step 6: Key Insights (Your Takeaways)

Summarize what the data told you — this is where you flex your quality manager perspective.

```markdown
## 📈 Key Insights

- Misalignment was the most frequent assembly defect — especially on Shift A.
- Supplier "Precision Gears" had the highest number of parts requiring rework.
- Rework trends are increasing month-over-month, suggesting need for intervention.

## ✅ Recommendations

- Conduct a focused process audit on Shift A for Gear Housing assembly.
- Engage Supplier "Precision Gears" for a corrective action review.
- Train inspectors on alignment checks and ensure SOP adherence.

## 🛠️ Tools Used

- SQL (SQLite/PostgreSQL)
- Excel (for CSV validation)
- Power BI (for dashboards — optional)
- Markdown (for documentation)

