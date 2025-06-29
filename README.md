# 🏢 TeamK Community Volunteer App 🏢

## Overview

This project is a data-driven platform designed to match individuals who need to complete court-mandated volunteer hours with nonprofit organizations offering suitable opportunities. The system leverages CSV data, a normalized SQLite database, and Python-based data analysis to facilitate efficient, interest- and availability-based matching.

---

## Project Purpose

Many individuals are required to complete community service hours as part of court cases. Our app streamlines the process of finding, reserving, and tracking volunteer opportunities that meet court requirements, while also supporting nonprofits in recruiting volunteers who are a good fit for their needs.

---

## Features

- **Volunteer & Nonprofit Profiles:** Import and manage detailed data for both volunteers and nonprofits.
- **Court Case Tracking:** Link volunteers to their court-mandated service requirements, including hours and deadlines.
- **Matching Logic:** Match volunteers to opportunities based on:
  - Location (zipcode)
  - Available days and time of day
  - Interests and skills
- **Database Integration:** Convert CSV data into a normalized SQLite database for robust querying and reporting.
- **Extensible Design:** Ready for web or app integration, with features like timeslot reservation, progress tracking, and badges.

---

## Data Sources

- **volunteers_.csv:**  
  Contains volunteer profiles, including name, unique volunteer ID, zipcode, available days, and up to three interests per volunteer.

- **court_case.csv:**  
  Contains court case information, linking volunteers to their required hours, deadlines, county, and parole officer.

- **opportunities.csv:**  
  Contains nonprofit volunteer opportunities, including organization, title, location, days/times available, and required interests.

- **_Community Connection App_ Mock Data - fake_nonprofit_volunteer_opportunities.csv:**  
  (Used in EDA/disregard notebooks) Contains mock data for nonprofit opportunities.

- **_Community Connection App_ Mock Data - volunteer_profiles.csv:**  
  (Used in EDA/disregard notebooks) Contains mock data for volunteer profiles.

---

## Data Flow

1. **CSV Import:**  
   CSVs are loaded into pandas DataFrames in the Jupyter notebook [`Notebooks/TeamK_eda.ipynb`](Notebooks/TeamK_eda.ipynb).

2. **Database Creation:**  
   DataFrames are written to a SQLite database (`community_volunteer.db`) with normalized tables for volunteers, court cases, opportunities, and more.

3. **Analysis & Matching:**  
   SQL queries and pandas operations are used to match volunteers to opportunities based on location, interests, and availability.

4. **Visualization:**  
   Data is visualized using matplotlib and seaborn for insights and reporting.

---

## Example Usage

```python
import pandas as pd
import sqlite3

# Load CSVs
volunteers_df = pd.read_csv('volunteers_.csv')
court_case_df = pd.read_csv('court_case.csv')
opportunities_df = pd.read_csv('opportunities.csv')

# Connect to SQLite
conn = sqlite3.connect('community_volunteer.db')

# Write DataFrames to SQL tables
volunteers_df.to_sql('volunteers', conn, if_exists='replace', index=False)
court_case_df.to_sql('court_case', conn, if_exists='replace', index=False)
opportunities_df.to_sql('opportunities', conn, if_exists='replace', index=False)
```

---

## Project Structure

```
Notebooks/
  └── TeamK_eda.ipynb
  └── community_volunteer.db
volunteers_.csv
court_case.csv
opportunities.csv
README.md
```

---

## Next Steps

- Build a web or mobile interface for volunteers and nonprofits.
- Implement advanced matching (e.g., by distance, partial interest overlap).
- Add features like timeslot reservation, progress tracking, and badges.
- Integrate user authentication and case management for parole officers.

---

*Created by Team K*