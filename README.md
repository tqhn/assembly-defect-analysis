# Assembly Defect Analysis — Reducing Rework in Manufacturing

This project uses SQL to analyze defect and inspection data from a fictional manufacturing environment. The goal is to identify the top drivers of rework in assembly components and recommend data-backed actions to reduce rework by 20%.

---

## 🛠️ Business Context

In many manufacturing settings, rework due to assembly defects can cost significant time and money. As a Quality Manager, it's crucial to identify patterns across shifts, parts, and suppliers that drive non-conformities and inefficiencies.

This mock project simulates real inspection data to uncover these patterns using SQL.

---

## 📦 Dataset Overview

Three CSV files simulate data from a quality management system:

- `quality_inspections.csv`: Inspection records with defect type, severity, shift, and rework required flag
- `parts.csv`: Part details including part category and supplier ID
- `suppliers.csv`: Supplier information with ID, name, and location

---

## 🔍 Key Questions Answered

- What are the most common assembly-related defect types?
- Which shift is associated with the highest number of severe defects?
- Which suppliers contribute most to rework-required defects?
- What is the trend of rework cases over time?

---

## 📈 Key Insights

- **Misalignment** was the most frequent assembly defect — especially on **Shift A**.
- **Supplier "Precision Gears"** had the highest number of parts requiring rework.
- **Rework trends** are increasing month-over-month, suggesting the need for intervention.

---

## ✅ Recommendations

- Conduct a focused process audit on **Shift A** for **Gear Housing assembly**.
- Engage **Supplier "Precision Gears"** for a corrective action review.
- Train inspectors on **alignment checks** and ensure **SOP adherence**.

---

## 💻 SQL Queries Used

Below are some of the key SQL queries used to analyze the dataset:

```sql
-- 1. Identify the most frequent defect types
SELECT defect_type, COUNT(*) AS defect_count
FROM quality_inspections
GROUP BY defect_type
ORDER BY defect_count DESC;

-- 2. Count high-severity defects by shift
SELECT shift, COUNT(*) AS high_severity_count
FROM quality_inspections
WHERE severity = 'High'
GROUP BY shift
ORDER BY high_severity_count DESC;

-- 3. Rework trends over time
SELECT strftime('%Y-%m', inspection_date) AS month, COUNT(*) AS rework_count
FROM quality_inspections
WHERE rework_required = 1
GROUP BY month
ORDER BY month DESC;

-- 4. Supplier contribution to defects
SELECT suppliers.supplier_name, COUNT(*) AS defects_by_supplier
FROM quality_inspections
JOIN parts ON quality_inspections.part_id = parts.part_id
JOIN suppliers ON parts.supplier_id = suppliers.supplier_id
WHERE quality_inspections.rework_required = 1
GROUP BY suppliers.supplier_name
ORDER BY defects_by_supplier DESC;

