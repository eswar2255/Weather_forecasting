
# Real-Time Weather Monitoring and Data Processing System

## Project Overview
This project is a **Real-Time Weather Monitoring and Data Processing System** designed to retrieve, process, and analyze weather data from multiple cities in India. Using data from the OpenWeatherMap API, this system performs live monitoring of weather parameters, computes daily rollup summaries, and triggers alerts based on user-defined thresholds. The results can be visualized, enabling users to understand trends and monitor critical weather events effectively.

## Objectives
The system's key objectives are to:
1. Collect real-time weather data for major Indian metros (Delhi, Mumbai, Chennai, Bangalore, Kolkata, Hyderabad).
2. Store and process this data for real-time and historical analysis.
3. Provide daily rollups and aggregates for key weather indicators.
4. Alert users when specified weather conditions (e.g., high temperature, specific weather conditions) are met.
5. Display insights through visualizations for better understanding and decision-making.

## Features
- **Real-Time Data Collection**: Fetches weather data every 30 seconds for predefined cities using the OpenWeatherMap API.
- **Data Storage**: Utilizes an SQLite database to store both real-time data and computed aggregates.
- **Daily Rollups and Aggregates**: Computes daily summaries, including:
    - Average, maximum, and minimum temperature.
    - Dominant weather condition.
- **Alerting System**: Triggers alerts based on user-configurable thresholds (e.g., high temperature or specific weather conditions).
- **Data Visualization**: Visualizes daily average temperatures, maximum and minimum temperatures, and alerts using charts.

## Project Structure
The code is organized into several key functions, each responsible for a specific aspect of data processing, storage, or alerting. The primary components are:

1. **Database Setup**: Initializes an SQLite database and creates tables for storing real-time and aggregated data.
2. **Data Collection**: Retrieves data from the OpenWeatherMap API, processes it, and stores it in the `weather_data` table.
3. **Rollups and Aggregates**: Processes data to create daily summaries and store them in the `daily_weather_summary` table.
4. **Alerting System**: Monitors for consecutive temperature breaches or specific weather conditions and triggers alerts.
5. **Visualization**: Plots historical and daily weather data using line charts.

## Detailed Workflow

### 1. Setup and Configuration
The project uses Python with the following primary libraries:
- **SQLite**: For data storage.
- **Requests**: To fetch data from the OpenWeatherMap API.
- **Matplotlib and Seaborn**: For data visualization.

The project is configured to run on an API key provided by OpenWeatherMap, and the SQLite database is initialized with two tables:
- `weather_data`: Stores real-time data with fields for city, temperature, weather condition, and timestamp.
- `daily_weather_summary`: Stores daily aggregated data.

### 2. Data Collection Process
The `monitor_weather()` function initiates the real-time data collection process, where:
- Weather data for each city is fetched every 30 seconds.
- Key parameters such as temperature and weather conditions are parsed and stored in the `weather_data` table.
- The system converts temperature data from Kelvin to Celsius.

### 3. Rollups and Aggregates
Every cycle, the system computes daily rollups to summarize data for each city, calculating:
- **Average Temperature**: Mean of all recorded temperatures.
- **Maximum and Minimum Temperature**: Peak values throughout the day.
- **Dominant Weather Condition**: Most frequently observed condition (e.g., Clear, Rain).
  
These daily summaries are stored in the `daily_weather_summary` table.

### 4. Alerting System
Alerts are generated based on:
- **Temperature Threshold**: If the temperature exceeds a user-defined limit (e.g., 35°C) for two consecutive readings, an alert is raised.
- **Specific Weather Condition**: Alerts can also trigger if a particular weather condition (e.g., Rain) is detected.

This alerting functionality is particularly useful for users needing to respond quickly to changing weather conditions.

### 5. Visualization
The `visualize_weather_summary()` function generates line plots showing:
- **Daily Average Temperature Trends**: Tracks temperature trends over time.
- **Alerts**: Highlights instances where temperature or specific weather conditions have triggered alerts.

This visualization provides a quick overview of the collected data and enhances understanding of weather patterns across cities.

## Usage Instructions

### Prerequisites
1. **Python 3.x** with libraries: `requests`, `sqlite3`, `matplotlib`, and `seaborn`.
2. An API key from [OpenWeatherMap](https://home.openweathermap.org/users/sign_up).

### Setup
1. Clone the repository or download the project files.
2. Install required libraries:
    ```bash
    pip install requests matplotlib seaborn
    ```
3. Update the `monitor_weather()` function with your OpenWeatherMap API key.

### Run the Project
To start the real-time monitoring and data processing system, run:
```python
python weather_monitoring.py
```
Follow on-screen prompts to specify the number of monitoring iterations.

### Visualize Data
After running the monitoring system, you can visualize data by calling:
```python
visualize_weather_summary()
```

## Future Enhancements
1. **Expanded Weather Parameters**: Add support for additional parameters like pressure and visibility.
2. **Extended Forecasting**: Integrate weather forecasts and generate summaries based on predicted conditions.
3. **Alert Dashboard**: Develop a user interface to display alerts and data summaries interactively.

## Conclusion
The **Real-Time Weather Monitoring and Data Processing System** is a comprehensive solution for tracking weather patterns across major Indian cities. With capabilities for real-time data collection, daily summaries, and alerting, the system provides valuable insights into weather trends, enabling users to stay informed about critical weather conditions.

