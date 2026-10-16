# AC

# Business Understanding
## Business problem
Ice hockey teams, analysts, and management want to understand how teams might perform in the upcoming season and anticipate organizational changes.

Using the historical ice hockey data provided in this assignment, the goal is to develop machine learning models to predict the following for the target test season:
- **The final regular season ranking of teams:** Estimate the final standings of teams at the end of the upcoming regular season.
- **The set of teams that will change coaches:** Identify which teams are likely to change their head coach during the upcoming season.

## Business goal
The main objectives of this project are:

1. Predict the final regular-season ranking of each team in the target season.
2. Identify the teams most likely to change their head coach during the target season.
3. Evaluate the performance of different machine learning models to determine which models produce the most reliable predictions.
4. Use historical patterns to identify factors associated with team performance and coaching changes.
5. Ensure that all predictions are generated using only information available before the target season begins.

## Data Mining goal
| Business goal | Corresponding data mining goal |
|---------------|--------------------------------|
| 1. Predict the final regular-season ranking of each team. | Develop and evaluate machine learning models that predict the final regular-season ranking of each team using historical performance data and other relevant pre-season information. |
| 2. Identify teams likely to change their head coach. | Build a classification model that predicts whether each team will change its head coach during the target season, using historical coaching changes and relevant team performance indicators. |
| 3. Evaluate different machine learning models. | Compare the predictive performance of different algorithms using appropriate evaluation metrics and historical seasons that were not used for training. |
| 4. Identify factors associated with team performance and coaching changes. | Analyze historical data to identify which variables are associated with final team rankings and coaching changes. |
| 5. Ensure predictions use only information available before the season begins. | Establish a prediction cutoff date and construct the training and test datasets so that no information from after the prediction date is used as a predictor. |

## Business question
- Can we use historical ice hockey data to predict the final regular-season rankings of teams and identify which teams will change their head coach in the upcoming season?

## Success criteria
The project will be considered successful if the models can make useful predictions and demonstrate reasonable performance on historical seasons that were not used for training.

| Prediction task | Success criteria | Suggested evaluation metrics |
|-----------------|------------------|------------------------------|
| Final regular-season ranking | Predicted rankings are close to the actual final standings. | MAE of rank, Spearman rank correlation |
| Coaching changes | The model identifies teams that change coaches while limiting incorrect predictions. | Precision, recall, F1-score, PR-AUC |
| Third prediction task | To be determined when task (c) is announced. | To be determined based on the prediction objective. |

## Stakeholders
The project could be useful to several stakeholders:

- **Team management:** Gain insights into expected team performance and potential coaching instability.
- **Coaches:** Understand historical performance patterns and factors associated with success.
- **Sports analysts:** Produce data-driven forecasts of regular-season standings.

# Ice Hockey
## Basic Rules
Ice hockey is a team sport played on an ice rink. Two opposing teams use sticks to shoot a puck into the opponent's goal. The team that scores the most goals wins.

- **Players:** Each team has 6 players on the ice: 1 goaltender, 2 defensemen, and 3 forwards.
- **Game duration:** Three periods of 20 minutes each, totalling 60 minutes of regulation time.
- **Substitutions:** Players can be substituted during play.
- **Penalties:** Rule violations, such as tripping or hooking, can result in penalties that temporarily leave a team short-handed.
- **Overtime:** If a regular-season game is tied, overtime is played. In the NHL, a shootout determines the winner if overtime does not resolve the tie.

## Season Structure
Ice hockey seasons generally consist of two main phases:

- **Regular season:** Teams play scheduled games to accumulate points and qualify for the playoffs.
- **Playoffs:** Qualified teams compete in elimination series to determine the champion.

In the National Hockey League (NHL), there are 32 teams, and each normally plays 82 regular-season games. Teams are organized into conferences and divisions.

## Regular-Season Points and Rankings
In the NHL, teams earn points according to the outcome of each game:

| Result | Points |
| ------ | ------ |
| Win (regulation, overtime, or shootout) | 2 |
| Overtime or shootout loss | 1 |
| Regulation loss | 0 |

Teams are ranked primarily by their total points. Official tiebreaking rules determine the order when teams have equal points.

