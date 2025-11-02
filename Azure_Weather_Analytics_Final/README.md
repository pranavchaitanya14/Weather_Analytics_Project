

# 🌤️ Weather Analytics Project using Azure Data Factory & Power BI

## ✅ Project Objective

To build a cloud-based data analytics pipeline that:

* Stores raw weather data in Azure Blob Storage
* Processes it using Azure Data Factory
* Visualizes insights through Power BI

---

## 🚀 Cloud Architecture

**Azure Blob Storage → Azure Data Factory → Power BI Desktop → Power BI Service**

---

## 🏗️ Step-by-Step Implementation

### ✅ 1️⃣ Create Virtual Machine 

> A VM provides a controlled environment for testing and managing Azure services.

1. Go to **Azure Portal → Create a Resource → Virtual Machine**
2. Choose:

   * **Image:** Windows Server or Ubuntu
   * **Size:** Standard B1s
   * **Username/Password:** Set credentials
3. Enable **RDP/SSH access**
4. Click **Review + Create → Create**
5. After deployment, **connect to the VM**

---

### ✅ 2️⃣ Create Azure Storage Account

1. Portal → Search **Storage Accounts → Create**
2. Choose **Resource Group**, **Region**, and **Storage Name**
3. Under **Advanced**, enable **Blob Storage**
4. After deployment → Go to **Containers**
5. Create container: `weatherdata`
6. Upload dataset: `Weather_Data.csv`

   7.create a empty ouput file "Weather_Output.csv" in the same container (so that the data stores here again after completing ETL process)

---

### ✅ 3️⃣ Create Azure Data Factory

1. Portal → **Create Resource → Data Factory**
2. After deployment → **Launch Studio**

---

### ✅ 4️⃣ Create a New Pipeline

1. In ADF Studio → **Author → + → Pipeline → New Pipeline**
2. Rename: `WeatherDataPipeline`
3. Drag and drop **Copy Data** activity into the canvas

---

### ✅ 5️⃣ Configure Source Dataset

> During this step, the **Linked Service** to Azure Blob Storage will be created automatically.

1. Select the **Copy Data** activity → Open the **Source** tab
2. Click **+ New Dataset → Azure Blob Storage → Delimited Text (CSV)**
3. Name: `Weather_Data_Input`
4. **Linked Service:**

   * If none exists → click **+ New**
   * Enter **Storage Account name & key** → Test Connection → Create
5. Select file: `Weather_Data.csv`
6. ✔ First row as header
7. Import schema: From sample file

---

### ✅ 6️⃣ Configure Sink Dataset (Output)

1. Go to **Sink tab → + New Dataset**
2. Select **Azure Blob Storage → Delimited Text (CSV)**
3. Name: `Weather_Data_Output`
4. Use the **same Linked Service** as Source
5. Container: `weatherdata`
6. File name: `Weather_Output.csv`

   * *(If not already there, upload an empty file named `Weather_Output.csv` in Blob — ADF will overwrite it later)*
7. ✔ First row as header

---

### ✅ 7️⃣ Validate and Publish

1. Top toolbar → Click **Validate all**

   * Ensure no errors
2. Click **Publish All** → Confirm to deploy pipeline

---

### ✅ 8️⃣ Trigger and Monitor Pipeline

1. Click **Add Trigger → Trigger Now**
2. Go to **Monitor** tab
3. Observe pipeline run → Status should be **Succeeded** ✅
4. Check **Blob Storage → weatherdata container**

   * New file `Weather_Output.csv` should now exist

---

## 📊 Power BI Visualization Steps

### ✅ Load Data from Azure Blob Storage

1. Open **Power BI Desktop**
2. **Get Data → Azure(or)web → Azure Blob Storage**
3. Enter your **Storage Account URL**
4. Select `Weather_Output.csv`
5. Load data

---

### ✅ Create Visuals

| Chart Type   | X-Axis | Y-Axis        | Description                      |
| ------------ | ------ | ------------- | -------------------------------- |
| Line Chart   | Date   | Temperature   | Track temperature trend          |
| Bar Chart    | City   | Humidity      | Compare humidity by city         |
| Column Chart | City   | Wind Speed    | Analyze wind speed across cities |
| Area Chart   | Date   | Precipitation | View rainfall variation          |

✅ Add **Slicers** for **City** and **Date**

---

## 🌐 Publish to Power BI Service

1. Click **Home → Publish → My Workspace**
2. Open in **Power BI Service** → View dashboard

---

## 📌 Deliverables

✔ Virtual Machine setup (optional)
✔ Azure Blob Storage with input & output files
✔ Azure Data Factory pipeline (linked, validated, published)
✔ Power BI report with interactive visuals
✔ End-to-end workflow operational ✅

---

## ✅ Status: **Completed Successfully**

Pipeline executed, data transformed, and dashboard visualized successfully in the cloud.


