# 🌤️ NED Energy Weather in Home Assistant

Geïnspireerd op de **verwachte zon- en windenergieproductie** van [NED.nl](https://ned.nl).  
Deze Home Assistant-integratie toont per dag de verwachte zon en windopwekking in Nederland  rechtstreeks in je eigen dashboard.

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

```yaml
type: custom:apexcharts-card
grid_options:
  columns: full
experimental:
  disable_config_validation: true
header:
  show: true
  title: NED Energy Weather (7 dagen)
now:
  show: false
graph_span: 7d
all_series_config:
  float_precision: 0
  show:
    legend_value: false
apex_config:
  chart:
    type: bar
    toolbar:
      show: false
    height: 350
  tooltip:
    enabled: false
  plotOptions:
    bar:
      horizontal: false
      columnWidth: 70%
      borderRadius: 10
  legend:
    show: true
    position: bottom
    horizontalAlign: right
  xaxis:
    type: category
  yaxis:
    max: 100
    min: 0
    labels:
      show: false
  stroke:
    width: 0
series:
  - name: Wind
    type: column
    show:
      legend_value: false
    color: rgb(80, 150, 255)
    entity: sensor.ned_windheight_day_1
    data_generator: |
      const S = (e) => Number(hass.states[e]?.state);
      const L = (e) => hass.states[e]?.state || 'N/A';

      return [
        {
          x: L('sensor.ned_day_1_label'),
          y: S('sensor.ned_windheight_day_1'),
          goals: [{
            name: 'Wind avg',
            value: S('sensor.ned_windaverage_day_1'),
            strokeWidth: 6,
            strokeHeight: 0,
            strokeColor: '#333333'
          }]
        },
        {
          x: L('sensor.ned_day_2_label'),
          y: S('sensor.ned_windheight_day_2'),
          goals: [{
            name: 'Wind avg',
            value: S('sensor.ned_windaverage_day_2'),
            strokeWidth: 6,
            strokeHeight: 0,
            strokeColor: '#333333'
          }]
        },
        {
          x: L('sensor.ned_day_3_label'),
          y: S('sensor.ned_windheight_day_3'),
          goals: [{
            name: 'Wind avg',
            value: S('sensor.ned_windaverage_day_3'),
            strokeWidth: 6,
            strokeHeight: 0,
            strokeColor: '#333333'
          }]
        },
        {
          x: L('sensor.ned_day_4_label'),
          y: S('sensor.ned_windheight_day_4'),
          goals: [{
            name: 'Wind avg',
            value: S('sensor.ned_windaverage_day_4'),
            strokeWidth: 6,
            strokeHeight: 0,
            strokeColor: '#333333'
          }]
        },
        {
          x: L('sensor.ned_day_5_label'),
          y: S('sensor.ned_windheight_day_5'),
          goals: [{
            name: 'Wind avg',
            value: S('sensor.ned_windaverage_day_5'),
            strokeWidth: 6,
            strokeHeight: 0,
            strokeColor: '#333333'
          }]
        },
        {
          x: L('sensor.ned_day_6_label'),
          y: S('sensor.ned_windheight_day_6'),
          goals: [{
            name: 'Wind avg',
            value: S('sensor.ned_windaverage_day_6'),
            strokeWidth: 6,
            strokeHeight: 0,
            strokeColor: '#333333'
          }]
        },
        {
          x: L('sensor.ned_day_7_label'),
          y: S('sensor.ned_windheight_day_7'),
          goals: [{
            name: 'Wind avg',
            value: S('sensor.ned_windaverage_day_7'),
            strokeWidth: 6,
            strokeHeight: 0,
            strokeColor: '#333333'
          }]
        },
      ];
  - name: Zon
    type: column
    color: rgb(255, 215, 0)
    show:
      legend_value: false
    entity: sensor.ned_sunheight_day_1
    data_generator: |
      const S = (e) => Number(hass.states[e]?.state);
      const L = (e) => hass.states[e]?.state || 'N/A';

      return [
        {
          x: L('sensor.ned_day_1_label'),
          y: S('sensor.ned_sunheight_day_1'),
          goals: [{
            name: 'Zon avg',
            value: S('sensor.ned_sunaverage_day_1'),
            strokeWidth: 6,
            strokeHeight: 0,
            strokeColor: '#333333'
          }]
        },
        {
          x: L('sensor.ned_day_2_label'),
          y: S('sensor.ned_sunheight_day_2'),
          goals: [{
            name: 'Zon avg',
            value: S('sensor.ned_sunaverage_day_2'),
            strokeWidth: 6,
            strokeHeight: 0,
            strokeColor: '#333333'
          }]
        },
        {
          x: L('sensor.ned_day_3_label'),
          y: S('sensor.ned_sunheight_day_3'),
          goals: [{
            name: 'Zon avg',
            value: S('sensor.ned_sunaverage_day_3'),
            strokeWidth: 6,
            strokeHeight: 0,
            strokeColor: '#333333'
          }]
        },
        {
          x: L('sensor.ned_day_4_label'),
          y: S('sensor.ned_sunheight_day_4'),
          goals: [{
            name: 'Zon avg',
            value: S('sensor.ned_sunaverage_day_4'),
            strokeWidth: 6,
            strokeHeight: 0,
            strokeColor: '#333333'
          }]
        },
        {
          x: L('sensor.ned_day_5_label'),
          y: S('sensor.ned_sunheight_day_5'),
          goals: [{
            name: 'Zon avg',
            value: S('sensor.ned_sunaverage_day_5'),
            strokeWidth: 6,
            strokeHeight: 0,
            strokeColor: '#333333'
          }]
        },
        {
          x: L('sensor.ned_day_6_label'),
          y: S('sensor.ned_sunheight_day_6'),
          goals: [{
            name: 'Zon avg',
            value: S('sensor.ned_sunaverage_day_6'),
            strokeWidth: 6,
            strokeHeight: 0,
            strokeColor: '#333333'
          }]
        },
        {
          x: L('sensor.ned_day_7_label'),
          y: S('sensor.ned_sunheight_day_7'),
          goals: [{
            name: 'Zon avg',
            value: S('sensor.ned_sunaverage_day_7'),
            strokeWidth: 6,
            strokeHeight: 0,
            strokeColor: '#333333'
          }]
        },
      ];

```
