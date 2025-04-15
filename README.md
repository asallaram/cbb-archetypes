# College Basketball Archetypes

## Abstract

Team success in college basketball is based not only on the talent available on a team, but also on how players complement one another within a lineup. While advanced metrics exist for evaluating individual performance, less attention has been paid to how different player archetypes interact within a team structure. This project introduces a method for evaluating lineups based on the roles and archetypes of the players within them and the interactions seen. By analyzing offensive and defensive efficiency metrics across various team compositions, this study aims to identify which archetype combinations yield the highest performance. It also explores how teams match up against each other based on archetypal builds and differences. Unlike approaches that focus solely on raw talent or position, this largely is focused on efficiency — how a passing point guard might elevate a lob-threat power forward more than a shooting one, or how archetypal diversity within a lineup can influence matchup outcomes. These insights can inform coaching strategies and lineup optimization, offering another useful approach to building successful teams.

## Data Collection, Cleaning, and Archetype Tagging 

- First, I gathered players from the consensus top 5 conferences of college basketball: ACC, Big 12, B10, Big East, SEC.
  - I only wanted to consider players that had played a marginal amount of their team's possessions in order for their impact on the team and their
    personal stats to be meaningful and not due to a small sample size. So players with atleast 475 possessions (team has the ball on offense) were selected. The assist% and usage% were taken        from Bart Torvik
  - Using the official position listed on ESPN for a player, I then further classified the players into the following categories with the following characteristics:
    - Pure PG- Guards with >25% assist rate and >20% usage rate.
      - Primarily a ball handler with mediocre shooting stats.
    - Scoring PG- Guard with >15% assist rate and above 40% shooting in either 2P shooting or 3P shooting(at least 50 shots taken).
      - A ball handler that is also efficient and above average at shooting.
    - Combo G- Guards with 10-15% assist rate but had above 40% shooting in either 2P or 3P shooting(at least 50 shots taken).
      - Lots of shooting guards fit into this criteria along with some play-making small forwards.
    - Wing G- Guards that didn't fit the criteria of Pure PG, Scoring PG, or Combo G.
      - Primarily off-ball guards with low assist rates.
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
 - However, I felt that just the position didn't accurately convey the impact of certain players(i.e. top players compared to their average counterparts at a position). I decided to add markers     for the top offensive, defensive, and two-way players at positions. I also considered adding a playmaker tag that allowed non-guards to be recognized as such. Cooper Flagg who had a 26.3%   
   assist rate would not be considered a PG, but his high assist rate would convey him as a play-making Stretch 4. However, I found that through modeling the play-making tag was often having the same effect as the offensive tag and so the tag was not included. 
    - Offensive- Players in the top 0.5 standard deviations above the mean(~32%) of the obpr(Offensive Bayesian Performance Ratings from Evan Miya) were given an offensive tag.
      - "Offensive Wing G"- Further establish this player as an impactful offensive Wing G compared to other players his position.
    - Defensive- Players in the top 0.5 standard deviations above the mean(~32%) of the dbpr(Defensive Bayesian Performance Ratings from Evan Miya) were given a defensive tag.
      - "Defensive C"- Further establish this player as an impactful defensive Center compared to other players his position.
    - 2-Way- Players in the top 0.5 standard deviations in both obpr and dbpr.
      - "2-Way Stretch 4"- Further establish this player as an impact offensive and defensive Stretch 4 compared to other players his position.
 - I then collected line-ups for each P5 team that played atleast 150 possessions together. While some line-ups were thrown out due to some players not meeting the possessions cateogory above, I was able to find 668 line-ups total.
 - I created one lineup that included players tagged as Offensive, Defensive, or Two-Way, and another lineup without those tags. Naturally, a lineup filled with highly effective, tagged players is expected to perform well—so I used that as a benchmark to explore which combinations of tags and positions contribute most to team success. The untagged (or normal) lineup was primarily used to test the most effective archetypal builds, matchup advantages, and other lineup-related metrics.
    

## Data Sources
- https://barttorvik.com/trank.php#
- https://evanmiya.com/?player_ratings

## Goals

- Identify high-performing and underperforming archetype combinations and examine how these do in-game in terms of bayesian rating.
- Examine which archetypes(tagged) are most frequent in the top and bottom bpr line-ups.

