# Corporate Announcement Event Study

## Project Overview

This project analyzes how corporate announcements affect short-term stock returns and trading volume.

The analysis uses corporate announcement data and one-minute OHLCV market data for five Indian listed companies. The objective is to determine whether different announcement types are associated with meaningful short-term price and trading-activity responses.

The study evaluates market reactions over 5-minute, 30-minute, and 60-minute windows following the point at which an announcement becomes tradable.

---

## Business Questions

The analysis addresses five main questions:

1. Do corporate announcements generate significant short-term stock returns?
2. Does the market reaction differ across announcement types?
3. How does trading volume change following announcements?
4. Which return and volume effects remain significant after multiple-testing correction?
5. Are the observed return patterns robust to extreme observations?

---

## Dataset

The analysis uses:

- Corporate announcement records from BSE
- One-minute OHLCV market data
- Five stocks:
  - RELIANCE
  - HDFCBANK
  - NYKAA
  - RVNL
  - HAL

The original announcement dataset contains 2,530 announcements.

After event alignment, clustering, and independence filtering, the final analysis contains:

**1,743 independent events**

Each independent event has return observations at:

- 5 minutes
- 30 minutes
- 60 minutes

---

## Methodology

### 1. Data Validation

The analysis performs checks for:

- Missing values
- Duplicate announcement IDs
- Duplicate timestamps
- Invalid timestamps
- Invalid OHLC observations
- Zero-volume observations
- Incomplete event windows
- Announcement timestamp consistency

`DissemDT` is used as the primary dissemination timestamp and market data is aligned to the first complete one-minute bar at or after the event.

---

### 2. Event Identification and Clustering

Announcements occurring close together and potentially representing the same underlying corporate event are clustered to avoid treating related announcements as independent observations.

The analysis then retains one representative observation for each independent event.

Final dataset:

**1,743 independent events**

The final data-quality check confirms:

- 1,743 independent events
- 1,743 unique event IDs
- No missing values in the final return/volume analysis dataset
- No duplicate event IDs

---

## Announcement Taxonomy

Announcements are grouped into seven subject categories:

1. Analyst / Investor Communication
2. Business / Strategic / Media
3. Capital Actions
4. Corporate Governance / Management
5. Financial Results
6. Other Corporate Updates
7. Regulatory / Legal / Clarification

Event counts vary by category, with the largest group being Other Corporate Updates.

---

## Return Analysis

Short-term stock returns are measured over:

- 5 minutes
- 30 minutes
- 60 minutes

The analysis reports:

- Mean return
- Median return
- Sample size
- t-statistic
- p-value
- Adjusted p-value
- Statistical significance

### Main Return Findings

After Benjamini-Hochberg FDR correction:

#### Business / Strategic / Media

This category produced the strongest short-term positive return effect.

- 5-minute mean return: **+0.3704%**
- 30-minute mean return: **+0.3921%**
- 60-minute mean return: **+0.3705%**

The 5-minute and 30-minute effects remained statistically significant after FDR correction, while the 60-minute effect did not.

#### Other Corporate Updates

This category showed positive returns across all three horizons:

- 5-minute: **+0.2072%**
- 30-minute: **+0.2274%**
- 60-minute: **+0.2363%**

All three remained statistically significant after FDR correction.

#### Regulatory / Legal / Clarification

This category also showed positive returns:

- 5-minute: **+0.2423%**
- 30-minute: **+0.2506%**
- 60-minute: **+0.2769%**

All three horizons remained statistically significant after FDR correction.

#### Financial Results

Financial-result announcements showed positive average returns:

- 5-minute: **+0.1576%**
- 30-minute: **+0.1437%**
- 60-minute: **+0.0747%**

However, none of these return effects remained statistically significant after FDR correction.

#### Analyst / Investor Communication

Returns were slightly negative:

- 5-minute: **-0.0528%**
- 30-minute: **-0.0813%**
- 60-minute: **-0.0840%**

None were statistically significant after FDR correction.

#### Corporate Governance / Management

Returns were also negative:

- 5-minute: **-0.0839%**
- 30-minute: **-0.0566%**
- 60-minute: **-0.1335%**

None were statistically significant after FDR correction.

#### Capital Actions

Returns were positive but relatively small:

- 5-minute: **+0.1371%**
- 30-minute: **+0.1018%**
- 60-minute: **+0.0596%**

None remained statistically significant after FDR correction.

---

## Trading Volume Analysis

Trading activity is measured relative to a historical volume baseline using log volume ratios.

