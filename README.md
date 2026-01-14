# Exoplanet-Research-NASA

Statistical Analysis of the Exoplanet Radius Gap and Observational Bias using Python.

Project Overview
This project investigates the Fulton Gap (the "Radius Gap")—a significant dip in the distribution of exoplanet sizes between 1.5 and 2.0 Earth radii. By analyzing ~6,000 confirmed planets, I visualized how this gap appears and how different discovery methods (Transit vs. Radial Velocity) create observational biases in our data.

Key Features

Data Source:
Data collected from [NASA Exoplanet Archive](https://exoplanetarchive.ipac.caltech.edu/), 
operated by the California Institute of Technology, under contract with the 
National Aeronautics and Space Administration under the Exoplanet Exploration Program.

Data Cleaning: Filtering missing values and outliers from NASA's huge dataset.

KDE Visualization: Using Kernel Density Estimation to identify the bimodal distribution (having two peaks) of small planets.

Logarithmic Scaling: Applying log scales to compare planetary radius against host star mass across different orders of magnitude. Reason; huge variability in the data.

Independent Learning & Tools

Language: Python

Libraries: Pandas (Data manipulation), Matplotlib & Seaborn (Scientific visualization), NumPy.

Methods: Self-taught through online free sources (Microsoft/DataCamp), then moved to advanced learning through YT lectures from "Corey Schafer" and "Kimberly Fessel"

How to view the work:
The primary analysis scripts are found in main.py and main_2.py.

Process Logs: See the /Process_logs folder for early drafts, handwritten notes, and development stages of this project.
