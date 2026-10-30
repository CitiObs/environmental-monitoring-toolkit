---
icon: pen-to-square
---

# Why is contextual information critical in wearable sensing?

## Description

When a fixed reference station reports PM2.5 at 25 µg/m³, the context is controlled: location, height, orientation, nearby sources and meteorology are all known. The number of variables is limited and well characterised.

A wearable sensor operates in a context that changes continuously. The same device might record data in a bedroom, kitchen, car, street, shop and office within a single hour. Without knowing which reading corresponds to which environment and activity, the raw data stream is uninterpretable. A PM10 reading of 50 µg/m³ could mean walking along a busy road or opening a bag of flour. Both are legitimate measurements, but they belong to entirely different analytical streams.

## Why is this relevant?

Context transforms raw sensor data into actionable information. Without it, cooking data cannot be separated from walking data, wearable data cannot feed mapping models because personal emissions contaminate the ambient signal, and contradictions arise between personal readings and official maps that erode trust if unexplained.

Conversely, when context is documented, even low-cost sensors reveal insights high-end instruments cannot: pollutant behaviour at different floor levels, ventilation impact in cars, comparative exposure between commuting modes, PM dynamics during different cooking techniques. Contextualised observations also enable before/after comparisons that make exposure concrete and actionable.

## How can this be done?

Effective context documentation addresses three layers:

#### Automatic context

Captured by the device or platform:

* GPS coordinates and timestamps, from the smartphone
* Indoor/outdoor detection, using GPS signal strength, accelerometer and luminosity
* Speed and transport mode, using accelerometer data
* Meteorological conditions, retrieved online based on location

#### Semi-automatic context

Prompted by the system:

* Activity tagging via the companion app, using a predefined list such as cooking, commuting, cleaning and exercising
* Alarm-triggered documentation: when a threshold is exceeded, the user photographs or describes the situation

#### Manual context

Recorded by the participant:

* Logbook entries for specific events, such as drilling, cleaning products or unusual traffic
* Photographs when unusual readings occur
* Notes on ventilation, including windows open or closed and AC on or off

{% hint style="info" %}
The design principle: minimise manual burden, maximise contextual richness. Every additional tap risks reducing compliance. Automate what can be automated, prompt for what is critical, and accept that some context will be missing. Partial context is vastly more valuable than none.
{% endhint %}

### Useful resources

[Community Exposure Science Collaborative — Personal Exposure Toolkit Recorder](https://www.citizen.exposurescience.org/pet/petrecorder). Shows how activity and location tags accompany sensor readings and GPS records, providing a practical example of contextual annotation.

[UrbanBetter — Citizen Science Insights on Air Quality from Three Cities in Africa](https://urbanbetter.science/archive/wp-content/uploads/2023/03/Citizen-science-insights-on-air-quality.pdf). A campaign example combining measurements taken during runs with geolocated observations of the surrounding environment.

### You might also be interested in…

* [Why is it important to document context and how does it help better understand collected data?](https://monitoring.toolkit.citiobs.eu/managing-data/why-is-it-important-to-document-context-and-how-does-it-help-better-understand-collected-data)
* [How do we increase traceability in data collected by citizens?](https://monitoring.toolkit.citiobs.eu/managing-data/how-do-we-increase-traceability-in-data-collected-by-citizens)
* [What are the main aspects you need to consider when managing citizen collected data?](https://monitoring.toolkit.citiobs.eu/managing-data/what-are-the-main-aspects-you-need-to-consider-when-managing-citizen-collected-data)
