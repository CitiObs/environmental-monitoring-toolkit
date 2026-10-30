---
icon: universal-access
---

# Wearables

## Category: Personal Exposure and Wearable Environmental Monitoring

### A paradigm shift, not just a smaller sensor

Environmental monitoring has traditionally relied on fixed stations and models designed to characterise environmental conditions over large areas and long periods. These systems remain essential for regulatory monitoring, trend analysis, environmental assessment and policy support. They form the backbone of official monitoring infrastructures and their accuracy, standardisation and long-term continuity are irreplaceable.

However, environmental exposure is experienced at the scale of the individual, not at the scale of a city or an annual average. People move continuously through different environments during the day — homes, schools, offices, vehicles, shops, streets — and their exposure is shaped by activities, ventilation, mobility and proximity to pollution sources. As a result, what fixed monitoring systems measure may differ significantly from what individuals actually breathe.

Wearable and mobile sensing technologies introduce a fundamentally different type of observation. A wearable device does not describe a place; it follows a person. Its data stream flows through bedrooms, kitchens, working space, streets, cars, shops and streets in the course of a single hour. It measures the air the individual actually breathes, including the pollution they generate themselves through cooking, cleaning, driving or working.

This is not air quality mapping with a smaller instrument. It is a different kind of measurement that answers a different question: _what am I breathing, right now, in this specific situation?_

### From institutions to communities to individuals: where wearables fit

Wearable sensing does not stand alone. It is the third step in a progression that has gradually brought environmental monitoring closer to the people it concerns. Understanding this progression is essential to understanding what wearables add — and what they do not replace.

{% stepper %}
{% step %}
### Institutional monitoring (reference stations)

For decades, air quality monitoring was the exclusive domain of public authorities operating a small number of high-grade reference stations. These instruments are accurate, standardised and essential for regulatory compliance and long-term trend analysis. But they are also expensive to install and maintain, which severely limits how many can be deployed.

The result is excellent data at very few points — a sparse network that captures the regional picture but misses the fine-grained spatial variability of pollution within a neighbourhood, a street, or a building.
{% endstep %}

{% step %}
### Community monitoring (low-cost sensors)

Low-cost sensors (LCS) are the technology at the heart of CitiObs and of citizen science more broadly. By dramatically reducing the cost per device, they make something new possible: dense networks operated not by institutions but by communities. This is a fundamental shift — from a few authoritative points to a dense fabric of observations maintained by the people who live in the monitored area.

The advantages of low-cost sensors are precisely what make them the backbone of Citizen Observatories:

* **Dense spatial coverage:** many sensors reveal the spatial gradients of pollution that a sparse reference network cannot — the difference between one side of a street and the other, between a courtyard and a main road.
* **High temporal resolution:** continuous real-time measurement captures the daily and hourly dynamics of air quality, not just regulatory averages.
* **Affordability and accessibility:** low-cost and ease of use mean non-experts can deploy and maintain them, putting monitoring directly in the hands of communities.
* **Engagement and ownership:** when citizens host and operate sensors, they become active participants in understanding their own environment, not passive recipients of official data.
* **Complementarity, not competition:** once calibrated and quality-controlled, LCS data densifies and strengthens official networks rather than replacing them. In CitiObs, the FILTER/ValAir framework handles the necessary quality control and uncertainty estimation, and MapAir fuses LCS observations with models to produce decision-ready maps at resolutions a reference network alone cannot reach.

The trade-off is well understood: individual low-cost sensors are less accurate than reference instruments and require careful calibration, quality control and uncertainty handling. CitiObs exists precisely to address this — turning dense but noisy community data into trustworthy information.
{% endstep %}

{% step %}
### Individual monitoring (wearables)

Wearable sensors take the same miniaturisation and affordability that made LCS possible and bring monitoring one step closer still: from the community to the individual. A fixed low-cost sensor still describes a place, even if it is a place the community cares about. A wearable describes a person — the specific air a specific individual breathes as they move through their day.

This is the natural endpoint of the progression: from the region (institutions), to the neighbourhood (communities), to the person (individuals).

Each step does not replace the one before; each answers a question the previous step could not. Reference stations answer “what is the regional air quality?” Low-cost sensor networks answer “how does air quality vary across our community?” Wearables answer “what am I actually breathing, right now, in this situation?”

Together, the three scales form a complete picture — and wearables are what extend citizen science all the way down to personal exposure.
{% endstep %}
{% endstepper %}

### What makes wearable sensing fundamentally different

The differences between wearable and fixed sensing go beyond physical form factor. They create a cascade of technical, methodological and ethical challenges:

| Dimension               | Fixed low-cost sensor                                                                 | Wearable sensor                                                                                                        |
| ----------------------- | ------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| **Location**            | Known, stable monitoring location with GPS coordinates recorded once at installation. | Continuously changing. GPS must be recorded every second; unreliable indoors.                                          |
| **Context**             | Limited variables, documented once at deployment.                                     | Unlimited, constantly changing: activity, transport, ventilation, personal emissions. Must be documented continuously. |
| **Temporal resolution** | Sufficient temporal resolution, ranging from minutes to hours.                        | Seconds needed to capture transients (entering a car park, cooking onset).                                             |
| **Quality control**     | Cross-comparison with neighbours. Spatial consistency.                                | Device often alone. Motion artefacts. Context changes faster than QC windows.                                          |
| **Privacy**             | Minimal privacy risk. Data describes a place, not a person.                           | High. Continuous GPS traces reveal home, work, habits. Full GDPR compliance required.                                  |
| **Purpose**             | Describe air quality at a location (mapping).                                         | Describe the air an individual breathes (exposure).                                                                    |
| **Engagement model**    | Passive: install once and operate passively.                                          | Active: carry, tag activities, respond to alarms, document events.                                                     |

### Specific challenges

#### Geolocation and GPS

* **Indoor GPS loss:** GPS signals degrade inside buildings, car parks and tunnels. The device may record valid air quality data while location is absent or inaccurate. Indoor periods must be flagged using proxy indicators such as luminosity, signal strength and accelerometer data.
* **Smartphone dependency:** When geolocation relies on the paired phone, the system inherits variability across GPS chipsets, battery-saving behaviours and OS permission models. A protocol that works on one phone model may produce 50-metre errors on another.
* **Precision vs. privacy:** A continuous trajectory at 1-second intervals trivially reveals where a person lives, works and socialises. The more precise the geolocation, the greater the privacy risk. This tension must be resolved architecturally, not by asking participants to trust.

#### Privacy and GDPR

Fixed sensors describe a place; wearable sensors describe a person. The moment a sensor follows an individual and records their GPS trajectory, the dataset becomes personal data under the GDPR (Regulation (EU) 2016/679), even if the environmental measurements themselves are not personal.

