# Varmeoptimering

Home Assistant-projekt til overvagning og optimering af varmeforbrug, temperaturer, drift, alarmer og okonomi for varmeanlaeg.

Projektet samler dashboardfiler, Home Assistant packages, notifikationer, brugerguide og screenshots for en varmeoptimeringslosning baseret pa Home Assistant og Shelly-sensorer. Losningen kan bruges pa mobil, tablet og computer via Home Assistant.

## Formal

Varmeoptimering giver et hurtigt overblik over:

- Aktuel driftstatus for varmeanlaeg
- Fremlob, returlob, udetemperatur og Delta T
- Energiforbrug og omkostninger
- Aktive fejl, advarsler og alarmer
- Historik, drift score og centrale nogletal
- Anbefalinger til bedre varmeokonomi

Maalet er at reducere energiforbrug uden at ga pa kompromis med komfort eller driftssikkerhed.

## Funktioner

- Dashboard med driftstatus, temperaturhistorik og alarmoversigt
- Konfiguration af sensor-entity IDs fra Home Assistant
- Temperaturgraenser for fremlob, returlob, Delta T og frostsikring
- Alarmhaandtering med kvittering, pause og reset
- Notifikationer via Home Assistant services og mulighed for SMS
- Statistik for 1 time, 24 timer og 7 dage
- Okonomioversigt med elpris fra Stromligning, forbrug, braendsel og SCOP
- Lager- og genopfyldningsberegninger for braendsel

## Projektstruktur

```text
Varmeoptimering/
|-- docs/
|   `-- User Guide Heatoptimisation.docx
|-- home-assistant/
|   |-- AM2305_temp_hum.js
|   |-- configuration.yaml
|   |-- varmeoptimering_dashboard.yaml
|   |-- varmeoptimering_economy_package.yaml
|   |-- varmeoptimering_economy_view.yaml
|   |-- varmeoptimering_notifikationer.yaml
|   `-- varmeoptimering_package.yaml
|-- images/
|   |-- Shelly project energyoptimisation.JPG
|   |-- Shelly project energyoptimisation_devices.JPG
|   |-- Shelly project energyoptimisation_economy.JPG
|   `-- Shelly project energyoptimisation_scorecard.JPG
`-- README.md
```

## Home Assistant-filer

- `home-assistant/configuration.yaml`: reference til Lovelace dashboard, packages og GatewayAPI SMS rest_command.
- `home-assistant/varmeoptimering_dashboard.yaml`: hoveddashboard med overblik, sensorer, alarmer og statistik. Inkluderer okonomiviewet.
- `home-assistant/varmeoptimering_economy_view.yaml`: Lovelace-view for okonomi, elpris, forbrug, braendsel, lager og SCOP.
- `home-assistant/varmeoptimering_package.yaml`: Home Assistant package med helpers, template-sensorer, alarmer, scripts og automations til varmeoptimering.
- `home-assistant/varmeoptimering_economy_package.yaml`: Home Assistant package med okonomi-, energi-, driftstid- og utility meter-sensorer. Aktuel elpris hentes fra Stromligning-projektets `sensor.stromligning_aktuel_elpris`.
- `home-assistant/varmeoptimering_notifikationer.yaml`: automations til notifikationer og alarmhaandtering.
- `home-assistant/AM2305_temp_hum.js`: Shelly-script til AM2305 temperatur/fugt-sensor.

## Installation i Home Assistant

1. Kopier `home-assistant/varmeoptimering_dashboard.yaml` og `home-assistant/varmeoptimering_economy_view.yaml` til din Lovelace dashboard-mappe.
2. Kopier `home-assistant/varmeoptimering_package.yaml` og `home-assistant/varmeoptimering_economy_package.yaml` til din Home Assistant `packages/` mappe.
3. Kopier `home-assistant/varmeoptimering_notifikationer.yaml` til din automations-mappe, hvis notifikationer skal bruges.
4. Brug `home-assistant/configuration.yaml` som reference til Lovelace dashboard-, package- og SMS-opsatning.
5. Brug `home-assistant/AM2305_temp_hum.js` pa Shelly-enheden, hvis du bruger AM2305 temperatur/fugt-sensor.
6. Installer Stromligning-projektet, sa `sensor.stromligning_aktuel_elpris` findes i Home Assistant.
7. Tilpas entity IDs i dashboardet og helper-felterne, sa de matcher dine egne sensorer og enheder.
8. Kontroller at temperatur-, effekt-, pris- og status-sensorer leverer data.
9. Juster graensevaerdier og okonomipriser for dit varmeanlaeg.
10. Aktiver notifikationer og SMS, hvis det skal bruges.

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
