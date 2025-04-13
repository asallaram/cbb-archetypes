# 🏀 College Basketball Archetypes

## Abstract

Team success in college basketball is based not only on the talent available on a team, but also on how players complement one another within a lineup. While advanced metrics exist for evaluating individual performance, less attention has been paid to how different player archetypes interact within a team structure. This project introduces a method for evaluating lineups based on the roles and archetypes of the players within them and the interactions seen. By analyzing offensive and defensive efficiency metrics across various team compositions, this study aims to identify which archetype combinations yield the highest performance. It also explores how teams match up against each other based on archetypal builds and differences. Unlike approaches that focus solely on raw talent or position, this largely is focused on efficiency — how a passing point guard might elevate a lob-threat power forward more than a shooting one, or how archetypal diversity within a lineup can influence matchup outcomes. These insights can inform coaching strategies and lineup optimization, offering another useful approach to building successful teams.

## Methodology 

- First, I gathered players from the consensus top 5 conferences of college basketball: ACC, Big 12, B10, Big East, SEC.
  - I only wanted to consider players that had played a marginal amount of their team's possessions in order for their impact on the team and their
    personal stats to be meaningful and not due to a small sample size. So players with atleast 475 possessions (team has the ball on offense) were selected.
  - Using the official position listed on ESPN for a player, I then further classified the players into the following categories with the following characteristics:
    - Pure PG- Guards with >25% assist rate and >20% usage rate.
      - Primarily a ball handler with mediocre shooting stats.
    - Scoring PG- Guard with >15% assist rate and above 40% shooting in either 2P shooting or 3P shooting(at least 50 shots taken).
      - A ball handler that is also efficient and above average at shooting.
    - Combo G- Guards with 10-15% assist rate but had above 40% shooting in either 2P or 3P shooting(at least 50 shots taken).
      - Lots of shooting guards fit into this criteria along with some play-making small forwards.
    - Wing G- Guards that didn't fit the criteria of Pure PG, Scoring PG, or Combo G.
      - Largely shooting guards that rarely passed the ball.
    - Wing F- Small Forwards and Power Forwards classified as wings by ESPN.
      - Largely 3 and D players that ESPN classified as wings.
    - Stretch 4- Power Forwards that took at least 50 3's.
      - While maybe not very accurate, players that averaged above 1 attempted 3 a game were given a Stretch 4 archetype.
    - Stretch PF/C- PF/C hybrids that took at least 35 3s and made them at a 30% rate.
      - PF/C that averaged above a 3 attempted a game, but I decided to give it a 30% accuracy rate to take out the outliers of some PF/C shooting largely because they were left open and not             being accurate.
    - Paint PF/C- PF/C that didn't stretch the floor.
      - PF/C that were the more prototypical definition of their positions.
    - Stretch C- Centers that took at least 35 3s and made them at a 30% rate.
      - C that averaged above a 3 attempted a game, but I decided to give it a 30% accuracy rate to take out the outliers of some C shooting largely because they were left open and not                   being accurate.
    - Paint C - Centers that didn't stretch the floor.
      - Centers that didn't stretch the floor. 
 
 - However, I felt that just the position didn't accurately convey the impact of certain players(i.e. top players compared to their average counterparts at a position). I decided to add markers     for the top offensive, defensive, and two-way players at positions. I also added a playmaker tag that allowed non-guards to be recognized as such. Cooper Flagg who had a 26.3% assist rate       would not be considered a PG, but his high assist rate conveys him as a play-making Stretch 4. 

## Data Sources

- https://barttorvik.com/trank.php#
- https://evanmiya.com/?player_ratings

## Goals

- Evaluate lineup performance through the idea of archetypes.
- Identify high-performing and underperforming archetype combinations.
- Offer predictive and strategic insights for recruiting, roster building, and in-game lineup decisions.

## 📊 Data Dictionary

### **1. `archetypes.csv`**
| Column         | Description                                                           |
|----------------|-----------------------------------------------------------------------|
| `Player`       | Full name of the player                                               |
| `Abbreviation` | Shortened player ID used across datasets                              |
| `OBPR`         | Offensive Box Plus/Minus Rating – measures offensive contribution     |
| `DBPR`         | Defensive Box Plus/Minus Rating – measures defensive contribution     |
| `Role`         | Manually defined player archetype (e.g. "Lob Threat PF", "3-and-D Wing") |
| `Team`         | College team the player is on                                         |

### **2. `lineup-efficiencies.csv`**
| Column               | Description                                                  |
|----------------------|--------------------------------------------------------------|
| `Lineup`             | 5-player lineup listed by abbreviation or name               |
| `Efficiency`         | Overall efficiency score of the lineup                       |
| `OBPR Avg`           | Average Offensive BPR of the lineup                          |
| `DBPR Avg`           | Average Defensive BPR of the lineup                          |
| `Archetype Composition` | Combined roles pulled from the archetypes tab             |

### **3. `matchups.csv`**
| Column           | Description                                                    |
|------------------|----------------------------------------------------------------|
| `Team A Lineup`  | The lineup for Team A                                          |
| `Team B Lineup`  | The lineup for Team B                                          |
| `Team A Score`   | Adjusted score or efficiency for Team A                        |
| `Team B Score`   | Adjusted score or efficiency for Team B                        |
| `Archetype Advantage` | Which team had the better archetype matchups              |

## Author

- Aneesh — [GitHub](https://github.com/asallaram)
