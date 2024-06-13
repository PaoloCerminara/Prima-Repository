import requests
import streamlit as st
st.title("Ilmeteo.it")
API_key ="1ed39ab9cba3293253497cccbe27025b"

city_name =  st.text_input("Inserisci il nome della città:", )

if city_name:
    if st.button("Clicca QUI"):
        url = f"https://api.openweathermap.org/data/2.5/weather?q={city_name}&appid={API_key}"
        result = requests.get(url)
        json = result.json()
        temp = round(json["main"]["temp_min"] -273.15, 1)
        st.write(f"la temperatura è di {temp} °C")
        country = json["sys"]["country"]
        st.write(f"la città è  {country} ")
        pressure = json["main"]["pressure"]
        st.write(f"la pressione è di  {pressure} ")




