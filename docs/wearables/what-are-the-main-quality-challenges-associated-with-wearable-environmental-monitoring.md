---
icon: circle-exclamation
---

# What are the main quality challenges associated with wearable environmental monitoring?



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

##