## Data Dictionary (all in archetypes.csv

### **1. `archetypes tab`**
|   Column              | Description(Assist%/Usage% found in assist-to-stats tab)                        |
|-----------------------|---------------------------------------------------------------------------------|
| `Class`               | Player’s academic year (e.g., Freshman, Sophomore)                              |
| `Player`              | Full name of the player                                                         |
| `Player Abbreviation` | Unique player ID used across datasets                                           |
| `Team`                | College team the player is on                                                   |
| `Conference`          | Player's conference (e.g., ACC, Big Ten)                                        |
| `Role`                | Player archetype (e.g., "Lob Threat PF", "3-and-D Wing") with tags("2-way")      |
| `Min %`               | Percentage of team minutes the player is on the court                           |
| `Plus-Minus Average`  | Average on/off court plus-minus rating across all games                         |
| `Usage %`             | Usage rate — percentage of team possessions used by the player while on court   |
| `2P`                  | Number of 2-point field goals made                                               |
| `2P%`                 | 2-point field goal percentage                                                    |
| `3P`                  | Number of 3-point field goals made                                               |
| `3P%`                 | 3-point field goal percentage                                                    |
| `obpr`                | Offensive Bayesian Performance Rating from EvanMiya                             |
| `dbpr`                | Defensive Bayesian Performance Rating from EvanMiya                             |
| `Reference Roll`      | Official ESPN-listed position for the player                                    |
| `Tag Roll`            | Roll before tags("2-way") were assigned                                         |


### **2. `team-stats tab`**

| Column                   | Description (Evan Miya stats)                                 |
|--------------------------|--------------------------------------------------------------|
| `Rank`                   | National rank of the team                                     |
| `Team`                   | Name of the college team                                      |
| `Conference`             | Conference the team belongs to                                |
| `team_obpr`              | Team's overall Offensive Bayesian Performance Rating (OBPR)   |
| `team_dbpr`              | Team's overall Defensive Bayesian Performance Rating (DBPR)   |
| `team_bpr`               | Combined OBPR and DBPR for total performance rating           |
| `off_rank`               | Offensive ranking among all teams                             |
| `def_rank`               | Defensive ranking among all teams                             |
| `tempo`                  | Estimated possessions per game                                |
| `tempo_rank`             | Tempo ranking among all teams                                 |
| `home_rank`              | Performance ranking in home games                             |
| `roster_rank`            | Ranking based on team roster strength                         |
| `runs_per_game`          | Average point differential runs per game                      |
| `runs_conceded_per_game` | Average point differential runs allowed per game              |
| `runs_margin`            | Average margin between runs scored and runs conceded          |
| `runs_total`             | Total point differential runs scored                          |
| `runs_conceded_total`    | Total point differential runs conceded                        |
| `wins`                   | Total number of wins                                          |
| `losses`                 | Total number of losses                                        |


### **3. `lineup-efficiency tab`**

| Column                            | Description(Evan Miya Stats)                                                |
|-----------------------------------|-----------------------------------------------------------------------------|
| `Lineup`                          | List of players in the lineup                                              |
| `Lineup archetypes`               | Archetype types for players in the lineup                                  |
| `Lineup archetypes(considering efficiency)` | Archetypes weighted by tags(off,def,2-way)                       |
| `Team`                            | The team that used the lineup                                              |
| `Conference`                      | The conference the team belongs to                                         |
| `adj_team_off_eff`               | Adjusted team offensive efficiency                                          |
| `adj_team_def_eff`               | Adjusted team defensive efficiency                                          |
| `adj_team_eff_margin`            | Adjusted efficiency margin (off - def)                                     |
| `off_poss`                        | Number of offensive possessions during the lineup                          |
| `def_poss`                        | Number of defensive possessions during the lineup                          |
| `plus_minus`                      | Point differential while this lineup was on the floor                      |
| `avg_opp_bpr`                     | Average Bayesian Performance Rating of opposing lineups                    |
| `team_off_eff`                    | Raw team offensive efficiency during this lineup                           |
| `team_def_eff`                    | Raw team defensive efficiency during this lineup                           |
| `team_eff_margin`                 | Raw efficiency margin (off - def) during this lineup                       |


## Author

- Aneesh — [GitHub](https://github.com/asallaram)
