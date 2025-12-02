# 📊 OCHA Donor Ranking Automation

This repository belongs to the CB Brand and Design Unit at OCHA.

---

## 🎯 Purpose
This project automates the creation of a cleaned donor ranking CSV for use in Datawrapper. It fetches data from the OCHA OCT API, converts country codes to ISO2 for flag display, and generates a stable CSV link that can be used directly in Datawrapper charts.

---

## ⚙️ How it works

### 🌐 Source  
Data is fetched from:  
https://oct.unocha.org/api/OCHAOnline/GetDonorRanking

### 🔄 Processing  
The workflow:
- Fetches donor ranking data from the API  
- Converts ISO3 country codes to ISO2  
- Adds a column with Datawrapper-ready flag codes in the format `:xx:`  
- Handles special cases:  
  - `EU` becomes `:eu:`  
  - Private contributions are left without a flag  
- Outputs a clean CSV file ready for Datawrapper

### 📁 Output  
The final file is published as `data_2025_flags.csv` in the repository.

---

## 🔗 Public CSV link
Use this link in Datawrapper:

https://raw.githubusercontent.com/UN-OCHA/oct_api_donor_ranking_to_csv_2025_BDU/refs/heads/main/data_2025_flags.csv

---

## 🛠️ Workflow details
Workflow file: `.github/workflows/update-donor-csv.yml`

The workflow:
1. Fetches the latest donor ranking data from the API  
2. Installs dependencies (`pandas`, `pycountry`)  
3. Processes the data and generates ISO2 and flag codes  
4. Commits and pushes the updated CSV to the repository  

Runs:
- Automatically every day at **06:00 UTC**  
- Manually via **Actions → Run workflow**

---

## 📈 Using the CSV in Datawrapper
1. In Datawrapper, select **Link external dataset**  
2. Paste the public CSV link  
3. Map the `FlagCode` column and enable flag replacement  
4. Optional: create a combined field such as:  
   `CONCAT(FlagCode, " ", DonorName)`  
   This displays the flag next to the donor name

---

## 👥 Maintainers
CB Brand and Design Unit – OCHA  
ochavisual@un.org  

Data provided by Donor Relations Section  
API focal point: Mohannad Ali (ali55@un.org)
