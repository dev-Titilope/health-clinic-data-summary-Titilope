# Life Care Clinics: Vital Signs Analysis Tool

## 📋 Overview
This Python-based analytical tool processes patient medical records to identify statistical outliers in vital signs. By calculating the **First ($Q_1$)** and **Third ($Q_3$)** Quartiles, the script automatically flags patients whose heart rate or body temperature falls outside the mathematically "normal" range.



## ✨ Features
* **Automated Data Cleaning:** Parses raw CSV data and handles encoding issues (including BOM characters like `\ufeff`).
* **Synthetic Data Generation:** Uses `random.seed` to generate consistent age data for demo purposes.
* **Outlier Detection:** Implements the **1.5 × IQR rule** to detect anomalies in:
    * Heart Rate (BPM)
    * Body Temperature (°C)
* **High-Risk Reporting:** Generates a clean console report for clinical staff, highlighting specific Patient IDs that require immediate review.

## 🛠️ Technical Stack
* **Language:** Python 3.x
* **Modules:** * `csv`: For file I/O operations and dictionary mapping.
    * `statistics`: Used for finding $Q_1$, $Q_3$, and medians.
    * `random`: For generating patient demographic data.

---

## 🚀 How It Works

### 1. The Math
The script identifies outliers by calculating the **Interquartile Range (IQR)**:

$$IQR = Q_3 - Q_1$$

Any value falling outside the following bounds is flagged:
* **Lower Bound:** $Q_1 - (1.5 \times IQR)$
* **Upper Bound:** $Q_3 + (1.5 \times IQR)$



### 2. Data Structure
The script expects a CSV file named `patient_vitals.csv` with the following headers:
* `Subject ID`
* `Temperature reading 1`
* `Heart rate reading 1`
* `Diastolic blood pressure reading 1`
* `Oxygen saturation reading 1`

---

## 📊 Example Output

```text
==================================================
       LIFE CARE CLINICS: VITAL REPORT   
================================================== 

Total patient analyzed: 102
Average Patient's Heart Rate: 82.2 BPM
Average Patient's Temperature: 36.2 °C
--------------------------------------------------
All patient vitals within normal statistical ranges.
==================================================
