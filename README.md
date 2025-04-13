# 🏀 College Basketball Archetypes

## Abstract

Team success in college basketball is based not only on the talent available on a team, but also on how players complement one another within a lineup. While advanced metrics exist for evaluating individual performance, less attention has been paid to how different player archetypes interact within a team structure. This project introduces a method for evaluating lineups based on the roles and archetypes of the players within them and the interactions seen. By analyzing offensive and defensive efficiency metrics across various team compositions, this study aims to identify which archetype combinations yield the highest performance. It also explores how teams match up against each other based on archetypal builds and differences. Unlike approaches that focus solely on raw talent or position, this largely is focused on efficiency — how a passing point guard might elevate a lob-threat power forward more than a shooting one, or how archetypal diversity within a lineup can influence matchup outcomes. These insights can inform coaching strategies and lineup optimization, offering another useful approach to building successful teams.

## Methodology 

- First, I gathered players from the consensus top 5 conferences of college basketball: ACC, Big 12, B10, Big East, SEC
  - I only wanted to consider players that had played a marginal amount of their team's possessions in order for their impact on the team and their
    personal stats to be meaningful and not due to a small sample size. So players with atleast 475 possessions (team has the ball on offense) and a 20% usage rate(played at least 20% of their       team's overall possessions) were selected.
  - Using the official position listed on ESPN for a player, I then further classified the players into the following categories with the following characteristics
  - 

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
