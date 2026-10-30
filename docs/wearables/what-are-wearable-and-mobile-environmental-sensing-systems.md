---
icon: sunglasses
---

# What are wearable and mobile environmental sensing systems?

## Description

Wearable and mobile environmental sensing systems are portable devices designed to measure environmental conditions directly within the user’s surroundings during daily activities and mobility. Unlike fixed monitoring stations that remain at static locations, wearable systems move with the user and collect measurements across multiple environments throughout the day.

These systems typically integrate environmental sensors, a battery, positioning technology (GPS or smartphone-relayed), wireless communication (Bluetooth), onboard memory and often a companion smartphone application for visualisation, geolocation, synchronisation and user interaction. Some provide real-time values, charts and maps on the phone; others log data for later download.

Wearable systems may measure particulate matter (PM1, PM2.5, PM10), gase pollutants (NO₂, O₃, CO, CO₂, VOCs), temperature, humidity, noise or light. Some devices update every second, providing the temporal resolution needed to capture rapid exposure transients. Depending on the use case, they may be worn on the body, clipped to a bag or bicycle, placed in a vehicle, or simply carried.

A critical feature for personal exposure use is configurable alarms. When a device triggers an alert, for example PM2.5 above 15 µg/m³ for more than 30 seconds, the user looks around to understand the cause. This feedback loop turns the participant from a passive data carrier into an active investigator of their own environment.

## Why is this relevant?

Wearable systems make it possible to observe environmental conditions in everyday environments rather than only at fixed monitoring locations. They capture variability at spatial and temporal scales that fixed networks cannot reach: inside homes, during a commute, while cooking, in a car park.

Because they are portable and increasingly accessible, they create new opportunities for citizen participation. Participants interact directly with measurements from their own activities, which strengthens engagement and environmental understanding.

At the same time, wearable systems introduce significant technical and operational challenges: device usage, participant engagement, data quality, battery autonomy, motion artefacts and privacy. These are addressed in dedicated entries below.

## How can this be done?

{% stepper %}
{% step %}
### Define the objective first

Personal exposure assessment, educational awareness, commuting analysis, occupational study, or participatory monitoring. The objective determines everything downstream.
{% endstep %}

{% step %}
### Select devices matched to the scenario

For personal exposure, prioritise 1-second temporal resolution, Bluetooth smartphone pairing, activity tagging, and configurable alarms. For vehicle-mounted monitoring, prioritise GPS precision and vibration resistance.
{% endstep %}

{% step %}
### Test wearing positions before deployment

Clip the device to the belt, bag strap or jacket and verify that the air inlet does not touch clothing. False PM readings from textile friction are a documented artefact.
{% endstep %}

{% step %}
### Ensure battery lasts the mission

Aim for 12–16 hours of continuous operation. Consider whether data logging continues during charging.
{% endstep %}

{% step %}
### Evaluate the companion app

Does it tag activities? Provide configurable alarms? Display values, charts and maps? Export data as CSV/JSON? Support both iOS and Android?
{% endstep %}

{% step %}
### Pilot-test in real conditions

Run the full workflow end-to-end, from device to data platform, with a small group before scaling.
{% endstep %}
{% endstepper %}

## Useful resources

[Community Exposure Science Collaborative — Personal Exposure Toolkit Recorder](https://www.citizen.exposurescience.org/pet/petrecorder). A community exposure-science tool combining a portable sensor with a smartphone recorder. Useful as a concrete introduction to personal monitoring.

[HabitatMap — AirBeam Mini User’s Guide](https://www.habitatmap.org/airbeam/users-guide-airbeammini). A device-specific practical guide. Consult the mobile recording sections to understand the sensor–phone workflow and carrying requirements.

### You might also be interested in…

* [What are the main elements of a sensing device?](https://monitoring.toolkit.citiobs.eu/sensing-devices/what-are-the-main-elements-of-a-sensing-device)
* [What variables can be measured with air quality sensing devices?](https://monitoring.toolkit.citiobs.eu/sensing-devices/what-variables-can-be-measured-with-air-quality-sensing-devices)
* [What non-technical aspects to consider when choosing sensing devices?](https://monitoring.toolkit.citiobs.eu/sensing-devices/what-non-technical-aspects-to-consider-when-choosing-sensing-devices)

##
