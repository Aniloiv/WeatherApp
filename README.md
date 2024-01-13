## **API key**
```
133dc8f6fa5ec54b5f3ed0226afd7d2c
```
## **Base URL**
```
https://api.openweathermap.org/data/2.5/weather
```
## **Fetch query & response**
```
Query -> ${BASE_URL}?q=${city.value}&appid=${WEBHOOK}
```
```
Response
{
    "coord": {
        "lon": 2.3488,
        "lat": 48.8534
    },
    "weather": [
        {
            "id": 701,
            "main": "Mist",
            "description": "mist",
            "icon": "50n"
        }
    ],
    "base": "stations",
    "main": {
        "temp": 271.62,
        "feels_like": 269.58,
        "temp_min": 270.58,
        "temp_max": 272.49,
        "pressure": 1022,
        "humidity": 91
    },
    "visibility": 5000,
    "wind": {
        "speed": 1.54,
        "deg": 0
    },
    "clouds": {
        "all": 100
    },
    "dt": 1705174280,
    "sys": {
        "type": 2,
        "id": 2041230,
        "country": "FR",
        "sunrise": 1705131623,
        "sunset": 1705162635
    },
    "timezone": 3600,
    "id": 2988507,
    "name": "Paris",
    "cod": 200
}
```