# 🌤️ NED Energy Weather in Home Assistant

Geïnspireerd op de **verwachte zon- en windenergieproductie** van [NED.nl](https://ned.nl).  
Deze Home Assistant-integratie toont per dag de verwachte zonne- en windopwekking in Nederland — rechtstreeks in je eigen dashboard, met dezelfde herkenbare stijl.

---

## 🖼️ Voorbeelden

### Originele weergave op NED.nl
![NED voorbeeld](ned.png)

### Weergave in Home Assistant
![Home Assistant versie](homeassistant.png)

---

## ⚙️ Installatie

1. **Open je Home Assistant-configuratie**  
   Voeg de inhoud van de bestanden **`rest.yaml`** en **`template.yaml`** toe aan je `configuration.yaml`.

2.	**Herlaad de integraties**
	Ga in Home Assistant naar Ontwikkelaarstools → YAML en kies:
	•	“Herlaad REST-entiteiten”
	•	“Herlaad Template-entiteiten”

3.	**Voeg de Lovelace-kaart toe**
	Maak een handmatige kaart in je dashboard en plak onderstaande configuratie.

