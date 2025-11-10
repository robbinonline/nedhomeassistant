# 🌤️ NED Energy Dashboard for Home Assistant

Een visueel dashboard voor Home Assistant geïnspireerd op de **verwachte zon- en windenergieproductie** van [ned.nl](https://ned.nl).  
Het project toont de dagelijkse zon- en windopbrengst in Nederland op een aantrekkelijke manier, vergelijkbaar met de officiële NED-weergave — maar dan volledig geïntegreerd in je eigen Home Assistant omgeving.

---

## 🔍 Inspiratie

Op de website van NED is te zien hoeveel duurzame elektriciteit (zon & wind) er in de komende week wordt verwacht.  
Die stijl wilde ik graag ook in Home Assistant kunnen weergeven — met herkenbare blauwe en gele kolommen, en een stippellijn die het gemiddelde van de dag toont.

➡️ Zo ontstond dit kleine project: een combinatie van REST-sensors, template-sensors en een [ApexCharts-card](https://github.com/RomRider/apexcharts-card).

---

## 🧩 Bestanden

| Bestand | Omschrijving |
|----------|---------------|
| `rest.yaml` | REST-sensordefinities die de JSON-data van NED ophalen |
| `template.yaml` | Template-sensors die o.a. de daglabels (MA, DI, WO…) genereren |
| `ui-lovelace.yaml` | (optioneel) voorbeeldweergave voor ApexCharts |
| `ned.png` | Originele NED-weergave ter inspiratie |
| `inhomeassistant.png` | Resultaat in Home Assistant |

---

## 🖼️ Voorbeeld

### Originele weergave op ned.nl
![NED voorbeeld](ned.png)

### Dezelfde data in Home Assistant
![Home Assistant versie](inhomeassistant.png)

---

## ⚙️ Installatie

1. **Download of kopieer** de bestanden  
   - Plaats `rest.yaml` en `template.yaml` in je `config`-map (bijv. `config/integrations/` of direct in `packages/`).
2. Voeg in `configuration.yaml` toe:
   ```yaml
   homeassistant:
     packages: !include_dir_named integrations
