
# 🌤️ Weather Analytics Project using Azure Data Factory & Power BI

## ✅ Project Objective
To build a cloud-based analytics pipeline that:
- Stores raw weather data in Azure Blob Storage
- Copies and processes data using Azure Data Factory
- Visualizes insights using Power BI

---

## 🚀 Cloud Architecture
Azure Blob Storage → Azure Data Factory → Power BI Desktop → Power BI Service

---

## 🏗️ Step-by-Step Implementation

### ✅ 1️⃣ Create Azure Storage Account
1. Go to Azure Portal → Search **Storage Accounts**
2. Create → Choose Resource group + region
3. Enable **Blob Storage**
4. Open Storage → Containers → Create container: **weatherdata**
5. Upload file: `Weather_Data.csv` (this dataset)

---

### ✅ 2️⃣ Create Azure Data Factory
1. Azure Portal → Create Resource → **Data Factory**
2. Launch ADF Studio → **Integrate → Pipeline**

---

### ✅ 3️⃣ Create Source Dataset (Input)
- Type: **Delimited Text (CSV)**
- Linked Service: Azure Blob Storage
- Container: `weatherdata`
- File: `Weather_Data.csv`
- First row = Header ✔
- Import Schema = From Sample File

---

### ✅ 4️⃣ Create Sink Dataset (Output)
- Same storage, same container
- Filename: `Weather_Output.csv`
- First row as header ✔

---

### ✅ 5️⃣ Build Pipeline
Inside Pipeline:
- Activity: **Copy Data**
- Source = `Weather_Data`
- Sink = `Weather_Output`
- Debug → Publish
- **Trigger Now**

✅ Monitoring → Pipeline runs → Success


✅ Output file now exists in Blob ✅

---

## 📊 Power BI Visualization Steps

### ✅ Load from Azure Blob Storage
1. Power BI Desktop → **Get Data → Azure Blob Storage**
2. Enter Storage Account URL
3. Choose **Weather_Output.csv**
4. Load

### ✅ Create Visuals
Suggested Charts:
| Chart Type | X-Axis | Y-Axis |
|-----------|--------|--------|
| Line Chart | Date | Temperature |
| Bar Chart | City | Humidity |
| Column Chart | City | Wind Speed |
| Area Chart | Date | Precipitation |

✅ Add Slicers for **City** and **Date**

---

## 🌐 Publish to Cloud
1. Home → **Publish**
2. Select **My Workspace**
3. Open in Power BI Service ✅

---

## 📌 Deliverables
✔ Blob storage with dataset  
✔ Azure Data Factory pipeline  
✔ Weather insights report in Power BI  
✔ End-to-end cloud analytics workflow

---

## ✅ Status: Completed Successfully
