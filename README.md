# Football Event Data Analysis and Visualization

This repository contains a comprehensive project for analyzing and visualizing football (soccer) event data. By leveraging StatsBomb JSON event files, the project extracts detailed information on shots, passing networks, defensive actions, and player movements. The code generates a variety of visualizations—from heatmaps and movement trajectories to network graphs and zone distributions—to provide deep insights into team tactics and individual player performance.

---

## Table of Contents

- [Overview](#overview)
- [Data Source](#data-source)
- [Project Structure](#project-structure)
  - [Shots Analysis](#shots-analysis)
  - [Passing Network and Defensive Analysis](#passing-network-and-defensive-analysis)
  - [Player Movement and Positioning Analysis](#player-movement-and-positioning-analysis)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

---

## Overview

This project processes football match event data to extract key tactical and performance insights. The analyses include:
- **Shot Analysis:** Visualizes shot outcomes, expected goals (xG) heatmaps, shot success rates by field zone, and shot technique comparisons.
- **Passing Network & Defensive Analysis:** Builds passing networks to identify key playmakers, analyzes defensive actions (e.g., pressures, interceptions, blocks), and maps pressing intensity.
- **Player Movement and Positioning:** Creates heatmaps of player positions, analyzes movement directions with arrows, and examines under-pressure actions and team interaction patterns.

Each module overlays its visualizations on a realistically drawn soccer field, enhancing the interpretability and aesthetic quality of the outputs.

---

## Data Source
https://www.kaggle.com/datasets/ekrembayar/statsbomb-football-event-data
The event data is sourced from StatsBomb JSON files. These files contain detailed event-level information from football matches (e.g., match ID "7530"). The data includes information on player actions, locations on the pitch, event types (e.g., Shot, Pass, Pressure), and additional metadata (e.g., shot outcome, expected goals).

---

## Project Structure

The project is organized into several key modules:

### Shots Analysis

- **Field Drawing:**  
  The `draw_soccer_field(ax)` function uses Matplotlib patches to draw a soccer field with proper dimensions, including penalty areas, goal areas, and the center circle.  
- **Shot Extraction & Heatmap:**  
  Functions such as `get_player_events()`, `get_location_data()`, and `plot_basic_heatmap()` extract shot locations for a given player and generate a heatmap (with Gaussian smoothing) to show shooting intensity.
- **Advanced Shot Analysis:**  
  Additional functions (e.g., `plot_movement_analysis()`, `plot_pressure_analysis()`, and `plot_team_interaction()`) overlay movement arrows, pressure points, and passing trajectories to analyze shot outcomes and team interactions.
- **Composite Visualization:**  
  The `plot_advanced_analysis()` function composes multiple subplots into a grid layout to provide a detailed analysis of an individual player's actions.

### Passing Network and Defensive Analysis

- **Passing Network:**  
  (See previous modules for passing network analysis.) The project includes functions to filter pass events and build a directed graph of player interactions using NetworkX.
- **Defensive Analysis:**  
  The module `analyze_defensive_actions()` extracts defensive events (e.g., Pressure, Interception, Block) for a team, aggregates them by player, and computes summary statistics.  
  - The `visualize_pressure_map()` function creates a heatmap of pressing locations.
  - The `analyze_team_pressing()` function evaluates pressing triggers (such as presses after losing possession or near the sidelines).

### Player Movement and Positioning Analysis

- **Movement & Heatmap Generation:**  
  Functions like `get_player_events()` and `get_location_data()` retrieve location data for a specified player.  
  - `plot_basic_heatmap()` visualizes the density of player actions as a heatmap.
- **Trajectory Analysis:**  
  `plot_movement_analysis()` draws arrows between sequential locations to indicate movement direction and speed.
- **Pressure & Interaction:**  
  `plot_pressure_analysis()` identifies events where the player was under pressure, while `plot_team_interaction()` displays pass trajectories between the player and teammates.
- **Composite Player Analysis:**  
  The `analyze_player()` function retrieves basic player information (team and position) and combines all the visualizations into a comprehensive analysis figure.

---
    *Required libraries include:*  
    - pandas  
    - numpy  
    - matplotlib  
    - seaborn  
    - scipy  
    - networkx

---

## Usage

- **Data Preparation:**  
  Place your StatsBomb JSON event files in the designated data folder (e.g., `/kaggle/input/`).

- **Running Analyses:**  
  The project scripts are modular. For example, to analyze a specific player's movement and positioning, update the `player_name` variable in the analysis script and run:

    ```bash
    python your_analysis_script.py
    ```

  The script will load the match event data (e.g., from `7530.json`), generate visualizations for player heatmaps, movement directions, pressure actions, and team interactions, and display the resulting figures.

- **Customizing Analyses:**  
  You can modify parameters such as bin sizes for heatmaps, color schemes, and grid layout settings directly within the functions.

---

## Contributing

Contributions, suggestions, and improvements are welcome! Please fork the repository and submit a pull request with your changes. For major changes, please open an issue first to discuss what you would like to modify.

---

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.

---

## Contact

For any questions or feedback, please contact:


