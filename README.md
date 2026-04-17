# ESG Quintile Portfolio Sorting Dashboard — MSCI World IMI (2019–2026)

> An interactive research dashboard accompanying the DBA dissertation
> *Beyond Ratings: Narratives and Numbers of ESG Data in Sustainable Investing*
> at Sheffield Hallam University.

**Live dashboard:** [https://<your-username>.github.io/<repo-name>/](https://example.com)
(update after GitHub Pages deployment)

---

## Abstract

This repository hosts an interactive visualisation of equal-weight and
market-weight quintile portfolio sorting results for MSCI World IMI
constituents across sixteen ESG, climate, and sustainability factors
between July 2019 and March 2026. Portfolios are formed annually at each
30 June sorting date and held for twelve months using active local
returns. The dashboard reports cumulative and annualised returns, Sharpe
and Sortino ratios (MAR = 0%), volatility, and maximum drawdown for each
quintile, alongside Q5−Q1 long-short spreads.

The dashboard supports the empirical component of the author's DBA
dissertation, which investigates the dissociation between ESG rating
narratives and quantitative return signals across distinct market
regimes (COVID-19, regulatory expansion, inflation and rate shocks,
tariff volatility, and the 2026 Iran conflict).

## Author

Niklas Sain — Doctor of Business Administration candidate, Sheffield
Hallam University, United Kingdom. Professional affiliation: MSCI Inc.
(DACH institutional ESG sales, Vice President).

## Methodology

### Universe and sorting

- **Investment universe:** MSCI World IMI constituents (developed-markets
  large-, mid-, and small-cap equities), approximately 5,100–6,140
  securities per month.
- **Sorting frequency:** annual, on 30 June of each year from 2019
  through 2025, producing seven holding periods (the final period,
  2025/26, is partially observed at the time of this release and covers
  July 2025 through March 2026).
- **Quintile construction:** `pd.qcut` with five equal-count bins.
  - ESG Score, Controversies, and Sustainable Impact Revenue are sorted
    on the global cross-section (simple sort).
  - Environmental, Social, and Governance pillars, Implied Temperature
    Rise (ITR), and Climate Value-at-Risk (ClimateVaR 1.5 °C) are sorted
    within GICS industries (industry-neutral sort).
  - For ITR, quintile labels are reversed so that Q5 represents the
    lowest-temperature (best) portfolio.
  - Controversies and Sustainable Impact Revenue distributions are
    highly concentrated; the procedure yields two and three effective
    groups respectively rather than five.
- **Weighting:** equal-weight (EW) and market-weight (MW) portfolios are
  constructed separately for each factor.

### Return calculation

Monthly holdings use **MSCI Active Local Returns**, which remove
foreign-exchange effects and express performance net of the benchmark.
Annual returns are geometrically compounded across the twelve holding
months. For the partial period 2025/26 YTD, nine-month returns are
annualised as (1+r)^(12/9)−1.

### Risk statistics

- **Annualised volatility:** monthly return standard deviation × √12.
- **Sharpe ratio:** annualised excess-of-zero mean return divided by
  annualised volatility (risk-free rate assumed zero; this is the
  convention in the factor-sorting literature and avoids time-varying
  rate noise).
- **Sortino ratio:** mean annualised return divided by annualised
  downside deviation, where downside deviation is computed against a
  minimum acceptable return (MAR) of zero, following Sortino & Price
  (1994).
- **Maximum drawdown:** peak-to-trough cumulative return decline within
  each holding period.

### Long-short portfolios

The Q5 − Q1 long-short portfolio is formed from monthly return
differences between the top and bottom quintiles. All reported long-short
statistics use these monthly differences as inputs.

## Data Sources and Licensing

All data are sourced from **MSCI Inc.** proprietary datasets accessed
under a research-use agreement:

- MSCI World IMI constituent holdings and weights
- MSCI ESG Ratings (Final Industry-Adjusted Company Score, E/S/G pillar
  scores, Controversy Score)
- MSCI ESG Sustainable Impact Metrics (SI Revenue)
- MSCI Climate Metrics (ITR, ClimateVaR 1.5 °C)
- MSCI Global Portfolio Performance (Active Local Returns)

The raw MSCI data are not redistributed in this repository. The
dashboard displays aggregated quintile-level statistics only, which
constitutes derivative research output. Redistribution, reproduction, or
commercial use of MSCI underlying data is prohibited without separate
written permission from MSCI Inc.

Use of MSCI data in this repository has been reviewed and approved by
MSCI Inc. for the purpose of academic dissertation research at Sheffield
Hallam University.

## Repository Contents

```
.
├── index.html                # Interactive dashboard (v4, July 2025 – March 2026 YTD)
├── README.md                 # This file
└── LICENSE                   # Code license (MIT); data licensing above
```

## Technical Notes

The dashboard is a single-file HTML artefact with no server dependency.
Chart rendering is powered by Chart.js, loaded from a public CDN. The
file runs in any modern browser (Chrome, Firefox, Safari, Edge) and
requires an active internet connection for chart rendering.

To run locally, open `index.html` in a browser; no build step is
required.

## Versioning

- **v1–v3** (internal): incremental development with progressively
  broader factor coverage.
- **v4** (this release): sixteen factors across seven holding periods,
  Sharpe and Sortino ratios, partial 2025/26 period through March 2026.
- **v5** (planned, mid-2026): complete 2025/26 holding period upon
  receipt of April–June 2026 return data.

## Citation

If you refer to this dashboard in academic work, please cite as:

> Sain, N. (2026). *ESG Quintile Portfolio Sorting Dashboard: MSCI World
> IMI (2019–2026)* (Version v4) [Interactive visualisation]. Zenodo.
> https://doi.org/10.5281/zenodo.XXXXXXX

(DOI placeholder — to be populated following Zenodo release.)

## Related Dissertation Output

Sain, N. (forthcoming). *Beyond Ratings: Narratives and Numbers of ESG
Data in Sustainable Investing* [Doctoral dissertation, Sheffield Hallam
University].

## Acknowledgements

The author thanks the Sheffield Hallam University DBA supervisory team
for methodological guidance, and MSCI Inc. for data access and approval
to publish aggregated research output.

## Disclaimer

The views, interpretations, and conclusions expressed in this repository
and the accompanying dashboard are solely those of the author in his
personal academic capacity and do not represent the views, positions, or
official output of MSCI Inc. or any of its affiliates. Nothing in this
repository constitutes investment advice.

## License

The dashboard code in this repository is released under the MIT License
(see `LICENSE`). The underlying MSCI data are not released under any
open licence and remain the property of MSCI Inc.

---

*Last updated: April 2026*
