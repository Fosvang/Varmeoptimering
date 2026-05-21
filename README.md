# Varmeoptimering

Home Assistant-projekt til overvagning og optimering af varmeforbrug, temperaturer, drift, alarmer og okonomi for varmeanlaeg.

Projektet samler dashboardfiler, brugerguide og screenshots for en varmeoptimeringslosning baseret pa Home Assistant og Shelly-sensorer. Losningen kan bruges pa mobil, tablet og computer via Home Assistant.

## Formal

Varmeoptimering giver et hurtigt overblik over:

- Aktuel driftstatus for varmeanlaeg
- Fremlob, returlob, udetemperatur og Delta T
- Energiforbrug og omkostninger
- Aktive fejl, advarsler og alarmer
- Historik, drift score og centrale nogletal
- Anbefalinger til bedre varmeokonomi

Målet er at reducere energiforbrug uden at ga pa kompromis med komfort eller driftssikkerhed.

## Funktioner

- Dashboard med driftstatus, temperaturhistorik og alarmoversigt
- Konfiguration af sensor-entity IDs fra Home Assistant
- Temperaturgraenser for fremlob, returlob, Delta T og frostsikring
- Alarmhaandtering med kvittering, pause og reset
- Notifikationer via Home Assistant services og mulighed for SMS
- Statistik for 1 time, 24 timer og 7 dage
- Okonomioversigt med elpris, forbrug, brændsel og SCOP
- Lager- og genopfyldningsberegninger for brændsel

## Projektstruktur

```text
Varmeoptimering/
├── docs/
│   └── User Guide Heatoptimisation.docx
├── home-assistant/
│   ├── varmeoptimering_dashboard.yaml
│   └── varmeoptimering_dashboard_V0.yaml
├── images/
│   ├── Shelly project energyoptimisation.JPG
│   ├── Shelly project energyoptimisation_devices.JPG
│   ├── Shelly project energyoptimisation_economy.JPG
│   └── Shelly project energyoptimisation_scorecard.JPG
└── README.md
```

## Installation i Home Assistant

1. Kopier YAML-filerne fra `home-assistant/` til din Home Assistant-konfiguration.
2. Tilpas entity IDs i dashboardet, sa de matcher dine egne sensorer og enheder.
3. Kontroller at temperatur-, effekt- og status-sensorer leverer data.
4. Juster graensevaerdier for dit varmeanlaeg.
5. Aktiver notifikationer og SMS, hvis det skal bruges.

Typiske entity IDs kan vaere:

- `sensor.shelly_supply_temperature`
- `sensor.shelly_return_temperature`
- `sensor.outdoor_temperature`
- `sensor.heatpump_power`
- `binary_sensor.heat_source_running`

## Screenshots

![Driftstatus](images/Shelly%20project%20energyoptimisation.JPG)

![Enheder og opsaetning](images/Shelly%20project%20energyoptimisation_devices.JPG)

![Okonomi](images/Shelly%20project%20energyoptimisation_economy.JPG)

![Statistik og nogletal](images/Shelly%20project%20energyoptimisation_scorecard.JPG)

## Dokumentation

Den fulde brugerguide findes i [docs/User Guide Heatoptimisation.docx](docs/User%20Guide%20Heatoptimisation.docx).

## Vedligeholdelse

Det anbefales regelmaessigt at kontrollere sensorer, temperaturer, alarmer, netvaerk og Home Assistant-logfiler. Ved fejl bor entity IDs, sensorstatus og de seneste aendringer i opsaetningen gennemgas.
