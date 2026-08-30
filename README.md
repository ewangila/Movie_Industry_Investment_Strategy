# Movie Industry Investment Strategy: A Data-Driven Approach to Production

**Author:** Eugin Wangila  

---

## Overview

The film industry offers massive financial upside, but production is inherently high-risk. A blockbuster can generate billions, while an expensive misfire can destroy capital.

**Core Investment Question:**  
Given limited production capital, which budgets, release windows, and genres offer the strongest opportunity for financial performance?

This analysis evaluates historical production budgets, worldwide box-office revenue, and IMDb audience ratings to uncover repeatable patterns for smarter production decisions.

---

## Business Problem

Studios often chase high-grossing blockbusters. However, the highest-grossing movie is not necessarily the most efficient investment.  

We evaluate success using two distinct metrics:

- **Net Profit**: Absolute dollars remaining after recovering the production budget  
- **Gross ROI**: How efficiently production capital was converted into revenue  

The goal is to provide actionable, data-driven recommendations for capital allocation.

---

## Data Understanding

Primary data sources used:

| Source              | File                          | Key Information                          |
|---------------------|-------------------------------|------------------------------------------|
| The Numbers         | `tn.movie_budgets.csv`        | Production budget, domestic & worldwide gross, release date |
| IMDb                | `im.db` (SQLite)              | Genres, average ratings, number of votes |
| Cleaned Datasets    | `final_cleaned_movie_data.csv`<br>`final_cleaned_movie_data_exploded.csv` | Merged & cleaned analysis-ready data |

**Scope**: Movies released from **2010 onwards** (to better match IMDb coverage and modern market conditions).

---

## Methodology

1. **Data Cleaning**
   - Standardized monetary columns (removed `$` and commas)
   - Extracted release month and year
   - Calculated `net_profit` and `gross_roi`
   - Filtered to post-2010 releases

2. **Feature Engineering**
   - Exploded multi-genre films into individual rows for genre-level analysis
   - Merged financial data with IMDb ratings and genres (title-based matching)

3. **Analysis Focus Areas**
   - Release timing impact on box-office performance
   - Genre-level median Gross ROI
   - Relationship between production budget and worldwide gross
   - Relationship between production budget and IMDb ratings

---

## Key Findings

### 1. Release Timing Matters
Certain months consistently show stronger box-office potential (particularly early summer and late year). Revenue timing must be paired with cost-efficiency.

### 2. Genre Efficiency
Using **median Gross ROI** (to reduce blockbuster skew), the highest-performing genres include:

- Animation  
- Sci-Fi  
- Adventure  
- Mystery  

These genres deliver stronger capital efficiency compared to many high-budget action titles.

### 3. Budget vs. Revenue
There is a positive relationship between production budget and worldwide gross. Larger budgets raise the revenue ceiling, but they also increase capital exposure and do **not** eliminate uncertainty.

### 4. Budget vs. Audience Reception
Correlation between production budget and IMDb rating is near zero.  
**Business implication**: Higher production costs should not be treated as a reliable proxy for higher audience satisfaction.

---

## Strategic Recommendations

| Investment Dimension   | Analytical Signal                                      | Strategic Recommendation                     |
|------------------------|--------------------------------------------------------|----------------------------------------------|
| **Genre**              | Animation, Mystery & Adventure deliver higher median ROI | Prioritize high-efficiency genres            |
| **Release Timing**     | Certain months show stronger box-office potential      | Target high-demand release windows           |
| **Production Budget**  | Larger budgets increase exposure without guaranteed returns | Maintain disciplined spending                |
| **Audience Reception** | Budget has near-zero correlation with ratings          | Do not equate cost with quality              |
| **ROI Focus**          | Revenue scale ≠ investment efficiency                  | Optimize for capital efficiency              |

> **Final Investment Thesis**  
> The strongest movie investment strategy is not to spend the most — it is to spend **intelligently**.

---

## Interactive Dashboard

[→ Open Interactive Tableau Dashboard](https://public.tableau.com/app/profile/eugin.wangila/viz/BoxOfficeDynamics/BoxOfficeDynamicsBudgetsGenresandRatings)

---

## Limitations

- Matching between financial data and IMDb was performed on **movie titles**, which can introduce mismatches due to duplicate titles, spelling variations, or different versions of films.
- Gross ROI calculation excludes marketing (P&A), distribution fees, theater revenue shares, and streaming backend revenue.
- Results should be interpreted as **directional evidence** rather than definitive accounting for every film.

---

## Next Steps

A second-stage predictive model could estimate expected return of a proposed film by incorporating:

- Marketing budgets  
- Franchise / sequel status  
- Director & cast historical performance  
- Studio track record  
- Competitive release landscape  
- Inflation-adjusted revenue

---

## Repository Structure

```text
Movie_Industry_Investment_Strategy/
├── data/
│   ├── final_cleaned_movie_data.csv           # Cleaned merged dataset
│   ├── final_cleaned_movie_data_exploded.csv  # Genre-exploded version
│   └── tn.movie_budgets.csv                   # Source budget data
├── Project_notebook.ipynb                     # Full analysis notebook
├── Movie_Analysis_Executive.pdf               # Executive summary PDF
├── requirements.txt                           # Python dependencies
├── LICENSE                                    # MIT License
├── .gitignore
└── README.md
```

---

## How to Reproduce

1. Clone the repository  
2. Install required packages (`pandas`, `matplotlib`, `seaborn`, `sqlite3`)  
3. Ensure `im.db` is available locally (not tracked due to size)  
4. Run `Project_notebook.ipynb` top to bottom

---

## Technologies Used

- Python 3  
- Pandas  
- Matplotlib & Seaborn  
- SQLite  

---
## Limitations

* Matching between financial data and IMDb was performed on movie titles, which can introduce mismatches due to duplicate titles, spelling variations, or different versions of films.
* Gross ROI calculation excludes marketing (P&A), distribution fees, theater revenue shares, and streaming backend revenue.
* Results should be interpreted as directional evidence rather than definitive accounting for every film.

## Next Steps

A second-stage predictive model could estimate expected return of a proposed film by incorporating:

* Marketing budgets
* Franchise / sequel status
* Director & cast historical performance
* Studio track record
* Competitive release landscape
* Inflation-adjusted revenue

## License

This project is licensed under the MIT License – see the [LICENSE](LICENSE) file for details.

**Author:** Eugin Wangila  
[GitHub](https://github.com/ewangila)
