---
icon: people-arrows
---

# How to maintain participant engagement and reduce user fatigue in wearable sensing projects?



## Description

Unlike fixed sensors that operate autonomously, wearable systems require continuous participant involvement: charging, carrying, synchronising, tagging activities and responding to alarms. This creates a much higher burden than most Citizen Observatory activities and inevitably generates fatigue over time.

## Why is this relevant?

Participant engagement directly determines data quality. If participants stop carrying the device, forget to charge, stop annotating or disengage, the dataset degrades. This is not a secondary concern — in wearable sensing, the human is part of the measurement system.

The good news is that wearable sensing offers a uniquely powerful engagement mechanism: personal relevance. When participants see that their cooking spiked PM10 to 108 µg/m³, that air recirculation in their car drops PM to 1 µg/m³, or that sweeping with a broom produces 40 times more particles than vacuuming, the data becomes personally meaningful. This connection between measurement and lived experience is the strongest engagement driver available.

## How can this be done?

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

##
