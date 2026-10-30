---
icon: eye-slash
---

# What ethical and privacy considerations should be addressed in wearable sensing projects?



## Description

Wearable projects collect environmental data that is inherently linked to personal trajectories, routines and behaviours. Even without names, continuous mobility traces can reveal homes, workplaces, health facilities and daily habits. This makes wearable data personal data under GDPR, regardless of whether the environmental measurements themselves are sensitive.

## Why is this relevant?

Privacy failures destroy trust and kill participation. Conversely, projects that handle privacy well build the sustained engagement that produces long-term datasets of scientific value.

Ethical concerns extend beyond data protection. Wearable observations may generate anxiety if participants see high readings without proper interpretation support. A PM10 spike during cooking does not mean a health emergency, but without explanation, participants may panic or lose trust in the monitoring system.

## How can this be done?

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

## Useful resources

[European Commission — Principles of personal data processing under the GDPR](https://commission.europa.eu/law/law-topic/data-protection/information-business-and-organisations/principles-gdpr_en). General legal guidance for specifying purposes, minimising personal data and explaining retention and sharing in wearable campaigns.

[Data Protection Commission — Anonymisation and pseudonymisation](https://www.dataprotection.ie/en/dpc-guidance/anonymisation-pseudonymisation). General privacy guidance relevant to trajectories: removing names or reducing spatial precision does not automatically make personal monitoring data anonymous.

## You might also be interested in…

* [I want to set up a Citizen Observatory and comply with ethics](https://creating.toolkit.citiobs.eu/creating-and-running-a-citizen-observatory/i-want-to-set-up-a-citizen-observatory-and-comply-with-ethics)
* [What are the main aspects you need to consider when managing citizen collected data?](https://monitoring.toolkit.citiobs.eu/managing-data/what-are-the-main-aspects-you-need-to-consider-when-managing-citizen-collected-data)
* [I want to work with data by sharing our Citizen Observatory data](https://creating.toolkit.citiobs.eu/creating-and-running-a-citizen-observatory/i-want-to-work-with-data-by-sharing-our-citizen-observatory-data)

##
