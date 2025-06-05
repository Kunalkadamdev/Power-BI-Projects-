
# 🏏 ESPN Cricket Data 1971-2025 Power BI Dashboard

📌 Problem Statement


The goal was to extract player performance data (batting, bowling, fielding) from the ESPN Cricinfo website and visualize it using Power BI. This dashboard provides insights into individual cricket players’ statistics over defined career spans.


🧾 Steps Followed

Source: ESPN Cricinfo Stats - https://stats.espncricinfo.com/ci/engine/stats/index.html?class=2;type=batting

Step 1 - Open Power BI Use Get Data → WebPaste ESPN URL and append page=1 at the end.

Step 2 - Use “Add Table Using Example” from the navigator.Paste data from the first and second rows of the web page.

Step 3 - Click Transform Data after automatic population of table.
Step 4 Convert the table to a function.Open Advanced Editor and modify:(pagetext as text) =>Update source to:page="&pagetext&"Ensure there are no syntax errors.

Step 5 - Create a Blank Query.Use code: ={1..3}Convert values to Text, then use Invoke Function.

Step 6 - Expand all tables into one table using Expand Button.Append headers manually in a new table → Use “Append Queries”.Click Use First Row as Headers.

Step 7 - Format all columns to the correct data types (e.g., decimal, whole number.

Step 8 - Create three report pages:- Batting- Bowling- FieldingAdd Player Filter (Slicer) to each page.


📸 Snapshots

Batting Page:

![Image](https://github.com/user-attachments/assets/a79a3873-d154-4def-8637-18f1c1e1aff5)

Bowling Page:

![Image](https://github.com/user-attachments/assets/64d1a04a-8f07-4d47-85a7-b3476d24ba6a)


Fielding Page:

![Image](https://github.com/user-attachments/assets/53aba5b1-508c-4e99-9f31-aed3fa4896bd)


🧠 Advanced Calculations

Strike Rate Category (Using LOOKUPVALUE() to group players)

Ranking (Using RANKX() with ALL() to avoid filter context)

Deviation of Runs:= ABS(SUM(Batting[Runs]) - AVERAGE(Batting[Runs]))
Squared Deviation:= POWER(SUM(Batting[Runs]) - AVERAGE(Batting[Runs]), 2)


⚠ Note on Zero Values

Some data fields like Stumpings or 5-Wicket hauls may contain zeros. These represent non-applicable metrics for the specific player and are excluded from average calculations.

📊 Data Dictionary

🔷 Batting Table

| Column Name | Description                       |
| ----------- | --------------------------------- |
| Player      | Name of the batsman               |
| Span        | Career duration (e.g., 2005–2019) |
| Mat         | Total matches played              |
| Inns        | Total innings batted              |
| NO          | Not outs                          |
| Runs        | Total runs scored                 |
| HS          | Highest score                     |
| Ave         | Batting average (Runs/Outs)       |
| BF          | Balls faced                       |
| SR          | Strike rate (Runs/100 balls)      |
| 100         | Centuries scored                  |
| 50          | Half-centuries scored             |
| 0           | Ducks (score of 0)                |
| 4s          | Fours hit                         |
| 6s          | Sixes hit                         |



🔷 Bowling Table

| Column Name | Description                         |
| ----------- | ----------------------------------- |
| Player      | Name of the bowler                  |
| Span        | Career duration                     |
| Mat         | Matches played                      |
| Inns        | Innings bowled                      |
| Overs       | Total overs bowled                  |
| Mdns        | Maiden overs bowled                 |
| Runs        | Runs conceded                       |
| Wkts        | Wickets taken                       |
| BBI         | Best bowling in innings (Wkts/Runs) |
| Ave         | Bowling average (Runs/Wkts)         |
| Econ        | Economy rate (Runs/Overs)           |
| SR          | Strike rate (Balls/Wkt)             |
| 4           | 4-wicket hauls                      |
| 5           | 5-wicket hauls                      |


🔷 Fielding Table


| Column Name | Description                |
| ----------- | -------------------------- |
| Player      | Name of the player         |
| Span        | Career duration            |
| Mat         | Matches played             |
| Inns        | Innings fielded            |
| Dis         | Total dismissals (Ct + St) |
| Ct          | Catches taken              |
| St          | Stumpings                  |
| Ct Wk       | Catches as Wicketkeeper    |
| Ct Fi       | Catches as Fielder         |
| MD          | Match Days                 |
| D/I         | Dismissals per innings     |
