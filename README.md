# FPL-Stats24 ⚽📊  
**Fantasy Premier League Player Stats Finder — Spring Boot & PostgreSQL Backend API**  
Data webscraped from [fberf.com](https://fberf.com) for the 2024/25 season

---

## Overview  
FPL-Stats24 provides a RESTful API to retrieve detailed player statistics for the 2024/25 Fantasy Premier League season.  
All player data is scraped from fferf.com and stored in a PostgreSQL database, accessible via a Spring Boot backend.

---

## Features  
- Fetch comprehensive player stats including goals, assists, expected goals, cards, minutes played, and more  
- Search players by name, team, or position  
- Filter players by team or position  
- Fast, JSON-based REST API built for integration with fantasy apps or data analysis  

---

## Tech Stack  
- Spring Boot (Java)  
- PostgreSQL  
- JSoup for web scraping  
- Maven  

---

## Setup & Installation  

### 1. Clone the repo  
```bash
git clone https://github.com/yourusername/fpl-stats24.git
cd fpl-stats24

### 2. Configure PostgreSQL

Create a database named `fpl_stats24` and update `src/main/resources/application.properties` with your DB credentials.

---

### 3. Run the app

```bash
mvn spring-boot:run
The API will be available at: http://localhost:8080

### API Endpoints

| Method | Endpoint                         | Description                      |
|--------|---------------------------------|--------------------------------|
| GET    | `/api/v1/players`               | List all players                |
| GET    | `/api/v1/player?name={name}`   | Search player by name           |
| GET    | `/api/v1/players/team/{team}`  | Filter players by team          |
| GET    | `/api/v1/players/position/{pos}` | Filter players by position    |

---

### Player Stats Model

Each player object returned contains the following fields:

| Field                    | Description                        |
|--------------------------|----------------------------------|
| `playerName`             | Player's full name                |
| `nation`                 | Player's nationality              |
| `position`               | Playing position (e.g., Forward) |
| `age`                    | Player's age                     |
| `matches_played`         | Number of matches played          |
| `matches_started`        | Number of matches started         |
| `minutes_played`         | Total minutes played              |
| `yellow_cards`           | Number of yellow cards            |
| `red_cards`              | Number of red cards               |
| `goals`                  | Goals scored                     |
| `assists`                | Assists made                     |
| `goals_assists`          | Sum of goals and assists          |
| `expected_goals`         | Expected goals (xG)              |
| `expected_assists`       | Expected assists (xA)            |
| `expected_g_and_a`       | Expected goals + assists         |
| `goals_per_game`         | Goals per game                   |
| `assists_per_game`       | Assists per game                 |
| `g_and_a_per_game`       | Goals + assists per game         |
| `expected_goals_per_game`| Expected goals per game          |
| `expected_assists_per_game` | Expected assists per game      |
| `team_name`              | Current team name                |
| `league_last_season`     | League name from previous season |

---

### Example API Response

#### Request

```bash
GET /api/v1/player?name=Mohamed%20Salah

{
  "playerName": "Mohamed Salah",
  "nation": "Egypt",
  "position": "Forward",
  "age": 31,
  "matches_played": 38,
  "matches_started": 38,
  "minutes_played": 3420,
  "yellow_cards": 2,
  "red_cards": 0,
  "goals": 23,
  "assists": 10,
  "goals_assists": 33,
  "expected_goals": 20.5,
  "expected_assists": 8.7,
  "expected_g_and_a": 29.2,
  "goals_per_game": 0.6,
  "assists_per_game": 0.26,
  "g_and_a_per_game": 0.86,
  "expected_goals_per_game": 0.54,
  "expected_assists_per_game": 0.23,
  "team_name": "Liverpool",
  "league_last_season": "Premier League"
}