The analysis evaluates abnormal volume over the same:

- 5-minute
- 30-minute
- 60-minute

windows.

### Main Volume Findings

Several announcement categories showed statistically significant changes in trading volume.

Examples include:

- Financial Results: **+89.06%** at 5 minutes
- Financial Results: **+24.89%** at 30 minutes
- Regulatory / Legal / Clarification: **+50.33%** at 5 minutes
- Corporate Governance / Management: **+36.22%** at 5 minutes
- Other Corporate Updates: **+23.07%** at 5 minutes

Some categories showed declining volume at longer horizons.

For example:

- Capital Actions: **-8.64%** at 5 minutes, **-35.30%** at 30 minutes, **-44.45%** at 60 minutes
- Analyst / Investor Communication: **+0.77%** at 5 minutes, followed by **-27.00%** at 30 minutes and **-38.76%** at 60 minutes
- Other Corporate Updates: **+23.07%** at 5 minutes, followed by **-15.80%** at 30 minutes and **-28.12%** at 60 minutes

This indicates that volume responses are not uniform across announcement types or time horizons.

---

## Statistical Significance

Hypothesis tests are performed for subject-group and time-horizon combinations.

To control for multiple comparisons, the analysis applies the:

**Benjamini-Hochberg False Discovery Rate (FDR) correction**

A result is treated as statistically significant when the FDR-adjusted p-value is below 0.05.

The results show that statistical significance is much more consistent for trading-volume responses than for stock-return responses.

In particular, many volume effects remain significant after FDR correction, while only selected announcement categories show statistically significant return effects.

---

## Robustness Analysis

To assess sensitivity to extreme observations, the analysis applies 1% / 99% winsorization to the return distributions.

The comparison between original and winsorized means shows that the main return patterns are broadly stable.

For example:

- Regulatory / Legal / Clarification, 5-minute return:
  - Original mean: **+0.2423%**
  - Winsorized mean: **+0.2442%**

- Business / Strategic / Media, 30-minute return:
  - Original mean: **+0.3921%**
  - Winsorized mean: **+0.3914%**

- Other Corporate Updates, 5-minute return:
  - Original mean: **+0.2072%**
  - Winsorized mean: **+0.2073%**

This suggests that the major positive return patterns are not simply driven by a small number of extreme observations.

---

## Key Findings

1. **Announcement type matters.** Short-term return responses differ substantially across announcement categories.

2. **Business / Strategic / Media announcements showed the largest positive short-term returns**, with significant effects at 5 and 30 minutes after FDR correction.

3. **Other Corporate Updates produced positive and statistically significant returns across all three horizons.**

4. **Regulatory / Legal / Clarification announcements produced positive returns that increased from approximately 0.24% at 5 minutes to 0.28% at 60 minutes**, with all three horizons remaining significant after FDR correction.

5. **Financial Results generated a strong trading-volume response**, particularly at the 5-minute horizon, but their average return effects were not statistically significant after multiple-testing correction.

6. **Trading volume often reacted more strongly than price.** Several announcement categories showed significant volume changes even when their corresponding return effects were not statistically significant.

7. **Some categories showed an initial increase in volume followed by declining activity at longer horizons**, suggesting that trading activity can normalize after the immediate announcement window.

8. **The main return patterns were broadly robust to winsorization**, indicating that the observed effects were not entirely driven by extreme return observations.

---

## Limitations

- The analysis covers only five stocks.
- Results are specific to the supplied sample period and companies.
- Announcement categories are rule-based classifications and may contain heterogeneous events.
- Statistical significance does not establish causality.
- Market-wide movements and other simultaneous information may contribute to observed returns.
- Some subject groups have substantially fewer observations than others.
- The analysis focuses on short intraday horizons and should not automatically be generalized to longer-term investment behavior.
- The available data does not contain analyst earnings expectations or earnings-surprise measures, so surprise-based PEAD conclusions cannot be established from this dataset alone.

---

## Tools & Technologies

- Python
- Pandas
- NumPy
- SciPy
- Statsmodels
- Matplotlib
- Jupyter Notebook

---

## Project Structure

```text
corporate-announcement-event-study/
│
├── Corporate_Announcement_Event_Study_CLEAN.ipynb
├── README.md
├── .gitignore
│
└── data/
    ├── corporate_announcements.csv
    ├── corporate_announcements.jsonl
    ├── RELIANCE.csv
    ├── HDFCBANK.csv
    ├── NYKAA.csv
    ├── RVNL.csv
    ├── HAL.csv
    └── metadata.json
