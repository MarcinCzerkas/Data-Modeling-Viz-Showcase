# Hotel Booking Analytics – Power BI Project

![Dashboard](/Assets/Dashboard.png)

## Project Overview

This project presents a Power BI dashboard built using a publicly available Kaggle dataset:
https://www.kaggle.com/datasets/mojtaba142/hotel-booking

The purpose of this project was not to build a highly complex analytical solution, but to demonstrate **how I approach a Power BI project end-to-end**:

- understanding and redefining business metrics in a new domain
- designing a clean dimensional data model
- performing structured ETL in Power Query
- implementing semantically correct DAX measures
- delivering a clear, decision-oriented dashboard

The dataset itself is relatively simple. The value of this project lies in the methodology and analytical discipline rather than dataset complexity.


---

## Business Context

The dataset describes booking behavior for two hotel types: City Hotel and Resort Hotel.

Since I do not have prior professional experience in the hotel industry, an important part of this project was adapting to a new set of business metrics. This required understanding how KPIs such as:

- ADR (Average Daily Rate)
- Revenue
- Cancellation Rate
- Booking Lead Time

should be interpreted and calculated correctly.

Rather than relying on naive aggregations, I reconstructed business logic directly from raw columns to ensure semantic correctness.


---

## Analytical Focus

The dashboard addresses three interconnected analytical areas:

1. Demand analysis
2. Cancellation risk factors
3. Comparison of the two hotels

The report is designed as a **single-page analytical view**, emphasizing:

- clarity over density
- minimal visual noise
- fast transition from observation to insight

The objective was to demonstrate structured analytical thinking and coherent storytelling rather than visual complexity.


---

## Technical Implementation

### ETL – Power Query

All data preparation was performed in Power Query. Key steps included:

- data type corrections
- column normalization and cleanup
- removal of redundant fields
- building dimension tables from a flat XLSX source
- creating a dedicated date table
- basic data quality validation

![ETL - Power Query](/Assets/PQ.png)

Each transformation step was deliberate and aligned with the final semantic model.


---

### Data Modeling

The data model follows dimensional modeling principles (Kimball-style approach):

- 1 fact table
- 5 dimension tables
- star schema structure

The date table plays three roles, with one active relationship and two inactive relationships handled using `USERELATIONSHIP()` where required.

![Data model](/Assets/data_model.png)

Modeling decisions were driven by semantic clarity, performance considerations, and future extensibility.


---

### DAX Measures

The project does not rely on highly complex DAX. Instead, it focuses on correct metric definition.

For example, ADR is a **non-additive metric** and must be calculated as a weighted average. A simple average of the `[adr]` column would be incorrect, so the measure reconstructs the appropriate business logic.


---

## Visualization & Data Storytelling

The dashboard was intentionally designed as a single page to:

- preserve analytical context
- prevent duplication of visuals
- maintain logical flow between business questions

A key design decision was separating booking date vs. arrival date analysis from revenue comparison using a toggle mechanism. This avoids visual overload while maintaining analytical continuity.

The storytelling structure follows a logical sequence:

- What is the demand?
- Where are the cancellation risks?
- How do the two hotels differ?
- What conclusions can be drawn?


---

## Insights

The analysis leads to the following conclusions:

- City Hotel generates higher revenue and attracts more customers, while also being more exposed to cancellation risk compared to Resort Hotel.
- Due to bookings made in advance, demand can be divided into two categories:
    - Demand by stay dates – the peak season is typically summer.
    - The period when the highest number of bookings is made – several months in advance, with the largest volume at the very beginning of the year (a potentially important insight for the marketing team in terms of advertising seasonality).
- The highest number of cancellations occurs in combination with the following factors:
    - Deposit type: non-refund (proportionally the highest number of cancellations)
    - Market segment: groups
    - Distribution channel: TA/TO
    - Customer type: transient
- The highest demand is for Room Type A and BB (Bed & Breakfast) meal plans.


---

## Scope & Limitations

- The analysis is based exclusively on historical data.
- No forecasting or predictive modeling was implemented.
- No cost data is available, so margin analysis is not possible.
- No information on overbooking or actual room capacity constraints.


---

## Purpose of the Project

This project serves as a practical showcase of how I work with Power BI, specifically:

- structured ETL
- disciplined dimensional modeling
- metric correctness
- analytical reasoning
- clear and coherent data storytelling

The dataset is intentionally simple. The objective was to provide a transparent example of methodology rather than technical complexity.
