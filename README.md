# Dashboard: US Flight Delays and Cancellations (2015)

**Project Goal:** Analyze the main reasons behind flight delays and cancellations in the US in 2015.  
**Data Source:** [Kaggle — US DOT Flight Delays Dataset](https://www.kaggle.com/datasets/usdot/flight-delays?select=flights.csv)

---

## What is this project?

This is a study project created during a data visualization course.  
The main task was to build an interactive Tableau dashboard to explore **key causes of flight delays and cancellations**, with filtering options by **time**, **airports**, **airlines**, and **states**.

---

## Why data preprocessing was necessary

The original dataset showed that a single flight may have **multiple delay reasons**.  
Tableau cannot natively handle such “one-to-many” relationships without prior transformation.

As an analyst, I chose to preprocess the data in **Python using Pandas** — a common and practical step when preparing datasets for dashboards.

---

## Data preparation steps in Pandas

The following transformations were applied:

- Created unique identifiers for each flight
- Extracted and normalized delay reasons, flight numbers, and delay time
- Created a dedicated table for the **Sankey diagram** (by month and delay type)
- Mapped numeric months to their textual names
- Sorted and exported final tables for Tableau

 *All steps can be reproduced in the notebook `data_preparation_for_dashboard.ipynb`.*

---

## Project structure

The project uses a simplified version of the original Kaggle data:

- `flights_light.csv` — simplified flight data  
- `airlines.csv` — airline reference  
- `airports.csv` — airport reference  

For Tableau integration:

- `airports.csv` is joined **twice** — once for departure, once for arrival  
- Each instance is renamed to avoid naming conflicts  
- Relationships between tables are manually configured in Tableau

_<img width="216" height="155" alt="Screenshot 2025-09-10 at 16 14 17" src="https://github.com/user-attachments/assets/b69144f4-84b8-4e0c-9ba8-687dafb57f17" />_

---

## What the dashboard shows

_<img width="1049" height="671" alt="Screenshot 2025-09-10 at 17 02 32" src="https://github.com/user-attachments/assets/ce78e558-97b2-4eeb-b80d-ca0c77c2c366" />_

The dashboard includes the following elements:

1. **Interactive Filter Panel**  
   Allows switching between delay and cancellation data via a parameter toggle, and filtering by airline, airport, state, date, year, month, and weekday.  
  
2. **Key Metrics**  
   Displays total number of flights, share of delays and cancellations, and share of delays over 15 minutes.  
   Monthly data is shown using line charts.

3. **“Taxi In vs Out” Diagram**  
   Compares average taxi-in and taxi-out time per month.

4. **Donut Chart: Delay/Cancellation Reasons**  
   Breakdown by cause: Late Aircraft, Airline, Weather, NAS, Security.  
   ⚠️ *Linked to the Delay/Cancellation selector.*

5. **Top 10 Airports by Incidents**  
   Horizontal bar chart sorted by number of delays or cancellations.  
   ⚠️ *Linked to the Delay/Cancellation selector.*

6. **Barplot: Delay & Cancellation Causes**  
   Comparison of delay/cancellation counts by category (Airline, Weather, etc.).  
   ⚠️ *Linked to the Delay/Cancellation selector.*

7. **“Airlines Delay & Cancellation” Chart**  
   Compares delay and cancellation rates per airline in a single chart.

8. **Delay vs Cancellation Over Time**  
   Combined chart showing average delay and cancellation share by month.

9. **US State Map**  
   Bubble map showing the number of incidents per state (size and color intensity).  
   ⚠️ *Linked to the Delay/Cancellation selector.*

10. **Heatmap: Delays & Cancellations**  
    Visualizes distribution by weekday and hour.  
    ⚠️ *Linked to the Delay/Cancellation selector.*

11. **Textual Explanation**  
    Helps users interpret the dashboard and understand key insights.

---

## Why this is useful

This visualization allows quick detection of:

- Problematic **airports** and time slots  
- Less reliable **airlines**  
- Dependency of **delays on time of day, day of week, or month**  
- Major **root causes** like weather, late arrivals, or operational issues

---

## Who may benefit from this project?

- **Junior analysts** — as a reference for data prep and dashboarding  
- **Airlines and airports** — as a prototype for issue monitoring  
- **HR & recruiters** — to evaluate Tableau, Python, and data skills

---

## How to use

1. Download the source data from Kaggle  
2. Run the notebook `data_preparation_for_dashboard.ipynb`  
3. Load prepared CSV files into Tableau  
4. Recreate table relationships (see diagram above)  
5. Explore the dashboard or customize it as needed

---

## 📍 Tableau Dashboard Link

[https://public.tableau.com/app/profile/olena.lytvynenko/viz/Project_Lytvynenko_Airlines_22/AirlineProblemDashboard?publish=yes](https://public.tableau.com/app/profile/olena.lytvynenko/viz/Project_Lytvynenko_Airlines_22/AirlineProblemDashboard?publish=yes)

---

## License

This project is published under the MIT license.  
You may reuse its structure, code, and ideas freely.  
**Original data is available on Kaggle**, the current dataset is a **reduced version** used for educational purposes.
