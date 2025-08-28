# Football Data

EA FC 25 Data for Pandas workshop

This dataset contains football-related entities (players, teams, leagues) along with linking tables and external enrichment data.
The tables are split into three categories: **data**, **links**, and **additional**.

---

## Data Tables

### `players.csv`

Stores all in-game player attributes, ratings, and metadata.
**Key columns:**

* `playerid` (primary key, internal player ID)
* `firstnameid`, `lastnameid` (text IDs for names, linkable to localization)
* `overallrating` (integer, 1-99)
* `potential` (integer, 1-99)
* Attribute ratings: `freekickaccuracy`, `composure`, `strength`, etc.
* `preferredposition1`, `preferredposition2`, … (positions like ST, CM, CB)
* `nationality` (integer code for country)
* `birthdate`, `height`, `weight`

---

### `teams.csv`

Stores team/club metadata and performance values.
**Key columns:**

* `teamid` (primary key, internal team ID)
* `teamname` (club name)
* `overallrating`, `attackrating`, `midfieldrating`, `defenserating`
* `rivalteam` (foreign key to another `teamid`)
---

### `leagues.csv`

Stores metadata about competitions and leagues.
**Key columns:**

* `leagueid` (primary key, internal league ID)
* `leaguename`
* `countryid` (country code ID)
---

### `countries.csv`

Stores metadata about competitions and leagues.
**Key columns:**

* `countryid` (primary key, internal country ID)
* `countryname`
---

## Relationships

### `teamplayerlinks.csv`

Links **players ↔ teams**, with per-player team stats.
**Key columns:**

* `playerid` (FK → players.csv)
* `teamid` (FK → teams.csv)
* `jerseynumber`
* `position`

---

### `leagueteamlinks.csv`

Links **teams ↔ leagues**, with standings and form.
**Key columns:**

* `teamid` (FK → teams.csv)
* `leagueid` (FK → leagues.csv)
---

## Helper Tables

### `models.csv`

Simple mapping of internal IDs to text.
**Key columns:**

* `playerid` (FK → players.csv)
* `playername` (string)

---

### `sofifa.csv`

External SoFIFA player dataset, providing real-world data for enrichment.
**Key columns:**

* `player_id`
* `name`, `full_name`
* Ratings: `overall_rating`, `potential`
* Value/wage: `value`, `wage`

---
