# Weather Forecast Application

## Description
This is an Android application that uses the OpenWeatherMap API to retrieve weather forecasts. The user can enter a city and country, and the app will display detailed weather information, including temperature, pressure, humidity, wind speed, and more. Additionally, the user can view forecasts for upcoming days along with images representing weather conditions.

## Features
- **Current weather forecast:** Displays real-time weather data including temperature, humidity, wind speed, pressure, etc.
- **Weather icons:** Displays images corresponding to different weather conditions (e.g., sunny, rainy, cloudy).
- **Next day forecast:** Displays forecast for the next few days with detailed information such as temperature and weather description.
- **Responsive design:** Adjusts the layout based on device orientation (portrait or landscape).

## Requirements

- Android Studio with SDK version 28 or higher
- JDK 8 or newer
- `org.json` library for JSON data parsing
- Internet connection to fetch weather data

## Installation

1. Clone or download the project to your computer.
2. Open the project in Android Studio.
3. Ensure you have the required dependencies and permissions (e.g., network access).
4. Run the application on a physical device or emulator.

## How to Use

1. **Start the app**: Open the app, and you'll be prompted to enter the name of the city and country.
2. **Enter city and country**: Provide the city and country, then press the "Get Weather" button.
3. **View the weather**: Once the data is fetched from the API, the app will display current weather details.
4. **Forecast for tomorrow and next days**: You can view the forecast for the upcoming days by navigating through the app.


## API Integration

The app uses the OpenWeatherMap API to fetch weather data. The API URL format is as follows:
 `https://api.openweathermap.org/data/2.5/weather?q={city},{country}&appid={API_KEY}&units=metric`

 
- Replace `{city}` with the city name.
- Replace `{country}` with the country code.
- Replace `{API_KEY}` with your API key from OpenWeatherMap.

## Code Structure

- **MainActivity**: Displays the main weather information, including temperature, humidity, wind speed, and more.
- **FormActivity**: Allows the user to input the city and country.
- **MainPhoto**: Handles displaying weather icons based on the weather description.
- **WeatherTableBack**: Displays the weather data in a table format for the next days.
- **WeatherTime**: Shows hourly weather data, including temperature and weather description for each time slot.
- **WeatherTommorow**: Displays tomorrow's forecast, including weather conditions, temperature, wind, humidity, and rain data.

## Example Code Snippets

### Fetching Weather Data
```java
class ApiTask extends AsyncTask<Void, Void, Void> {
    @Override
    protected Void doInBackground(Void... voids) {
        Api.api();
        return null;
    }
    
    @Override
    protected void onPostExecute(Void aVoid) {
        displayData();
    }
}
```

### Displaying Weather Data

```java
void displayData() {
    if (Api.responseCode != 200) {
        Toast.makeText(this, "Wrong data!", Toast.LENGTH_SHORT).show();
        Intent intent = new Intent(this, FormActivity.class);
        startActivity(intent);
    } else {
        progressBar.setVisibility(View.GONE);
        napis1.setVisibility(View.VISIBLE);
        tablica.setVisibility(View.VISIBLE);
        divider.setVisibility(View.VISIBLE);
        MainPhoto mainPhoto = new MainPhoto(this, Api.tab1[0][0]);
        mainPhoto.wyswietl(Api.tab1[2][0], Api.tab1[5][0], Api.tab1[4][0], Api.tab1[8][0], Api.tab1[7][0], Api.tab1[6][0], val, seaGrndLevel);
        mainPhoto.wywolaj(image);
    }
}
```

## Design

![weather](https://github.com/user-attachments/assets/b8adcbcd-3ea4-4e50-9f8a-226cd74d3149)


## License 

This project is licensed under the MIT License - see the LICENSE file for details.
