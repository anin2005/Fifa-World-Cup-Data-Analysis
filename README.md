# FIFA World Cup Data Analysis

## Project Overview

This project aims to analyze the FIFA World Cup dataset to uncover key metrics and factors that influence the outcomes of the World Cup tournaments. The analysis includes examining various aspects such as goals scored, match attendance, and team performances across different World Cups. The project utilizes three datasets: World Cup Matches, World Cup Players, and World Cups.

## Datasets

### 1. WorldCupMatches.csv
Contains information about the matches played in World Cups.

**Columns:**
- Year
- Datetime
- Stage
- Stadium
- City
- Home Team Name
- Home Team Goals
- Away Team Goals
- Away Team Name
- Win conditions
- Attendance
- Half-time Home Goals
- Half-time Away Goals
- Referee
- Assistant 1
- Assistant 2
- RoundID
- MatchID
- Home Team Initials
- Away Team Initials

### 2. WorldCupPlayers.csv
Contains information about the players who participated in the World Cups.

**Columns:**
- (Columns relevant to player performance and participation)

### 3. WorldCups.csv
Contains summary information about each World Cup.

**Columns:**
- Year
- Country
- Winner
- Runners-Up
- Third
- Fourth
- GoalsScored
- QualifiedTeams
- MatchesPlayed
- Attendance

## Key Analyses

### 1. Goals Scored Analysis
- Total goals scored by each team across all World Cups.
- Goals scored by winning teams.

### 2. Attendance Analysis
- Average attendance per match.
- Total attendance for each World Cup.

### 3. Match Outcomes Analysis
- Win rates for teams.
- Stage-wise performance of teams.

## Project Setup

### Requirements
- Python 3.x
- Pandas
- Matplotlib
- Seaborn

### Installation
1. Clone the repository:
   ```sh
   git clone https://github.com/your-username/fifa-world-cup-analysis.git
   cd fifa-world-cup-analysis
   ```

2. Install the required packages:
   ```sh
   pip install pandas matplotlib seaborn
   ```

### Usage
1. Mount Google Drive (if using Google Colab):
   ```python
   from google.colab import drive
   drive.mount('/content/drive')
   ```

2. Load the datasets:
   ```python
   import pandas as pd

   world_cup_matches = pd.read_csv('/content/drive/MyDrive/Colab Notebooks/WorldCupMatches.csv')
   world_cup_players = pd.read_csv('/content/drive/MyDrive/Colab Notebooks/WorldCupPlayers.csv')
   world_cups = pd.read_csv('/content/drive/MyDrive/Colab Notebooks/WorldCups.csv')
   ```

3. Perform analysis:
   ```python
   # Clean and preprocess data as needed
   world_cup_matches['Datetime'] = world_cup_matches['Datetime'].str.strip()
   world_cup_matches['Year'] = pd.to_datetime(world_cup_matches['Datetime'], format='%d %B %Y - %H:%M').dt.year
   combined_data = pd.merge(world_cup_matches, world_cups, on='Year', suffixes=('_match', '_cup'))

   # Example analysis: Total goals scored by each team
   home_goals = combined_data.groupby('Home Team Name')['Home Team Goals'].sum()
   away_goals = combined_data.groupby('Away Team Name')['Away Team Goals'].sum()
   total_goals = home_goals.add(away_goals, fill_value=0).sort_values(ascending=False)
   print(total_goals)

   # Plot total goals scored by each team
   import matplotlib.pyplot as plt

   total_goals.plot(kind='bar', figsize=(15, 7))
   plt.title('Total Goals Scored by Each Team in World Cups')
   plt.xlabel('Team')
   plt.ylabel('Total Goals')
   plt.show()
   ```

## Results

- **Goals Scored Analysis:** Identified the top goal-scoring teams in World Cup history.
- **Attendance Analysis:** Determined average and total attendance figures for World Cups.
- **Match Outcomes Analysis:** Analyzed win rates and stage-wise performances of teams.

## Conclusion

This project provides valuable insights into the performance and characteristics of teams and matches in the FIFA World Cups. The analyses help in understanding the key factors that contribute to winning the World Cup.

## Future Work

- Incorporate more advanced metrics like player statistics and performance indicators.
- Explore predictive modeling to forecast future World Cup outcomes.
- Expand the analysis to include more in-depth visualizations and interactive dashboards.

## Contact

For any questions or suggestions, please feel free to reach out:

- Email: dasaninda62@gmail.com 
- LinkedIn: [Aninda Das](https://www.linkedin.com/in/anindadas05)
