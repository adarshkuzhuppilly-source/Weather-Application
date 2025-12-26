import requests

API_KEY = "YOUR_API_KEY_HERE"
BASE_URL = "https://api.openweathermap.org/data/2.5/weather"

def get_weather(city):
    params = {
        "q": city,
        "appid": API_KEY,
        "units": "metric"
    }
    response = requests.get(BASE_URL, params=params)

  if response.status_code == 200:
        data = response.json()
        temp = data["main"]["temp"]
        condition = data["weather"][0]["description"]

   print(f"\nWeather in {city}")
        print(f"Temperature: {temp}°C")
        print(f"Condition: {condition.capitalize()}")
    else:
        print("City not found or API error.")

if __name__ == "__main__":
    city_name = input("Enter city name: ")
    get_weather(city_name)
