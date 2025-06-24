
# 📱 Smartphone Dataset - Power BI Dashboard

A comprehensive Power BI project analyzing global smartphone sales using data sourced via Microsoft SharePoint. This dashboard includes price analysis, feature comparisons, and brand performance across models and countries.

---

## 🚀 Key Learnings

- Microsoft SharePoint integration with Power BI  
- Power Query for data transformation  
- DAX functions and calculated columns  
- Data modeling and relationships  
- Use of slicers and filters  
- Bookmarks and drill-through functionality  
- Interactive dashboard design principles  

---

## 📌 Problem Statement

To analyze and visualize smartphone sales data across multiple countries. The goal was to understand brand-wise model distributions, price comparisons, and feature-based analysis for better business and consumer insights.

---

## 🧾 Steps Followed

**📁 Data Source**  
Smartphone dataset containing model specifications, selling prices across countries, and brand details.

### 📊 Power BI Workflow

1. **Data Import**
   - Used **Get Data** → **From SharePoint Folder** to connect and load data.
  
2. **Data Transformation**
   - Clicked **Transform Data** to open Power Query Editor.
   - Formatted all columns to correct data types (decimal, whole number, text, etc.).
   - Used **Split Column** to separate numeric values from units (e.g., "8 GB").
   - Identified and handled null values by replacing them with average values.
   - Applied **Trim** function to clean textual data.

3. **Data Modeling**
   - Established relationships between data tables.
   - Created calculated columns for easier filtering and grouping.
  
4. **Dashboard Pages & Visuals**
   - **Overview Page**: Includes slicers for Year and Model selection.
   - **Model Analysis**:
     - Bar chart showing smartphone model counts by company.
     - Chart comparing RAM size and front/back camera resolution by brand.
   - **Camera Resolution**:
     - Dedicated page for detailed camera specifications.
     - Drill-through enabled for exploring model-level data.
   - **Price Analysis**:
     - Charts to explore model-wise and company-wise price differences.
     - Used **Bookmarks** and **Buttons** for navigation and interaction.
   - **Feature vs Price**:
     - Comparison table including all major specifications.
     - Currency-based price selection using bookmark buttons.

5. **Custom Column Logic**
   - Used `CONCATENATE` function to combine company and model names (shared in Excel).
   - Used `IF` and `LEN` functions to extract specific text patterns from model names.

---

## 📸 Snapshots


![Image](https://github.com/user-attachments/assets/a2a17506-2b19-4c31-8397-e20565e098dc)


![Image](https://github.com/user-attachments/assets/63942b76-8579-4e8a-8018-7bca7a0a75fe)


![Image](https://github.com/user-attachments/assets/b488b58c-a1bd-490e-883c-bcf4d6b71b02)

![Image](https://github.com/user-attachments/assets/60afdeeb-e4ad-4509-881e-932eabfec061)