* **Informed consent:** Participants must understand what data is collected, how it will be stored, who has access, and for how long. Generic blanket consent is insufficient under GDPR.
* **Data minimisation:** Only data strictly necessary for the stated purpose should be collected. If full-precision GPS is not required, it should be degraded at collection, not stored in full and degraded later.
* **Geo-privacy by design:** The CitiObs architecture addresses this through a dual-datastream model. A private stream retains full-precision data accessible only to the participant; a public stream aggregates locations into geo-privacy cells. The effective spatial resolution follows the maximum of three levels: a legal minimum, a campaign default, and the participant’s own preference. This approach, supported by the OGC STAplus standard extensions, embeds privacy into the data architecture rather than relying on procedural safeguards alone.
* **Right to erasure:** Participants must be able to delete their data. The infrastructure must support selective deletion without corrupting aggregate datasets.
* **Authentication and ownership:** In CitiObs, the AUTHENIX service and STAplus data model ensure every observation is linked to an authenticated owner who controls access and licensing.

Privacy is not a constraint to be reluctantly satisfied; it is the foundation of trust that makes citizen-generated wearable data possible at scale.

#### Context: the most critical metadata

A fixed station operates in a context that changes slowly and is documented once. A wearable sensor operates in a context that changes every few minutes. Context determines whether a PM10 reading of 200 µg/m³ is a severe pollution event relevant for mapping or a participant sweeping drilling dust with a broom, relevant for exposure but irrelevant for ambient monitoring. Without context, the data is ambiguous.

#### Data quality: new artefacts

* **Motion artefacts:** Clothing brushing against the air inlet generates false PM readings. Empirical testing confirmed that improper mounting triggers alarms unrelated to ambient air quality.
* **Rapid transitions:** Moving from a clean office to a polluted street takes seconds to equilibrate. At 1-second resolution, transition artefacts are visible.
* **Intermittent time series:** Devices are turned off, lose Bluetooth, or run out of battery. Gaps must be documented.
* **Absence of spatial peers:** A wearable is often alone in its micro-environment. The FILTER framework’s mobile variant, developed within CitiObs as part of ValAir, addresses this with dedicated QC steps for moving sensors.

#### Two data streams, not one

The same device, in the same hour, produces data for two fundamentally different purposes:

* **Personal exposure stream:** all data including personal emissions such as cooking, smoking and cleaning, analysed by activity to give the individual feedback. This stream is private.
* **Ambient contribution stream:** data collected where the sensor reflects ambient conditions, outdoors and away from personal sources. Once quality-controlled and context-filtered, this stream feeds air quality mapping via the MapAir pipeline.

Separating these streams requires context. This is why context documentation and the dual-datastream architecture are foundational requirements, not optional features.

### The added value of wearable sensing

* **Empowering individuals:** Empirical studies have shown that individuals may be responsible for the vast majority of the PM they are exposed to on a given day. In a documented 48-hour study, one individual was responsible for 97% of their PM10 exposure, driven primarily by indoor activities. This insight is a powerful driver of behavioural change.
* **Filling the indoor blind spot:** People spend 80–90% of their time indoors, yet regulatory monitoring is designed for outdoor air. Wearable sensors provide data on the environments where exposure actually occurs.
* **Revealing micro-environments:** Underground car parks, kitchens, renovation sites, vehicle interiors — these have distinct and often severe pollution profiles invisible to any area-based approach.
* **Engaging citizens as investigators:** A fixed sensor turns a citizen into a host. A wearable turns them into an investigator who carries the device, observes alarms, documents causes and progressively understands their exposure dynamics.

These entries build on concepts from the Sensing Device, Managing Data and Sensor Data Platform categories. Readers new to low-cost sensing are encouraged to start with those categories first.

## What are wearable and mobile environmental sensing systems?

### Description

Wearable and mobile environmental sensing systems are portable devices designed to measure environmental conditions directly within the user’s surroundings during daily activities and mobility. Unlike fixed monitoring stations that remain at static locations, wearable systems move with the user and collect measurements across multiple environments throughout the day.

These systems typically integrate environmental sensors, a battery, positioning technology (GPS or smartphone-relayed), wireless communication (Bluetooth), onboard memory and often a companion smartphone application for visualisation, geolocation, synchronisation and user interaction. Some provide real-time values, charts and maps on the phone; others log data for later download.

Wearable systems may measure particulate matter (PM1, PM2.5, PM10), gase pollutants (NO₂, O₃, CO, CO₂, VOCs), temperature, humidity, noise or light. Some devices update every second, providing the temporal resolution needed to capture rapid exposure transients. Depending on the use case, they may be worn on the body, clipped to a bag or bicycle, placed in a vehicle, or simply carried.

A critical feature for personal exposure use is configurable alarms. When a device triggers an alert, for example PM2.5 above 15 µg/m³ for more than 30 seconds, the user looks around to understand the cause. This feedback loop turns the participant from a passive data carrier into an active investigator of their own environment.

### Why is this relevant?

Wearable systems make it possible to observe environmental conditions in everyday environments rather than only at fixed monitoring locations. They capture variability at spatial and temporal scales that fixed networks cannot reach: inside homes, during a commute, while cooking, in a car park.

Because they are portable and increasingly accessible, they create new opportunities for citizen participation. Participants interact directly with measurements from their own activities, which strengthens engagement and environmental understanding.

At the same time, wearable systems introduce significant technical and operational challenges: device usage, participant engagement, data quality, battery autonomy, motion artefacts and privacy. These are addressed in dedicated entries below.

### How can this be done?

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

### Useful resources

