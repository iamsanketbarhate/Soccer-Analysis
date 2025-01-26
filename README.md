# Soccer Analytics Project

## Project Overview
This data analysis project focuses on extracting meaningful insights from soccer database using advanced SQL techniques. The project demonstrates proficiency in data manipulation, aggregation, and deriving actionable business intelligence.

## Key Skills Demonstrated
- Complex SQL querying across multiple database tables
- Advanced data aggregation and filtering
- Performance indicator extraction
- Comprehensive data analysis techniques

## Technical Achievements
- Connected and analyzed data across multiple relational database tables
- Extracted key performance indicators using aggregate functions
- Applied advanced filtering, sorting, and ranking techniques
- Performed in-depth data exploration and statistical analysis

## Sample SQL Queries and Insights

### 1. Goal Scoring Analysis
```sql
SELECT 
    pm.player_name, 
    COUNT(gd.goal_id) as total_goals
FROM player_mast pm
JOIN goal_details gd ON pm.player_id = gd.player_id
GROUP BY pm.player_id, pm.player_name
ORDER BY total_goals DESC
LIMIT 5;
```
**Insight**: Identifies top-performing players based on goal-scoring performance, crucial for player evaluation and team strategy.

### 2. Team Performance Metrics
```sql
SELECT 
    sc.country_name, 
    st.match_played,
    st.won,
    st.draw,
    st.lost,
    st.points
FROM soccer_team st
JOIN soccer_country sc ON st.country_id = sc.country_id
ORDER BY st.points DESC;
```
**Insight**: Provides comprehensive team performance overview, including matches played, wins, draws, losses, and total points.

### 3. Venue Capacity Analysis
```sql
SELECT 
    sv.venue_name, 
    sc.city, 
    sc.country_name, 
    sv.aud_capacity
FROM soccer_venue sv
JOIN soccer_city sc ON sv.city_id = sc.city_id
ORDER BY sv.aud_capacity DESC
LIMIT 5;
```
**Insight**: Evaluates venue capacities to understand potential audience and event scaling opportunities.

### 4. Referee Performance
```sql
SELECT 
    rm.referee_name, 
    sc.country_name, 
    COUNT(mm.match_no) as matches_officiated
FROM referee_mast rm
JOIN match_mast mm ON rm.referee_id = mm.referee_id
JOIN soccer_country sc ON rm.country_id = sc.country_id
GROUP BY rm.referee_id, rm.referee_name, sc.country_name
ORDER BY matches_officiated DESC
LIMIT 3;
```
**Insight**: Tracks referee workload and distribution across matches.

### 5. Card Distribution Analysis
```sql
SELECT 
    COUNT(CASE WHEN sent_off = 'N' THEN 1 END) as yellow_cards,
    COUNT(CASE WHEN sent_off = 'Y' THEN 1 END) as red_cards
FROM player_booked;
```
**Insight**: Provides disciplinary statistics to understand player behavior and match intensity.

## Tools and Technologies
- SQL
- Database Management
- Data Analysis
- Performance Metrics Extraction

## Challenges Overcome
- Navigating complex relational database schemas
- Implementing advanced SQL joins and aggregations
- Extracting meaningful business insights from raw data
