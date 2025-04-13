# 🏀 College Basketball Archetypes

## Abstract

Team success in college basketball is based not only on the talent available on a team, but also on how players complement one another within a lineup. While advanced metrics exist for evaluating individual performance, less attention has been paid to how different player archetypes interact within a team structure. This project introduces a method for evaluating lineups based on the roles and archetypes of the players within them and the interactions seen. By analyzing offensive and defensive efficiency metrics across various team compositions, this study aims to identify which archetype combinations yield the highest performance. It also explores how teams match up against each other based on archetypal builds and differences. Unlike approaches that focus solely on raw talent or position, this largely is focused on efficiency — how a passing point guard might elevate a lob-threat power forward more than a shooting one, or how archetypal diversity within a lineup can influence matchup outcomes. These insights can inform coaching strategies and lineup optimization, offering another useful approach to building successful teams.

## Methodology 

The following pieces of data were pulled from the sites of Bart Torvik and Evan Miya (linked in Data Sources)
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
