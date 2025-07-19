# Cancer Data Visualization in America

A collaborative data visualization project analyzing cancer incidence, mortality rates, and associated risk factors across US states.

**Contributors:** Chris Catolico, Shahzina Khan, Susi Ng, Leeza Sergeeva

## Project Overview

This web application provides interactive visualizations of cancer statistics across the United States, combining incidence and mortality data with demographic information and risk factors to identify patterns and correlations in cancer rates by state.

## Features

### Interactive Visualizations
- **State-by-state cancer maps** for major cancer types (breast, lung, colon, prostate, skin)
- **Top 5 rankings** for cancer incidence and mortality rates
- **Pie charts** showing cancer distribution by state
- **Comparative analysis** of risk factors and demographics

### Cancer Types Analyzed
- Bladder, Brain, Breast (including in-situ)
- Cervical, Childhood cancers (<15 and <20 years)
- Colorectal, Esophageal, Kidney
- Leukemia, Liver, Lung
- Melanoma, Non-Hodgkin's Lymphoma
- Oral/Pharyngeal, Ovarian, Pancreatic
- Prostate, Stomach, Thyroid, Uterine

## Data Sources

### Primary Data
All cancer data obtained from [State Cancer Profiles](https://statecancerprofiles.cancer.gov/) as CSV files, converted to SQLite database for efficient storage and retrieval.

**Data Year:** 2015 (single year analysis)  
**Demographics:** All Races (includes Hispanic), Both Sexes, All Ages  
**Geographic Coverage:** All US states

### Risk Factors Data (2016 BRFSS)
- Current smoking rates (Ages 18+)
- Fruit and vegetable consumption (Ages 18+)
- Physical activity levels (Ages 18+)
- BMI categories:
  - Obesity rates (Ages 20+ and high school students)
  - Overweight rates (high school students)
  - Healthy weight percentages (Ages 20+)

### Census & Demographics Data (2012-2016 ACS)
- **Housing:** Household crowding (>1 person per room)
- **Economic:** Median family income, poverty rates (<150% poverty line)
- **Education:** Bachelor's degree attainment (Ages 25+)
- **Employment:** Unemployment rates (Ages 16+)
- **Healthcare:** Uninsured rates (Ages <65)

## Technology Stack

### Backend
- **Flask** - Web framework
- **SQLAlchemy** - Database ORM
- **SQLite** - Database storage
- **Pandas** - Data processing

### Frontend
- **HTML/CSS/JavaScript** - Web interface
- **Interactive maps and charts** - Data visualization

### Database Structure
- **incidence** - Cancer incidence rates and counts
- **mortality** - Cancer mortality rates and counts  
- **risk** - Risk factor percentages by state
- **census** - Demographic and socioeconomic data

## Installation & Setup

### Prerequisites
- Python 3.7+
- pip package manager

### Installation Steps

1. **Clone the repository**
   ```bash
   git clone [repository-url]
   cd cancer-data-visualization
   ```

2. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

3. **Database setup**
   - Ensure `cancer.sqlite` database file exists in the `data/` directory
   - Database should contain tables: `incidence`, `mortality`, `risk`, `census`

4. **Run the application**
   ```bash
   python app.py
   ```

5. **Access the application**
   - Open your browser to `http://localhost:5000`

## API Endpoints

### Data Access Routes
- `/api/incidence` - Cancer incidence data by state
- `/api/mortality` - Cancer mortality data by state  
- `/api/risks` - Risk factors data by state
- `/api/census` - Census/demographic data by state

### Visualization Routes
- `/` or `/index` - Main dashboard
- `/breastcancer` - Breast cancer map
- `/lungcancer` - Lung cancer map
- `/coloncancer` - Colorectal cancer map
- `/prostatecancer` - Prostate cancer map
- `/skincancer` - Melanoma map
- `/top5incd` - Top 5 incidence rates
- `/top5mort` - Top 5 mortality rates
- `/pie` - State pie chart analysis

## File Structure

```
UCBBEL2019_Project3/
├── LICENSE                          # Project license
├── ReadMe.md                       # Project documentation
├── app.py                          # Main Flask application
├── Resources/                      # Additional resources
│   ├── city_env_stats_all.csv    # Environmental statistics data
│   └── note.md                    # Resource notes
├── data/                          # Primary data directory
│   ├── cancer.sqlite              # Main SQLite database
│   ├── census.csv                 # Census demographic data
│   ├── geo_states.json           # State geographical boundaries
│   ├── incidence.csv             # Cancer incidence raw data
│   ├── mortality.csv             # Cancer mortality raw data
│   └── risk.csv                  # Risk factors raw data
├── instance/                      # Flask instance folder
├── sqlite/                        # Alternative database location
│   ├── Cancer_db.sqlite          # Backup/alternative database
│   ├── census.csv                # Census data copy
│   ├── incidence.csv             # Incidence data copy
│   ├── mortality.csv             # Mortality data copy
│   └── risk.csv                  # Risk data copy
├── static/                        # Static web assets
│   ├── css/
│   │   └── style.css             # Main stylesheet
│   ├── gz_2010_us_040_00_20m.json # US state boundaries GeoJSON
│   └── js/                       # JavaScript files
│       ├── config.js             # Configuration settings
│       ├── datafive.js           # Top 5 incidence data processing
│       ├── datafivemort.js       # Top 5 mortality data processing
│       ├── map_breast.js         # Breast cancer map logic
│       ├── map_colon.js          # Colorectal cancer map logic
│       ├── map_lung.js           # Lung cancer map logic
│       ├── map_prostate.js       # Prostate cancer map logic
│       ├── map_skin.js           # Skin cancer map logic
│       ├── plotsfive.js          # Top 5 incidence visualizations
│       ├── plotsfivemort.js      # Top 5 mortality visualizations
│       └── plotstatepie.js       # State pie chart logic
└── templates/                     # HTML templates
    ├── about.html                # About page
    ├── index.html                # Main dashboard
    ├── state_pie.html            # State pie chart page
    ├── topfiveIncidence.html     # Top 5 incidence page
    ├── topfiveMortality.html     # Top 5 mortality page
    ├── map_breast.html           # Breast cancer map page
    ├── map_colon.html            # Colorectal cancer map page
    ├── map_lung.html             # Lung cancer map page
    ├── map_prostate.html         # Prostate cancer map page
    ├── map_skin.html             # Skin cancer map page
    └── images/                   # Image assets
        ├── desktop.ini           # Windows system file
        ├── image1.jpg            # Project image 1
        ├── image2.jpg            # Project image 2
        └── image3.jpeg           # Project image 3
```

## Data Processing Notes

- All rates are age-adjusted per 100,000 population
- Data includes both raw counts and standardized rates
- Missing or suppressed data handled appropriately in visualizations
- Database uses SQLAlchemy ORM with automatic table reflection

## Future Enhancements

- Time series analysis with multi-year data
- Advanced statistical correlations between risk factors and cancer rates
- Machine learning predictions for cancer incidence
- Additional cancer types and demographic breakdowns
- Real-time data updates from cancer registries

## Additional Resources

- [National Cancer Institute SEER Program](https://www.cancer.gov/research/resources/resource/130)
- [Cancer GIS Tools](https://gis.cancer.gov/)
- [UV Exposure Mapping](https://gis.cancer.gov/tools/uv-exposure/)
- [EPA Superfund Sites](https://www.epa.gov/superfund/national-priorities-list-npl-sites-state)
- [CDC Cancer Statistics](https://www.cdc.gov/cancer/uscs/dataviz/download_data.htm)

## Contributing

This project was developed as a collaborative effort. For questions or contributions, please contact any of the project contributors listed above.

## License

MIT License

---

*This project analyzes publicly available cancer surveillance data to support research and public health initiatives.*