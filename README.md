# Gender-Inequality-Index - Beyond the Pay Gap:
## A Multi-Dimensional Gender Inequality Index Across Europe (EU)

### Project Overview
This project aims to construct a multi-dimensional Gender Inequality Index across EU countries using Eurostat data. 
By combining economic, educational, social, and leadership-related indicators, the project explores how different dimensions of gender inequality interact and where countries diverge across structural and lived-experience dimensions of inequality.

### Timeframe
The analysis focuses on the 2021–2024 period, which represents the latest timeframe consistently available across the selected Eurostat indicators.

### Objectives
- Build a multi-dimensional Gender Inequality Index using Eurostat data
- Compare EU countries across multiple dimensions of inequality
- Analyze how different inequality indicators interact
- Identify structural divergences and patterns across countries and over time

### Dimensions of Inequality
- Economic Participation
- Education
- Social Constraints
- Leadership

### Data Sources
Social Constraints
- [Self-reported unmet needs for medical examination](https://ec.europa.eu/eurostat/databrowser/view/hlth_silc_21__custom_20907036/default/table)
- [Overall life satisfaction](https://ec.europa.eu/eurostat/databrowser/view/ilc_pw01__custom_21471026/default/table)

Economic Participation
- [Persons at risk of poverty or social exclusion](https://ec.europa.eu/eurostat/databrowser/view/hlth_dpe010__custom_20908069/default/table)
- [Inability to face unexpected financial expenses](https://ec.europa.eu/eurostat/databrowser/view/hlth_dm040__custom_20908400/default/table)
- [Gender employment gap](https://ec.europa.eu/eurostat/databrowser/view/tesem060__custom_21470708/default/table)

Education
- [Students enrolled in tertiary education](https://ec.europa.eu/eurostat/databrowser/view/educ_uoe_enrt02__custom_21470450/default/table)
- [Persons with tertiary education in STEM fields](https://ec.europa.eu/eurostat/databrowser/view/hrst_stem_gen__custom_21470871/default/table)

Leadership
- [Positions held by women in senior management](https://ec.europa.eu/eurostat/databrowser/view/sdg_05_61__custom_21471234/default/table)
- [Seats held by women in national parliaments and governments](https://ec.europa.eu/eurostat/databrowser/view/sdg_05_50__custom_21471279/default/table)

### Methodology
The project will involve:
- Data cleaning and standardization
- Gender gap calculation
- Indicator normalization
- Construction of a composite index
- Exploratory and comparative analysis
- Dashboard visualization
  
Indicators will be standardized and directionally aligned to ensure comparability across dimensions before being combined into a composite index.

### Project Structure
- `/data/raw` → Original Eurostat datasets
- `/docs` → Project planning and documentation


### Naming Conventions
Dataset prefixes indicate project dimensions:
- ec_ -> Economic Participation
- ed_ -> Education
- s_ -> Social Constraints
- l_ -> Leadership

### Current Status
- [x] Project planning
- [x] Metric selection
- [x] Raw data collection
- [ ] Data cleaning & transformation
- [ ] Standardization & direction alignment
- [ ] Index construction
- [ ] Dashboard development
- [ ] Final analytical report

### Planned Deliverables
- Interactive analytical dashboard
- Analytical report
- Final index
- Reproducible data pipeline and project documentation
