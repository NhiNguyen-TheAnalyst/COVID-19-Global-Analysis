## COVID-19 Global Analysis

## Objective
To understand how the COVID-19 pandemic unfolded globally, not just in terms of raw numbers, but in terms of which countries were hit hardest, how death rates compared across regions, and whether vaccination rollout in early 2021 showed meaningful progress.

**Tools:** Power Query · DAX · Power BI  
**Dataset:** Our World in Data COVID-19 (85,171 rows · 59 columns · Jan 2020-Apr 2021)

### Data modeling decisions
- Dropped CovidVaccinations table after confirming zero unique columns vs CovidDeaths
- Split CovidDeaths into Fact_CovidDaily (daily metrics) and Dim_Country (static demographic attributes) using a star schema
- Filtered aggregate rows (World, continents) from both tables before modeling
- Built Rolling People Vaccinated as a DAX measure replicating SQL window function logic (SUM OVER PARTITION BY location ORDER BY date)

### Dashboard pages
1. **Global Overview**: world map, KPI cards, case/death trend line
<img width="1243" height="718" alt="image" src="https://github.com/user-attachments/assets/db59fc0e-8824-4c9a-914d-a1d03e1f2860" />

2. **Country Deep Dive**: slicer-driven country exploration with wave charts
<img width="1248" height="727" alt="image" src="https://github.com/user-attachments/assets/f4873a38-3642-4cee-9327-74dade205559" />

3.**Vaccination Progress**: cumulative rollout by continent, top 20 countries, vaccination vs death rate scatter
<img width="1248" height="725" alt="image" src="https://github.com/user-attachments/assets/811ea656-708c-4c50-a817-2de9065482d7" />

### Data limitations disclosed
- Vaccination data available for ~11% of country-date rows only
- 2020–2021 snapshot; does not reflect full pandemic trajectory
