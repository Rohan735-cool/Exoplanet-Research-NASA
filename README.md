# The Exoplanet Census: Observational Bias and the Radius Gap

## Objective
This was a open-ended data analysis. Performed to observe notable patterns in the data. Patterns were studied through AI to match it with previous findings and continued further.

## Language
![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)

## Tools/Libraries
![Anaconda](https://img.shields.io/badge/Anaconda-%2344A833.svg?style=for-the-badge&logo=anaconda&logoColor=white) ![Pandas](https://img.shields.io/badge/pandas-%23150458.svg?style=for-the-badge&logo=pandas&logoColor=white) ![NumPy](https://img.shields.io/badge/numpy-%23013243.svg?style=for-the-badge&logo=numpy&logoColor=white) ![Matplotlib](https://img.shields.io/badge/Matplotlib-%23ffffff.svg?style=for-the-badge&logo=Matplotlib&logoColor=black) ![Seaborn](https://img.shields.io/badge/Seaborn-%234479A1.svg?style=for-the-badge&logo=Seaborn&logoColor=white)

## Procedure

### Step 1
To obtain the csv file containing Exoplanet data, visit the [NASA Exoplanet Archive](https://exoplanetarchive.ipac.caltech.edu/).
Click on "Data" and choose any of the dataset.
Select the Columns you want and download them. (For better expirence; download them as ".csv" file)

### Step 2
Create a Folder and save your CSV File.
You can perform this project on VS Code or Excel, but I would suggest using the "Jupiter Notebook" for your easy going.
First install the "[Anaconda Prompt](https://www.anaconda.com/docs/getting-started/main)." You can easily access the Jupiter Notebook through Anaconda.

### Step 3
After installation, access Jupyter Notebook via Anaconda. You can open the anaconda prompt and comment "cd C:\Project_folder(Assuming your csv file is inside "Project_folder" in "C")" and press 'Enter.'
Then comment "jupyter notebook" and again press 'Enter.'

### Step 4
You can watch some Jupyter Notebook Tutorials from YouTube, that's what I did as well.
Anyway, now it time to finally begin the 'Data Analysis.'
First of all, we need to import all the important libraries that we're gonna need for this project.
Open a code cell and comment:-
'import pandas as pd
import numpy as np
import matplotlib as plt
import seaborne as sn'

### Step 5
Now that we have important important libraries, it's time to show the notebook our csv file.
Bash:- ' "A Variable" = "File_Name" .' [This Variable is important, so name it carefully.]

### Step 6
It's finally time to mine the data. First, you need to find the column header, because those are usally between 50-100 (in NASA Files).

Process Logs: See the /Process_logs folder for early drafts, handwritten notes, and development stages of this project.

Acknowledgenment:
This research has made use of the [NASA Exoplanet Archive](https://exoplanetarchive.ipac.caltech.edu/), 
which is operated by the California Institute of Technology, under contract with the 
National Aeronautics and Space Administration under the Exoplanet Exploration Program.