## Coaches and Coaching Changes
The head coach is responsible for team strategy, player management, training, and tactical decisions.

Coaching changes may occur because of poor performance, missed playoff qualification, management decisions, contract circumstances or personal reasons.

# Data Understanding
## Tables
- **Master:** Biographical details and career attributes for all players and coaches (e.g., height, weight, shooting/catching hand, debut/retirement years)
- **Scoring:** Player performance metrics (e.g., games played, goals, assists, penalty minutes)
- **Goalies:** Goaltender performance metrics (e.g., minutes played, wins, losses, goals against, saves/shots faced, shutouts)
- **Coaches:** Coaching statistics (e.g., games coached, wins, losses, ties, postseason performance)
- **Teams:** Team-level seasonal aggregates, standings, goal statistics, and playoff qualification status
- **TeamsHalf:** First half / second half standings
- **TeamSplits:** Team home/road performance metrics and monthly splits
- **TeamVsTeam:** Head-to-head records
- **ScoringShootout:** Individual performance metrics in shootouts
- **GoaliesShootout:** Goaltender performance metrics in shootouts
- **CombinedShutouts:** Logs of combined shutouts, recording the team, opponent, and involved goaltenders.
- **SeriesPost:** Outcome records (e.g., winning team, losing team, games won/lost) for the postseason playoff series
- **TeamsPost:** Team-level performance stats for the postseason playoff series
- **ScoringSC:** Player performance metrics in Stanley Cup finals
- **GoaliesSC:** Goaltender performance metrics in Stanley Cup finals
- **TeamsSC:** Team-level performance stats in Stanley Cup finals
- **AwardsPlayers:** Player awards, trophies, postseason all-star teams
- **AwardsCoaches:** Coaches awards, trophies, postseason all-star teams
- **AwardsMisc:** Miscellaneous awards
- **abbrev:** Abbreviations used in Teams and SeriesPost tables
- **HOF:** Hall of Fame information
- **ScoringSup:** Supplemental scoring statistics

## Glossary
- **playerID:** Player ID
- **coachID:** Coach ID
- **hofID:** Hall of Fame ID
- **legendsID:** ID at Legends Of Hockey (www.legendsofhockey.net)
- **ihdbID:** ID at the Internet Hockey Database
- **hrefID:** ID at Hockey-Reference.com
- **tmID:** Team ID
- **lgID:** League ID
- **franchID:** Franchise ID
- **confID:** Conference ID
- **divID:** Division ID
- **firstNHL:** First NHL season (2005-06 listed as "2005")
- **shootCatch:** Shooting hand (catching hand for goalies)
- **pos:** Position
- **stint:** order of appearance in a season
- **GP:** Games played
- **G:** Goals scored
    - Note: except in the "Coaches" and some team-related tables (i.e., "Teams", "TeamsHalf", "TeamsPost", and "TeamsSC" tables), where it stands for "Games"
- **A:** Assists
- **Pts:** Points
- **PIM:** Penalty minutes
- **PPG / PPA:** Power play goals / Power play assists
- **SHG / SHA:** Short-handed goals / Short-handed assists
- **W:** Wins
- **L:** Losses
- **T/OL:** Ties / Overtime losses
- **ENG:** Empty net goals
- **SHO:** Shutouts
- **GA / SA:** Goals against / Shots against
- **OTL:** Overtime losses
- **SoW / SoL:** Shootout wins / Shootout losses
- **SHF:** Shorthanded goals for
- **hW / rW:** Home wins / Road wins
- **JanW / JanL / JanT / JanOL:** January wins / losses / ties / overtime losses
- **R/P:** "R" for regular season, or "P" for postseason
- **GDG:** Game-deciding goals
- **S:** Shots
- **Type:** In ```abbrev.csv```, type refers to the type of thing that the abbreviation refers to

TODO: Compelete Glossary

## Missing Data per Table Before Changes
### abbrev.csv
No missing data.

### AwardsCoaches.csv
- Column ```note``` has no data

### AwardsMisc.csv
- 

# Data Preparation
## Remove Useless Data
- The ```note``` column in table ```AwardsCoaches.csv``` has no data! 

## Data to be manually added
- ...
