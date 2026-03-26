# The Exoplanet Census: Observational Bias and the Radius Gap

> An independent data analysis project exploring the bimodal distribution of exoplanet radii using the NASA Exoplanet Archive.

---

## Overview

This project investigates the **Fulton Gap** — a statistically significant dip in the frequency of planets with radii between **1.5 and 2.0 Earth radii** — using a dataset of approximately 6,000 confirmed exoplanets. The analysis explores how photoevaporation drives atmospheric loss in sub-Neptune-sized planets, causing them to shrink into bare rocky cores (super-Earths), and examines how observational bias across different discovery methods shapes our understanding of planetary populations.

**Key Finding:** The bimodal radius distribution is consistent with photoevaporation theory — smaller planets near their host stars cannot retain their hydrogen/helium envelopes under intense stellar XUV radiation, producing the observable gap in the size distribution.

---

## Language & Tools

![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)
![Pandas](https://img.shields.io/badge/pandas-%23150458.svg?style=for-the-badge&logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/numpy-%23013243.svg?style=for-the-badge&logo=numpy&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-%23ffffff.svg?style=for-the-badge&logo=Matplotlib&logoColor=black)
![Seaborn](https://img.shields.io/badge/Seaborn-%234479A1.svg?style=for-the-badge&logo=Seaborn&logoColor=white)
![Anaconda](https://img.shields.io/badge/Anaconda-%2344A833.svg?style=for-the-badge&logo=anaconda&logoColor=white)

---

## Visualizations

**Fig 1 — KDE Plot (Bimodal Distribution):** Visualizes the dip in planet frequency between 1.5 and 2.0 Earth radii, marking the boundary between rocky super-Earths and gaseous sub-Neptunes.

**Fig 2 — Log-Log Scatter Plot:** Maps ~6,000 confirmed exoplanets by radius vs. host star mass, color-coded by discovery method (Transit, Radial Velocity, etc.), revealing the observational bias inherent in each detection technique.

> Full plots and analysis are in `Exoplanet_Analysis_1.ipynb` — click the file above to view the complete project.

---

## How to Replicate This Project

### Prerequisites
Install [Anaconda](https://www.anaconda.com/docs/getting-started/main) — it includes Jupyter Notebook and all required libraries out of the box.

### Step 1 - Get the Data
Visit the [NASA Exoplanet Archive](https://exoplanetarchive.ipac.caltech.edu/). Navigate to Data → Planetary Systems Composite Parameters (PSCompPars). Select the columns you want and download the table as a .csv file. The file used in this project was PSCompPars_2025.10.26_04.25.20.csv.

### Step 2 - Set Up Your Project Folder
Create a folder (e.g. Exoplanet_Project) and place your .csv file inside it. Open Anaconda Prompt and navigate to it:

```bash
cd C:\Exoplanet_Project
jupyter notebook
```

### Step 3 - Import Libraries
```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
```

### Step 4 - Load and Clean the Dataset
NASA archive files contain ~84 header rows before the actual data begins. Use skiprows=84 to skip them:

```python
DATA_FILE = 'PSCompPars_2025.10.26_04.25.20.csv'
df = pd.read_csv(DATA_FILE, skiprows=84, header=0)
```

Then rename columns for clarity:
```python
new_names = {
    'pl_name': 'exoplanet_name',
    'pl_orbper': 'orbital_period_days',
    'disc_year': 'discovery_year',
    'pl_bmasse': 'exoplanet_mass_earth',
    'pl_rade': 'exoplanet_rad_earth',
    'hostname': 'steller_name',
    'pl_eqt': 'equilibrium_temp_kelvin',
    'pl_discmethod': 'discovery_method',
    'st_mass': 'star_mass_solar',
    'st_rad': 'star_rad_solar',
    'st_teff': 'star_temp_kelvin',
    'st_logg': 'star_log_gravity',
    'st_age': 'star_age_gyr'
}
df.rename(columns=new_names, inplace=True)
```

Drop all uncertainty/error columns (err1, err2, lim suffixes) to keep only the physical values, then check your data:

```python
print(df.describe())
```

### Step 5 - Plot 1: Orbital Period Distribution
```python
plt.figure(figsize=(10, 6))
sns.histplot(df['orbital_period_days'], bins=50, kde=True, log_scale=True)
plt.title('Distribution of Exoplanet Orbital Periods')
plt.xlabel('Orbital Period (Days, log scale)')
plt.ylabel('Count')
plt.grid(True)
plt.show()
```

Why log scale? Orbital periods range from under 1 day to over 400 million days. A linear axis would make the plot unreadable — log scale compresses this range meaningfully.

### Step 6 - Plot 2: The Fulton Gap (KDE Plot)
Filter out rows with missing values first:

```python
Col_X = 'star_mass_solar'
Col_Y = 'exoplanet_rad_earth'
Col_Hue = 'discoverymethod'

df_filtered = df.dropna(subset=[Col_X, Col_Y, Col_Hue])
```

Then plot the radius distribution:

```python
plt.figure(figsize=(10, 6))
sns.kdeplot(data=df_filtered, x='exoplanet_rad_earth', fill=True, linewidth=3,
            color='steelblue', alpha=0.6, bw_adjust=0.2, label='Density Estimate')

plt.axvspan(1.5, 2.0, color='red', alpha=0.2, label='Fulton Gap (Atmospheric Loss)')
plt.title('Bimodal Distribution of Exoplanet Radii: The Fulton Gap (Proof)')
plt.xlabel('Planet Radius (Earth Radii)')
plt.ylabel('Density Estimate')
plt.xlim(0.5, 5.0)
plt.ylim(bottom=0)
plt.grid(True, axis='y', alpha=0.3)
plt.legend()
plt.show()
```

Note: bw_adjust=0.2 was set lower than the default to reveal the gap more clearly — the default smoothing was masking the dip.

### Step 7 - Plot 3: Radius vs. Host Star Mass (Scatter Plot)

```python
plt.figure(figsize=(10, 6))
sns.scatterplot(data=df_filtered, x=Col_X, y=Col_Y, hue=Col_Hue,
                palette='Spectral', alpha=0.7, s=70, legend='full')

plt.xscale('log')
plt.yscale('log')
plt.title('Exoplanet Radius vs. Host Star Mass')
plt.xlabel('Host Star Mass (Solar Masses, log scale)')
plt.ylabel('Exoplanet Radius (Earth Radii, log scale)')
plt.axvline(x=1.0, color='red', linestyle='--', linewidth=1.5, label='Sun Mass')

# Earth plotted at correct position: 1/333000 solar masses, radius = 1 Earth radius
plt.scatter(1/333000, 1.0, marker='o', s=100, color='black', label='Earth')

plt.legend(title='Discovery_Method', bbox_to_anchor=(1.05, 1), loc=0)
plt.grid(True, which="both", ls="--", alpha=0.5)
plt.show()
```

Why 1/333000? Earth's mass is 1/333,000th of the Sun's. This places Earth at its correct position on the solar mass scale.

## Independent Learning Path

This project was built entirely through self-directed study.

---

## Acknowledgement

This research has made use of the [NASA Exoplanet Archive](https://exoplanetarchive.ipac.caltech.edu/), operated by the California Institute of Technology under contract with NASA's Exoplanet Exploration Program.