[Community Exposure Science Collaborative — Personal Exposure Toolkit Recorder](https://www.citizen.exposurescience.org/pet/petrecorder). A community exposure-science tool combining a portable sensor with a smartphone recorder. Useful as a concrete introduction to personal monitoring.

[HabitatMap — AirBeam Mini User’s Guide](https://www.habitatmap.org/airbeam/users-guide-airbeammini). A device-specific practical guide. Consult the mobile recording sections to understand the sensor–phone workflow and carrying requirements.

### You might also be interested in…

* [What are the main elements of a sensing device?](https://monitoring.toolkit.citiobs.eu/sensing-devices/what-are-the-main-elements-of-a-sensing-device)
* [What variables can be measured with air quality sensing devices?](https://monitoring.toolkit.citiobs.eu/sensing-devices/what-variables-can-be-measured-with-air-quality-sensing-devices)
* [What non-technical aspects to consider when choosing sensing devices?](https://monitoring.toolkit.citiobs.eu/sensing-devices/what-non-technical-aspects-to-consider-when-choosing-sensing-devices)

## What is the difference between ambient air quality and personal exposure?

### Description

Ambient air quality describes pollutant concentrations in the surrounding environment, measured by fixed stations, reference instruments or models. These systems characterise environmental conditions at the urban or regional scale.

Personal exposure describes the pollutants an individual actually encounters during daily activities. Exposure depends not only on concentration, but on time spent in an environment, activities performed, ventilation, mobility and proximity to sources.

### Why is this relevant?

Empirical measurements with wearable PM sensors have revealed findings that challenge common assumptions:

* **Indoor activities dominate exposure:** cooking in an open kitchen reached 108 µg/m³ of PM10. It took 35 minutes to return to baseline even with windows open. The worst outdoor reading at a busy intersection was 28 µg/m³.
* **Underground car parks are persistent hotspots:** PM accumulates on floors with no rain to wash it off. Vehicles put dust into suspension on arrival regardless of whether the engine is running — confirmed by testing: freewheeling in with the engine off produced the same high readings.
* **In-vehicle choices matter:** air recirculation mode reduced PM to \~1 µg/m³, closed windows gave \~10 µg/m³, open windows fluctuated between 4 and 37 µg/m³.
* **Cleaning method is decisive:** sweeping drilling dust with a broom reached 1,230 µg/m³. The same spot cleaned with a vacuum barely triggered a reaction.
* **Personal responsibility is higher than expected:** in a documented 48-hour study, the individual was responsible for 97% of their PM10 exposure, driven primarily by indoor activities.

These findings do not negate the importance of ambient monitoring; they show that it provides an incomplete picture. Wearable sensing fills the gap.

### How can this be done?

{% stepper %}
{% step %}
### Define the question

Are you studying where pollution is, mapping, or what people breathe, exposure? The answer determines experimental design, device choice and data processing.
{% endstep %}

{% step %}
### Design around activities, not locations

A personal exposure campaign is structured around cooking, commuting, cleaning, working and sleeping. The same location produces different readings depending on activity.
{% endstep %}

{% step %}
### Keep both data streams separate

Data from someone cooking or smoking is highly informative for exposure but noise for mapping. Mixing without context-based filtering produces misleading results for both purposes.
{% endstep %}

{% step %}
### Communicate the distinction

Participants and stakeholders must understand that personal sensor readings are not comparable to regulatory station data without accounting for context.
{% endstep %}
{% endstepper %}

### Useful resources

[Breathe London — Wearables Study (2019)](https://www.london.gov.uk/sites/default/files/the_breathe_london_wearables_study_oct19.pdf). A participatory study using monitoring backpacks to explore children’s exposure during school journeys and daily activities.

[Community Exposure Science Collaborative — Personal Exposure Toolkit FAQ](https://www.citizen.exposurescience.org/pet/pet-faq). Explains how personal measurements can address community questions and why individual exposure varies across everyday situations.

### You might also be interested in…

* [What aspects to consider when doing mobile monitoring?](https://monitoring.toolkit.citiobs.eu/sensing-devices/what-aspects-to-consider-when-doing-mobile-monitoring)
* [Why is it important to document context and how does it help better understand collected data?](https://monitoring.toolkit.citiobs.eu/managing-data/why-is-it-important-to-document-context-and-how-does-it-help-better-understand-collected-data)
* [How to Bring a Health Lens to Environmental Monitoring?](https://monitoring.toolkit.citiobs.eu/community/how-to-bring-a-health-lens-to-environmental-monitoring)

## Why is contextual information critical in wearable sensing?

### Description

When a fixed reference station reports PM2.5 at 25 µg/m³, the context is controlled: location, height, orientation, nearby sources and meteorology are all known. The number of variables is limited and well characterised.

A wearable sensor operates in a context that changes continuously. The same device might record data in a bedroom, kitchen, car, street, shop and office within a single hour. Without knowing which reading corresponds to which environment and activity, the raw data stream is uninterpretable. A PM10 reading of 50 µg/m³ could mean walking along a busy road or opening a bag of flour. Both are legitimate measurements, but they belong to entirely different analytical streams.

### Why is this relevant?

Context transforms raw sensor data into actionable information. Without it, cooking data cannot be separated from walking data, wearable data cannot feed mapping models because personal emissions contaminate the ambient signal, and contradictions arise between personal readings and official maps that erode trust if unexplained.

Conversely, when context is documented, even low-cost sensors reveal insights high-end instruments cannot: pollutant behaviour at different floor levels, ventilation impact in cars, comparative exposure between commuting modes, PM dynamics during different cooking techniques. Contextualised observations also enable before/after comparisons that make exposure concrete and actionable.

### How can this be done?

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

## What environmental variables can be monitored using wearable sensing systems?

### Description

Wearable systems can monitor a range of parameters depending on integrated sensors and project objectives. Air quality is the most common application, particularly particulate matter (PM1, PM2.5, PM10) because of its strong link to human activities, combustion sources and health impacts. Systems may also measure NO₂, O₃, CO, CO₂, VOCs, temperature, humidity, noise or light.

Not all variables are equally suited to wearable applications. Compact optical PM sensors have become particularly common because they achieve high temporal resolution in a small form factor. Gas sensors may require more power, more frequent calibration, and are often more sensitive to humidity and temperature changes during mobile use.

### Why is this relevant?

The usefulness of wearable observations depends on the match between the variable, the research question and the sensor’s capabilities:

* **PM:** relevant for combustion exposure, cooking, traffic, indoor dust and occupational settings. Most wearable-friendly sensor technology currently available.
* **NO₂:** relevant for traffic studies. Sensors exist but are more power-hungry and humidity-sensitive.
* **CO₂:** useful for evaluating indoor ventilation. Highly relevant for school and office environments.
* **Noise:** relevant for urban mobility, commuting analysis and occupational exposure.

Participants engage more when they can relate measurements to concrete activities. PM is intuitive because cooking, cleaning and traffic produce visible effects; CO₂ connects to ventilation; noise connects to comfort. Choosing relatable variables strengthens engagement.

{% hint style="warning" %}
Many optical PM sensors have a minimum detection size of 0.3 µm, meaning they miss ultrafine particles. This matters for in-vehicle exposure where combustion engines produce significant sub-0.3 µm particles.
{% endhint %}

### How can this be done?

{% stepper %}
{% step %}
### Define the environmental question

Define the question before selecting variables.
{% endstep %}

{% step %}
### Match variables to exposure scenarios

Match variables to the exposure scenarios of interest.
{% endstep %}

{% step %}
### Evaluate battery impact

More sensors mean shorter autonomy.
{% endstep %}

{% step %}
### Assess environmental sensitivity

Assess humidity and temperature sensitivity for the intended environments.
{% endstep %}

{% step %}
### Communicate sensor limitations clearly

Communicate detection range and interferences clearly.
{% endstep %}

{% step %}
### Test in realistic conditions

Test sensor performance in realistic conditions before scaling.
{% endstep %}
{% endstepper %}

### Useful resources

[expoAware — Participatory wearable monitoring in Leipzig](https://www.vgiscience.org/projects/expoaware.html). Describes wearable sensor combinations used during walking and cycling campaigns, including particles, gases and other environmental parameters.

[Community Exposure Science Collaborative — Personal Exposure Toolkit FAQ](https://www.citizen.exposurescience.org/pet/pet-faq). Describes the parameters reported by one portable monitoring setup. Use it as an example, alongside device-specific performance evidence.

### You might also be interested in…

* [What variables can be measured with air quality sensing devices?](https://monitoring.toolkit.citiobs.eu/sensing-devices/what-variables-can-be-measured-with-air-quality-sensing-devices)
* [What technical aspects to consider when choosing an air quality sensing device?](https://monitoring.toolkit.citiobs.eu/sensing-devices/what-technical-aspects-to-consider-when-choosing-an-air-quality-sensing-device)
* [I want to know what data & knowledge we need by deciding what data to collect](https://creating.toolkit.citiobs.eu/creating-and-running-a-citizen-observatory/i-want-to-know-what-data-and-knowledge-we-need-by-deciding-what-data-to-collect)

## What should be considered when deploying wearable sensing systems?

### Description

Deploying wearable systems involves far more than distributing devices. Unlike fixed stations in controlled environments, wearables are exposed to movement, changing conditions, user interactions and highly variable usage. Deployment conditions directly influence data quality, engagement, device reliability and the usability of collected observations.

### Why is this relevant?

Wearable systems partially depend on human adherence to protocols. If participants stop carrying the device, forget to charge, stop tagging activities or disengage, data quality deteriorates rapidly. Unlike fixed monitoring, the human is part of the measurement system.

Practical issues are often underestimated. Where to attach the device without having it in the way? How to ensure the air inlet does not generate false readings from clothing? Finding the right wearing position is genuinely challenging — the device is extremely sensitive and even the way it is clipped to a belt can produce particle artefacts from clothing friction.

### How can this be done?

{% stepper %}
{% step %}
### Define wearing position and test it

Test multiple positions, such as belt clip, bag strap and jacket pocket, and verify the air inlet is clear. Document the recommended position with photographs.
{% endstep %}

{% step %}
### Create a daily checklist

Is the device charged? Is Bluetooth connected? Is the app logging? One minute daily prevents data loss.
{% endstep %}

{% step %}
### Keep annotation minimal

Limit required tags to indoor/outdoor and a short activity list. Complex protocols kill compliance.
{% endstep %}

{% step %}
### Use short focused missions

A 48-hour cooking exposure study or a 1-week commuting comparison is easier to complete than open-ended monitoring.
{% endstep %}

{% step %}
### Provide meaningful feedback

Show participants their own data — a chart of their exposure by activity — early in the campaign. Nothing sustains engagement like seeing your own results.
{% endstep %}

{% step %}
### Monitor incoming data remotely

Detect technical issues or participant difficulties early rather than discovering data gaps at the end.
{% endstep %}

{% step %}
### Pilot end-to-end

Run the full workflow from device to dashboard with a small group. Every unforeseen issue found in pilot saves frustration at scale.
{% endstep %}
{% endstepper %}

### Useful resources

[La Captothèque — Sensors and equipment (in French)](https://captotheque.fr/fr/faq/categorie/capteurs-et-materiel). Practical citizen-facing guidance on starting a mobile session, adding tags and carrying the sensor without obstructing airflow. Adapt to your device.

[HabitatMap — AirBeam Mini User’s Guide](https://www.habitatmap.org/airbeam/users-guide-airbeammini). Use the mobile Bluetooth, sampling interval and connection sections when preparing participant instructions and a pilot session.

[Breathe London — Wearables Study (2019)](https://www.london.gov.uk/sites/default/files/the_breathe_london_wearables_study_oct19.pdf). A worked deployment example involving schoolchildren and monitoring backpacks. Useful for considering participant routines and campaign organisation.

### You might also be interested in…

* [What aspects to consider when doing mobile monitoring?](https://monitoring.toolkit.citiobs.eu/sensing-devices/what-aspects-to-consider-when-doing-mobile-monitoring)
* [What aspects to consider when writing guidance on how to install sensing devices?](https://monitoring.toolkit.citiobs.eu/sensing-devices/what-aspects-to-consider-when-writing-guidance-on-how-to-install-sensing-devices)
* [How can we ensure our CO is digitally inclusive?](https://inclusivity.toolkit.citiobs.eu/outreach-and-engagement/how-can-we-ensure-our-co-is-digitally-inclusive)

## What are the main quality challenges associated with wearable environmental monitoring?

### Description

Wearable sensors produce all the artefacts of fixed sensors, including drift, flatlines and spurious spikes, plus additional ones specific to mobile use: motion artefacts, rapid environment transitions, intermittent time series and the absence of spatial peers for cross-checking.

### Why is this relevant?

Poor quality control undermines trust in the data and in the project. With wearables the difficulty is sharper than with fixed sensors, because the usual safety net — cross-checking a suspect reading against nearby sensors — is rarely available. A wearable is typically alone in its micro-environment, so the platform cannot ask “do the neighbours agree?”

Quality control must instead rely on the device’s own behaviour over time, on context metadata such as activity, indoor/outdoor status and motion, and on the rare moments when the device passes close to a reference instrument.

The most damaging artefacts are also the hardest to distinguish from genuine exposure. A spike to 1,200 µg/m³ might be a real cooking or DIY event worth capturing, or it might be clothing brushing the air inlet — and only the accelerometer and activity tag can tell the two apart. A reading that looks like clean outdoor air might in fact be a sensor still equilibrating seconds after stepping out of a polluted kitchen. A gap in the time series might mean the participant paused monitoring, or simply that Bluetooth dropped.

Without context, every one of these is ambiguous; with context, each becomes interpretable.

Drift remains a concern too, but it must be handled differently than in a fixed network. Where a static sensor can be flagged by comparison with 30+ neighbours reading 6–18 µg/m³ while it alone reports 600+, a wearable has no such peers. Drift on a moving device has to be caught through temporal consistency within its own stream and through rendezvous checks when it passes a reference station — which is exactly what the mobile variant of the FILTER framework is designed to do.

### How can this be done?

The CitiObs ValAir toolkit provides the FILTER framework, with a mobile/wearable variant that applies a structured QC sequence:

{% stepper %}
{% step %}
### Range Check

Identifies physically impossible values, including negative concentrations and above-range readings.
{% endstep %}

{% step %}
### Flatline Check

Detects constant-value periods indicating hardware failure.
{% endstep %}

{% step %}
### Spatio-temporal Outlier Detection

Uses rolling statistics and cross-checks with reference data.
{% endstep %}

{% step %}
### Spatial Correlation and Similarity

Evaluates consistency with nearby sensors. For mobile sensors, a “Chain Test” evaluates rendezvous events when the wearable passes near a reference station.
{% endstep %}
{% endstepper %}

Beyond automated QC:

* **Educate on wearing correctly:** clothing friction, pocket placement and personal pollution sources generate artefacts.
* **Implement drift detection at platform level:** do not rely on participants to identify malfunction.
* **Distinguish raw and processed data:** always indicate whether QC has been applied. Offer both views so users can verify the underlying data is the same.

### Useful resources

[La Captothèque — Sensors and equipment (in French)](https://captotheque.fr/fr/faq/categorie/capteurs-et-materiel). Explains limitations of the service’s portable particle measurements and practical handling precautions. Useful for preparing realistic participant guidance.

[CitiObs — D2.3: ValAir and MapAir toolkits](https://citiobs.eu/wp-content/uploads/2026/03/CitiObs_D2.3-ValAir-MapAir-Toolkits_V1.pdf). Technical complement: section 3.1 includes mobile PM2.5 quality checks and comparison requirements. Adapt these to the wearable campaign; this is not wearable-specific validation.

### You might also be interested in…

* [What is data quality? How can we increase data quality in citizen gathered data?](https://monitoring.toolkit.citiobs.eu/managing-data/what-is-data-quality-how-can-we-increase-data-quality-in-citizen-gathered-data)
* [How to validate sensor data to create Analysis Ready Data?](https://monitoring.toolkit.citiobs.eu/data-integration/how-validate-raw-data)
* [How do we increase traceability in data collected by citizens?](https://monitoring.toolkit.citiobs.eu/managing-data/how-do-we-increase-traceability-in-data-collected-by-citizens)

## How can wearable data be transformed into analysis-ready exposure information?

### Description

Wearable devices generate massive volumes of data at high temporal resolution under dynamic conditions. Raw measurements alone are insufficient for meaningful exposure assessment. Before they support interpretation, they must be combined with context, quality-assessed and aggregated appropriately.

### Why is this relevant?

Participants confronted with thousands of rapidly changing values often cannot tell whether readings are normal, which activities drive exposure, or whether their behaviour makes a difference. Properly processed data transforms this noise into insight.

Activity-resolved analysis is particularly powerful. In one empirical study, grouping PM10 data by activity revealed that DIY activities, cooking and parking dominated exposure — by far — while time spent outdoors contributed comparatively little. This finding only emerged because measurements were associated with documented activities and analysed per time unit rather than as a flat average.

### How can this be done?

{% stepper %}
{% step %}
### Define outputs before collection

What exposure indicators will the project produce? Activity-based summaries, time-weighted metrics, before/after comparisons, exposure maps?
{% endstep %}

{% step %}
### Preserve raw data alongside processed data

Always maintain the original dataset. Processing decisions may need to be revised.
{% endstep %}

{% step %}
### Group by activity and environment

Calculate both total exposure, cumulative dose, and exposure rate, average concentration per time unit, for each activity. The rate reveals which activities are most hazardous per minute; the total reveals which contribute most overall.
{% endstep %}

{% step %}
### Use before/after comparisons

Participants can evaluate the impact of ventilation changes, commuting mode switches or cleaning method changes. These are concrete and actionable.
{% endstep %}

{% step %}
### Feed the CitiObs pipeline

Context-filtered ambient data enters ValAir for QC, VirtualAir for integration, and MapAir for visualisation. Personal exposure data stays on individual dashboards.
{% endstep %}

{% step %}
### Avoid over-aggregation

Hourly or daily averages hide the short-duration events that define personal exposure. Present both summaries and high-resolution traces.
{% endstep %}
{% endstepper %}

### Useful resources

[UrbanBetter — Citizen Science Insights on Air Quality from Three Cities in Africa](https://urbanbetter.science/archive/wp-content/uploads/2023/03/Citizen-science-insights-on-air-quality.pdf). Its methods describe cleaning and aligning measurements with run times and locations; its limitations help frame cautious interpretation.

[US EPA ExpoBox — Exposure Calculations](https://www.epa.gov/expobox/exposure-calculations). General methodological complement for distinguishing concentration, exposure and dose when analysing personal records. This is not a wearable field guide.

### You might also be interested in…

* [How to validate sensor data to create Analysis Ready Data?](https://monitoring.toolkit.citiobs.eu/data-integration/how-validate-raw-data)
* [How can I analyse and visualize my data?](https://monitoring.toolkit.citiobs.eu/managing-data/how-can-i-analyse-and-visualize-my-data)
* [How to make data accessible to non-experts in a clear and understandable format?](https://monitoring.toolkit.citiobs.eu/managing-data/how-to-make-data-accessible-to-non-experts-in-a-clear-and-understandable-format)

## How to maintain participant engagement and reduce user fatigue in wearable sensing projects?

### Description

Unlike fixed sensors that operate autonomously, wearable systems require continuous participant involvement: charging, carrying, synchronising, tagging activities and responding to alarms. This creates a much higher burden than most Citizen Observatory activities and inevitably generates fatigue over time.

### Why is this relevant?

Participant engagement directly determines data quality. If participants stop carrying the device, forget to charge, stop annotating or disengage, the dataset degrades. This is not a secondary concern — in wearable sensing, the human is part of the measurement system.

The good news is that wearable sensing offers a uniquely powerful engagement mechanism: personal relevance. When participants see that their cooking spiked PM10 to 108 µg/m³, that air recirculation in their car drops PM to 1 µg/m³, or that sweeping with a broom produces 40 times more particles than vacuuming, the data becomes personally meaningful. This connection between measurement and lived experience is the strongest engagement driver available.

### How can this be done?

{% stepper %}
{% step %}
### Use short focused missions

A “cooking week”, a “commuting comparison” or a “ventilation test”. These are easier to complete and produce cleaner, more interpretable data than open-ended monitoring.
{% endstep %}

{% step %}
### Show results early

Present participants with their own exposure chart within the first 48 hours. Waiting until the end of the campaign to provide feedback kills motivation.
{% endstep %}

{% step %}
### Leverage alarms as engagement tools

Configure threshold alarms and ask participants to document what triggered them with a photo and one sentence. This is far more practical than continuous logging and produces rich qualitative data.
{% endstep %}

{% step %}
### Design before/after experiments

Ask participants to cook with windows closed on Day 1, then open on Day 2. Compare. This creates a sense of investigation and control.
{% endstep %}

{% step %}
### Minimise annotation burden

Limit required tags to 4–6 categories. Automate everything else. A dataset with imperfect but consistent activity tags is more valuable than one where annotation was abandoned on Day 3.
{% endstep %}

{% step %}
### Organise interpretation workshops

Group sessions where participants discuss their data together sustain interest and produce collective insight.
{% endstep %}
{% endstepper %}

### Useful resources

[UrbanBetter — Nairobi Cityzens Run Leaders: Terms of Reference (2025)](https://cityzens.urbanbetter.science/wp-content/uploads/2025/02/ToR-Nairobi-Run-Leaders.pdf). A community programme example covering leader training, participant recruitment, sensing runs, collective review and communication of findings.

[Breathe London — Wearables Study (2019)](https://www.london.gov.uk/sites/default/files/the_breathe_london_wearables_study_oct19.pdf). Reports participant feedback from a school-based wearable study. Useful for planning explanations, engagement and feedback to families.

### You might also be interested in…

* [How can we maintain energy in our CO?](https://inclusivity.toolkit.citiobs.eu/outreach-and-engagement/how-can-we-maintain-energy-in-our-co)
* [I want to engage stakeholders in ways that keep them motivated over time](https://creating.toolkit.citiobs.eu/creating-and-running-a-citizen-observatory/i-want-to-engage-stakeholders-in-ways-that-keep-them-motivated-over-time)
* [How to promote involvement and participation in environmental monitoring to minimize data gaps?](https://monitoring.toolkit.citiobs.eu/community/how-to-promote-involvement-and-participation-in-environmental-monitoring-to-minimize-data-gaps)

## What ethical and privacy considerations should be addressed in wearable sensing projects?

### Description

Wearable projects collect environmental data that is inherently linked to personal trajectories, routines and behaviours. Even without names, continuous mobility traces can reveal homes, workplaces, health facilities and daily habits. This makes wearable data personal data under GDPR, regardless of whether the environmental measurements themselves are sensitive.

### Why is this relevant?

Privacy failures destroy trust and kill participation. Conversely, projects that handle privacy well build the sustained engagement that produces long-term datasets of scientific value.

Ethical concerns extend beyond data protection. Wearable observations may generate anxiety if participants see high readings without proper interpretation support. A PM10 spike during cooking does not mean a health emergency, but without explanation, participants may panic or lose trust in the monitoring system.

### How can this be done?

{% stepper %}
{% step %}
### Embed privacy in architecture, not just policy

The CitiObs dual-datastream model maintains a private stream, full precision and participant-only access, and a public stream, geo-privacy cells. The effective resolution follows max (legal minimum, campaign default, user preference). This is enforced by the system, not by goodwill.
{% endstep %}

{% step %}
### Obtain specific informed consent

Explain what is collected, why, how, by whom and for how long. Generic blanket consent does not satisfy GDPR.
{% endstep %}

{% step %}
### Apply data minimisation

Collect only what is needed. If full GPS precision is not required, degrade at collection.
{% endstep %}

{% step %}
### Support right to erasure

Ensure individual contributions can be deleted without corrupting aggregates.
{% endstep %}

{% step %}
### Communicate interpretation, not just data

Accompany exposure readings with context: what the value means, how it compares to guidelines, and whether it represents a transient or chronic situation.
{% endstep %}

{% step %}
### Use AUTHENIX/STAplus for ownership

Every observation is linked to an authenticated owner with licensing preferences and access control.
{% endstep %}
{% endstepper %}

### Useful resources

[European Commission — Principles of personal data processing under the GDPR](https://commission.europa.eu/law/law-topic/data-protection/information-business-and-organisations/principles-gdpr_en). General legal guidance for specifying purposes, minimising personal data and explaining retention and sharing in wearable campaigns.

[Data Protection Commission — Anonymisation and pseudonymisation](https://www.dataprotection.ie/en/dpc-guidance/anonymisation-pseudonymisation). General privacy guidance relevant to trajectories: removing names or reducing spatial precision does not automatically make personal monitoring data anonymous.

### You might also be interested in…

* [I want to set up a Citizen Observatory and comply with ethics](https://creating.toolkit.citiobs.eu/creating-and-running-a-citizen-observatory/i-want-to-set-up-a-citizen-observatory-and-comply-with-ethics)
* [What are the main aspects you need to consider when managing citizen collected data?](https://monitoring.toolkit.citiobs.eu/managing-data/what-are-the-main-aspects-you-need-to-consider-when-managing-citizen-collected-data)
* [I want to work with data by sharing our Citizen Observatory data](https://creating.toolkit.citiobs.eu/creating-and-running-a-citizen-observatory/i-want-to-work-with-data-by-sharing-our-citizen-observatory-data)

## How can wearable sensing contribute to next-generation Citizen Observatories?

### Description

Traditional Citizen Observatories have relied on fixed sensing, participatory reporting or community-based monitoring at neighbourhood or city scale. Wearable technologies complement these by introducing mobile, dynamic, human-centred observations that capture how environmental conditions are actually experienced during daily life.

### Why is this relevant?

Wearable sensing shifts Citizen Observatories from purely location-centred monitoring toward exposure-oriented observation. Participants are no longer only observing pollution at fixed points; they observe how exposure changes depending on environment, activity, behaviour and mobility.

This shift creates stronger links between observation, personal experience and behavioural understanding. It also provides data from locations no fixed infrastructure can reach: inside homes, during commutes, in workplaces and at different floor levels of buildings.

The lesson from other domains is that the greatest progress comes not from mixing wearable data with fixed-station data, but from combining the complementary insights each technology provides. Fixed monitoring gives the broad environmental context; wearable sensing reveals how that environment is experienced. Together, they enable more contextual, participatory and exposure-aware observation systems.

### How can this be done?

{% stepper %}
{% step %}
### Position wearable sensing as complementary

Within the CO strategy, use fixed networks for ambient context and wearable campaigns for exposure investigations.
{% endstep %}

{% step %}
### Design dual-purpose campaigns

Use some periods for free-movement personal exposure, with activity logging, and others for standardised ambient measurement, with the device on a windowsill. Two datasets from the same devices.
{% endstep %}

{% step %}
### Use the CitiObs pipeline

Feed ambient-equivalent data through ValAir → VirtualAir → MapAir. Keep personal exposure data on individual dashboards. Use context to route data.
{% endstep %}

{% step %}
### Communicate the dual value

Participants’ data helps them understand their own exposure and contributes to the community’s environmental picture. This dual proposition strengthens engagement.
{% endstep %}

{% step %}
### Invest in interpretation, not just collection

Workshops, feedback sessions and participatory analysis are where wearable data becomes understanding. The device collects; the community interprets.
{% endstep %}
{% endstepper %}

### Useful resources

[CitiObs — D2.1: Technical Architecture](https://citiobs.eu/wp-content/uploads/2025/02/CitiObs_D2.1-Technical-architecture_V2.pdf). Technical complement describing the wider CitiObs architecture. Use it to consider how wearable observations could enter validation, integration and mapping workflows.

### You might also be interested in…

* [How to deploy an architectural stack that transforms raw data to Decision Ready Information?](https://monitoring.toolkit.citiobs.eu/data-integration/how-deploy-arch-stack)
* [How can we ensure uptake of CO-generated data?](https://participation.toolkit.citiobs.eu/how-can-we-improve-the-participation-dynamics-in-our-citizen-observatory/how-can-we-ensure-uptake-of-co-generated-data)
* [Defining the scope](https://action.toolkit.citiobs.eu/lets-begin/defining-the-scope)

## Wearable monitoring in practice with PMScan

### Connecting the cookbook principles in one application

PMScan provides a practical illustration of the needs discussed in this chapter: recording measurements during everyday activities, documenting their context, interpreting personal exposure and deciding which observations contribute to a group. The following example connects these needs to the application’s design choices and explains the limits that remain relevant when using its outputs.

The solution comprises a sensor connection, a mobile application and account-based services for groups and synchronisation. A recording session is called a mission. Participants can record missions, review their observations and choose whether a mission contributes to their active group.

### Connecting a portable sensor to a usable recording system

The deployment questions in this chapter emphasise that a wearable system includes more than the sensor. PMScan illustrates the supporting role of a phone application: connecting the instrument, organising sessions and retaining records that can be reviewed and exported.

The application is built with React and TypeScript, with Capacitor integration for mobile functions such as Bluetooth Low Energy and geolocation. Android and iOS platform dependencies are present in the codebase; compatibility with a particular phone, operating-system version and sensor must be checked for the intended deployment.

The measurement model supports PM1, PM2.5 and PM10 concentrations. Additional fields include temperature, relative humidity, pressure and TVOC when supplied by the connected device. These fields describe the application’s data model; they do not mean that every compatible sensor measures every parameter. Sensor accuracy, response time and detection limits remain properties of the selected instrument.

Missions combine time-stamped measurements, recording duration, available geographical coordinates and context labels. The application includes local storage and account synchronisation. Mission data can be exported as CSV, including measurement, location and context fields; analysis views also provide PDF reporting. Availability of online group and synchronisation functions depends on the associated services.

### Making measurements meaningful through context

During a mission, participants can update both a place category and an activity label. The place category describes the setting, such as home, work or transport; the activity describes what is happening, such as cooking, walking or cleaning. These labels are stored alongside the measurements and timestamps.

Geolocation supplies geographical context when available. Activity and place annotations remain useful indoors or wherever GPS is uncertain: coordinates alone cannot explain a peak or identify the circumstances of exposure. The combined record helps distinguish changes associated with activities, environments and journeys, while retaining the need for interpretation and measurement-quality checks.

### Giving participants a common campaign framework

Comparable observations require participants to describe their situations using a shared vocabulary. PMScan addresses this organisational need through campaign groups and their common settings.

Participants can join a campaign group through an invitation, including a link or QR code. Selecting an active group loads its configured place and activity categories, concentration bands and alert settings. Activities can be organised within place categories, allowing a campaign to define a vocabulary suited to its objectives.

This configuration supports consistent annotation across participants and reduces individual setup. Concentration classifications and activity classifications serve different purposes: one describes measurement ranges; the other describes context. Group thresholds are campaign settings whose meaning and averaging period should be explained, rather than assumed to be medical warnings or regulatory limits.

### Separating personal recording from group contribution

Individual exposure monitoring and contribution to a community dataset are different uses of the same recording. PMScan makes this distinction visible through a mission-level sharing choice.

The mission-saving dialogue includes a sharing control. A mission saved with sharing enabled in group mode is associated with the active group and can contribute to its collaborative views. Participants can also save missions without selecting group sharing.

The sharing choice concerns contribution to the group; it is separate from personal account storage and synchronisation. A mission not shared with a group may still be synchronised to the participant’s account. In the current implementation, the sharing control can already be enabled when group mode is active, so its state should be made clear before a mission is saved. Group sharing should not be equated with unrestricted publication on the internet.

### Moving from individual observations to collective interpretation

The interpretation questions call for views that help participants investigate their observations. PMScan connects personal time series and maps with a collective geographical view of selected contributions.

Mission views combine maps and time-series graphs, while contextual analysis relates measurements to recorded activities and places. Together, these views help participants investigate where values changed, what they were doing and which observations deserve further discussion.

The collaborative map aggregates shared group observations into geographical cells. It presents PM concentrations together with measurement and contributor counts, supporting discussion of patterns across the monitored area. Cell values reflect the available observations: differences in sampling time, coverage, participant behaviour and sensor performance still matter when comparing locations.

### Turning concentration records into exposure indicators

The chapter distinguishes a measured concentration from exposure accumulated over time. PMScan illustrates how these quantities can be summarised, and how estimating inhaled dose introduces an additional assumption about breathing.

PMScan includes complementary ways to summarise personal measurements. Mean concentration is expressed in µg/m³. Time-integrated exposure combines concentration and duration and is expressed in µg·h/m³. Contextual views use this quantity to compare the contribution of recorded activities or places over the selected period.

The application also contains an estimated inhaled-dose calculation for particulate matter: concentration (µg/m³) × duration (h) × assumed inhalation rate (m³/h), giving an estimated mass in µg. The inhalation rate is selected from an activity-based lookup, with fallback assumptions when the context is unknown. It is not a measurement of the participant’s breathing, and the result is not a measured deposited dose in the lungs.

These indicators support exploration and comparison, provided that the pollutant, monitored duration, coverage and assumptions are made explicit. Estimated dose depends on the chosen inhalation rate and activity classification. Gaps, non-wear periods and mixed-activity missions can affect the result; the outputs should not be presented as clinical measurements or individual health-risk predictions.

### Reducing spatial detail in shared outputs

Wearable trajectories can reveal personal routines. PMScan illustrates one response to this concern: reducing the spatial detail of the collaborative representation, while recognising that this does not resolve every data-protection requirement.

PMScan implements spatial generalisation using geohashes. A geohash represents a geographical cell, and its precision determines the area represented. The group can configure the precision used by the collaborative map, allowing observations to be combined into broader areas instead of showing each exact GPS position on that map.

This obfuscation reduces the spatial detail displayed in the collective view. It involves a practical trade-off: larger cells conceal more local detail but also smooth environmental variation. Original coordinates remain in the underlying measurement records; the map’s reduced precision is therefore not, by itself, a guarantee of anonymity or protection across every access and export route.

For a GDPR-aligned deployment, the campaign must define the data controller, purposes, lawful basis, access roles, retention period and procedures for participant rights. Sharing controls and spatial generalisation can support this framework, but do not establish compliance on their own. Timestamps, repeated journeys and contextual annotations must also be considered when assessing whether a person could be identified.

### What this example illustrates

PMScan brings the cookbook’s emphasis on context into the recording and interpretation process. Groups provide shared categories, participants document their situations, personal views support reflection, and selected observations contribute to collaborative maps. Its value lies in connecting measurement with context and participation while making the distinctions between concentration, exposure, estimated dose and data-sharing choices explicit.

### Data protection references

[European Commission guidance on personal data processing](https://commission.europa.eu/law/law-topic/data-protection/information-business-and-organisations/principles-gdpr_en)

[Data Protection Commission guidance on anonymisation and pseudonymisation](https://www.dataprotection.ie/en/dpc-guidance/anonymisation-pseudonymisation)

## Wearable monitoring in practice with the CitiObs PMScan to STAplus App

### From a personal recording to an interoperable observation

The CitiObs PMScan to STAplus App, developed by project partners, illustrates another part of the wearable monitoring workflow: carrying observations from a portable sensor into a shared data infrastructure without losing their measurement context. The iOS application receives readings from a PMScan sensor over Bluetooth, stores recordings on the phone and subsequently uploads selected recordings to a CitiObs STAplus server.

Where the preceding PMScan example highlights contextual interpretation and campaign participation, this example makes the recording and transfer process particularly explicit. It shows how sensor values, time, location, activity, ownership and reuse conditions can travel together as structured observations.

### Choosing how to collect observations in the field

The deployment section stresses that recording settings should match the monitoring question. Here, participants can select a sensor sampling interval of 1, 5, 10 or 30 seconds, or 1 or 5 minutes. The application displays PM1, PM2.5 and PM10 concentrations in µg/m³, temperature in °C and relative humidity, together with the last update time and sensor battery status.

Connecting the sensor sets its clock and starts its measurement cycle; saving a recording is a separate action. Connection-state indicators and a no-data warning help participants recognise interruptions. Bluetooth background operation and background location during recording support collection when the application is not on screen. If the sensor disconnects, recording stops automatically. This makes the interruption explicit, although it does not replace checks for missing data or correct wearing position.

### Keeping activity and environment alongside each sample

As explained in the context section, the same concentration may have different meanings in different situations. Before recording, the participant selects INDOOR or OUTDOOR, and can change this environment label during the recording. An activity picker provides walking, smoking, cooking, sleeping and sitting labels. Each stored sample combines the readings with its time, available GPS position, environment and activity.

Participants can create a named Track with a description, or choose Observations only. A Track provides a way to keep a journey or session together; observations-only recording retains individual samples without that additional grouping. The location display indicates when there is no GPS fix, reminding the user that a valid sensor reading does not necessarily have a reliable geographical position.

### Separating collection from the decision to transfer

The sharing discussion distinguishes recording from making data available elsewhere. This application implements that separation through local recording followed by an explicit upload step. Recordings are saved as JSON files on the phone using iOS file protection; recorded measurement data are not sent to the STAplus server during collection.

An upload list shows pending, uploading, uploaded and failed recordings. The participant selects which recordings to transfer and chooses a reuse licence from the list supplied by the server. Progress is displayed for each recording, and failed uploads can be retried. Local recordings can be deleted, including those already uploaded. Deleting a local copy should not be understood as deleting its server counterpart.

If the application is terminated, an unfinished recording is closed on the next launch, and an interrupted upload is marked as failed for retry. These mechanisms illustrate how a wearable workflow can make unfinished collection and transfer states visible rather than leaving participants uncertain about what has been saved.

### Preserving meaning when measurements enter STAplus

The data-integration section emphasises that transferable observations require more than a list of numbers. During upload, the application creates or reuses the necessary user, device, sensor and measurement-location records, together with a separate data stream for each of the five measured variables. WMO, EnvThes or QUDT definitions identify the measured quantities.

Each sample becomes an ObservationGroup containing its five observations. When a Track was selected, those observations are also linked to it and the Track receives start and end times. Activity records are linked to the measurement location. In this way, simultaneous readings remain associated and their context remains available for subsequent processing. An ObservationGroup is a data grouping, not a participant or campaign group.

The upload workflow reuses a measurement location while movement remains below 10 metres and the environment label is unchanged. This is a location-management rule, not a claim of 10-metre GPS accuracy or a privacy guarantee.

### Supporting geographical exploration without assuming anonymity

The application attaches an H3 grid-cell identifier at resolution 9 to each observation, calculated on the phone. This supplies a common spatial reference for downstream grouping or mapping. A link to the PMScan Viewer provides access to the associated web-map interface.

This spatial indexing serves a different role from the configurable geohash generalisation described in the preceding PMScan example. Adding an H3 cell identifier does not itself establish that precise coordinates are removed or hidden from other users. Access to locations, viewer visibility and any additional privacy transformations must be specified separately.

### Connecting identity and reuse conditions to responsible sharing

The application uses Authenix, the CitiObs identity provider, for sign-in. It checks the identity token’s issuer, audience and expiry, stores tokens in the iOS Keychain and renews the session as needed. Logout disconnects the sensor, stops location collection and resets the server connection. Links provide access to terms and privacy information and the Authenix authorised-apps page.

These features illustrate several building blocks for responsible data handling: protected credentials, an explicit transfer step and a licence associated with reuse. They do not, on their own, define who may read uploaded observations or establish GDPR compliance. As discussed earlier in the cookbook, the deployment still needs clear purposes, access permissions, retention arrangements and procedures for participant rights. A reuse licence is also distinct from the lawful basis for processing personal data.

### What this example illustrates

The CitiObs PMScan to STAplus App demonstrates how a wearable campaign can connect field collection to interoperable data publication: participants configure recording, document context, retain data locally and choose recordings and a licence for transfer. The resulting STAplus observations preserve relationships between readings, locations, activities and tracks. This complements the preceding example by showing the practical steps that make personal measurements available for subsequent analysis and visualisation.
