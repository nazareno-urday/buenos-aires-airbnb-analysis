<p align="center">
  <img src="assets/banner.svg" alt="Buenos Aires Short-Term Rentals: project banner with an abstract city skyline" width="100%">
</p>

# Buenos Aires Short-Term Rentals

An exploratory analysis of prices, hosts, and guest reviews in the Buenos Aires Airbnb market, using Python and pandas.

![Status: analysis in progress](https://img.shields.io/badge/status-analysis%20in%20progress-orange)
![Python](https://img.shields.io/badge/Python-3-blue)
![pandas](https://img.shields.io/badge/pandas-data%20analysis-150458)

## Overview

Short-term rentals sit at the intersection of tourism, housing, and small-scale entrepreneurship. This project uses public listing data to describe how the Buenos Aires market is structured: where supply is located, what drives differences in asking prices, how concentrated hosting is, and how much guest ratings actually reveal.

The data is messy by nature. Prices are stored as formatted text, amenities as embedded lists, and key fields have missing values. Cleaning and combining it is a central part of the project, and each decision is documented.

## Research Questions

1. How are supply and asking prices distributed across neighbourhoods and room types?
2. Do Superhosts differ significantly from other hosts in price and rating?
3. How concentrated is supply among hosts with many listings?
4. How has review activity evolved over time, and is there visible seasonality?
5. Which amenities are associated with higher prices after accounting for multiple comparisons?
6. How informative are guest ratings when most scores sit close to the maximum?

## Key Findings

*To be added when the analysis is complete.*

## Dataset

**Source:** [Inside Airbnb](https://insideairbnb.com/get-the-data/), Buenos Aires snapshot of 23 September 2026.

| File | Compressed size | Contents |
|---|---|---|
| `listings.csv.gz` | 18 MB | One row per listing, with 90 columns covering hosts, location, property, price, and review scores |
| `calendar.csv.gz` | 26 MB | Availability and stay limits by listing and date |
| `reviews.csv.gz` | 129 MB | Date and text of each guest review |

### Getting the data

The data is not stored in this repository, in line with Inside Airbnb's [request not to republish it](https://insideairbnb.com/data-policies/). To reproduce the analysis, download the three files from the Buenos Aires section of the [Inside Airbnb data page](https://insideairbnb.com/get-the-data/) into `data/raw/`, without decompressing them.

Inside Airbnb offers free data for the last 12 months. Once this snapshot is no longer listed, it must be requested through their archived data process, and a newer snapshot may give different results.

## Project Structure

```text
├── assets/         README images
├── data/
│   ├── raw/        Source files, not tracked by Git
│   └── processed/  Derived datasets, not tracked by Git
├── notebooks/      Analysis notebooks
├── reports/
│   └── figures/    Exported charts
└── pyproject.toml  Project metadata and dependencies
```

## Setup

Requires Python 3.13 or later. On Windows:

```powershell
python -m venv .venv
.venv\Scripts\python -m pip install -e ".[dev]"
.venv\Scripts\jupyter lab
```

## Approach

1. **Assess data quality:** inspect structure, data types, missing values, duplicates, and implausible values.
2. **Clean:** parse prices, dates, and amenities, then record how many listings each filter removes.
3. **Integrate:** merge listings, calendar, and review data by listing ID.
4. **Explore:** compare groups with descriptive statistics, group-by operations, and pivot tables.
5. **Test:** evaluate selected differences with t-tests, reporting effect sizes alongside p-values and limiting the risk of p-hacking.
6. **Interpret:** present conclusions together with their limitations.

## Skills Applied

- **Data wrangling:** pandas, NumPy, and regular expressions
- **Data integration:** merging and concatenating multiple tables
- **Aggregation:** group-by operations and pivot tables
- **Time series handling:** working with dates and periods
- **Statistics:** distributions, sampling, and hypothesis testing with SciPy
- **Critical analysis:** metric design, Goodhart's Law, and p-hacking awareness

## Visualizations

*To be added after completing* Applied Plotting, Charting & Data Representation in Python, *using Matplotlib.*

## Limitations

- Prices are asking prices quoted for specific dates, not amounts paid by guests.
- Currency must be verified during cleaning, and inflation limits comparisons of Argentine peso prices across time.
- Reviews approximate demand, but not every stay produces a review.
- An unavailable calendar day may be either booked or blocked by the host.
- Occupancy and revenue fields are estimates, not observed bookings.
- The snapshot only includes listings that were online when the data was collected, so past activity is subject to survivorship bias.
- Observed relationships are associations and are not interpreted as evidence of causation.

## Privacy

The source data includes the first names of hosts and reviewers. This project reports aggregated results and does not publish personal names or review text linked to individuals.

## Learning Context

This independent project applies concepts from the University of Michigan's *Introduction to Data Science in Python* on Coursera. It will be extended with visualizations informed by *Applied Plotting, Charting & Data Representation in Python*.

## Attribution

Data from [Inside Airbnb](https://insideairbnb.com/), licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). This project is independent and is not affiliated with or endorsed by Airbnb or Inside Airbnb.
