---
icon: chart-mixed
---

# How can wearable data be transformed into analysis-ready exposure information?



## Description

Wearable devices generate massive volumes of data at high temporal resolution under dynamic conditions. Raw measurements alone are insufficient for meaningful exposure assessment. Before they support interpretation, they must be combined with context, quality-assessed and aggregated appropriately.

## Why is this relevant?

Participants confronted with thousands of rapidly changing values often cannot tell whether readings are normal, which activities drive exposure, or whether their behaviour makes a difference. Properly processed data transforms this noise into insight.

Activity-resolved analysis is particularly powerful. In one empirical study, grouping PM10 data by activity revealed that DIY activities, cooking and parking dominated exposure — by far — while time spent outdoors contributed comparatively little. This finding only emerged because measurements were associated with documented activities and analysed per time unit rather than as a flat average.

## How can this be done?

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
