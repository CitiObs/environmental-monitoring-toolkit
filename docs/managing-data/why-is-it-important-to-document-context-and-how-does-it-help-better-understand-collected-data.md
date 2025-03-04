---
icon: arrows-to-circle
---

# Why is it important to document context and how does it help better understand collected data?

## Description

Contextualization in data gathering involves providing additional information surrounding the collected data (e.g., air pollutant levels) to offer a clearer understanding of its significance and implications. This additional information, or context, typically includes details about the circumstances under which the data was collected, the conditions surrounding the observation, and any relevant factors that may influence its interpretation. Documenting context is even more critical when using wearables as often used while moving, measurement context may change a lot in time. Context provides the key to understanding what the data is about.

## Why is this relevant?

Adding context to air quality data collected by citizens is crucial for ensuring its accuracy, interpretability, and usefulness. Contextual information, such as the location, time, and potential sources of pollution, helps verify the reliability of the data and aids in its interpretation. This context allows users to understand why certain readings are high or low, making comparisons between different datasets more meaningful and actionable. Overall, contextualizing citizen-collected air quality data enhances its value (i.e. making it more trustable) for a wide range of stakeholders, including policymakers, researchers, public health officials, and the general public.

## How can this be done?

Some types of context data are available through online sources or even provided by the sensor device itself. That is for example the case of weather parameters that can be accessed through online meteorological services and some parameters like temperature and relative humidity are usually measured by the sensing device. But very often, context data needs to be reported by the person collecting the data, that is for example the case if the device is indoor or outdoor, heigh of installation, or potential local sources of pollution like smoking or barbecuing. However, it is important to note that nowadays most sensor platforms do not include any entry point for contextual information provided by the sensor users, so the participants might need to keep their own registers in logbooks.

1. **Identify the context information you need:** when it comes to contextualizing data collected by citizens it is important to assess what information will be needed. This will depend on the objectives, for example if we want to conduct behaviour impact assessment we must make sure that we are going to be able to know “what” happened “when” in order to link it to the pollution levels. Some examples of general context information are:
   1. **Location information:** include precise location data for each device deployment. This could be GPS coordinates or detailed descriptions of the devices’ placement, such as proximity to roads, industrial areas, or green spaces. Location information helps understand local environmental conditions that might influence air quality.
   2. **Time stamps:** record the date and time of each data point collected. This allows for tracking changes over time and identifying patterns or trends in air quality fluctuations. This is usually done automatically by the sensing device. When using diffusive samplers, this needs to be done manually.
   3. **Surroundings:** document nearby sources of pollution, such as factories, traffic congestion, construction sites, agricultural activities, or any unusual polluting activities. Understanding potential sources of contamination helps interpret air quality data more accurately.
2. **Identify sources of contextual information:** there might be on-line or local sources that can provide you with contextual information to enrich your data. By consulting these (online) sources, you can access a wealth of contextual information relevant for understanding air pollution and its impacts on health and the environment. Some examples are:
   1. **Environmental Protection Agencies (EPA):** many countries have their own EPA websites where they provide air quality data along with contextual information such as pollution sources, regulations, and health effects. For example, the European Environmental Agency provides comprehensive information on air quality, including data, reports, and educational resources. Data from official reference stations can be accessed through the website and through an API.
   2. **Local government:** check the websites of local government agencies responsible for environmental protection or public health. These websites often provide air quality data specific to your region along with information about pollution sources, regulations, and initiatives to improve air quality.
   3. **Meteorological institutes:** the national meteorological institutes often provide information on their website about atmospheric conditions such as temperature, humidity, wind speed, and precipitation, which can influence air quality. Understanding these factors can provide valuable context when interpreting air quality data.
3. **Protocols and training:** create a form that lists all the context information you want to have collected and train your participants to log this information alongside using the air quality sensor. Be aware that collecting contextual information might be an additional burden, so it is important to keep it simple while still collecting all relevant information. Make a plan on what information can be collected automatically (e.g. providing extra sensors like GPS, luminosity, accelerometer; and accessing online services like google maps) and what data can only be provided by the participant (e.g. singular polluting activities, malfunction of the sensor, spiderwebs, or ice in the sensing units, etc.)

## Useful resources

* Jotform [www.jotform.com](http://www.jotform.com) is a great tool to create custom logbooks in a user-friendly interface. It works like a Google Form but has way more options
* Google Data Studio: Google Data Studio enables users to create customizable reports and dashboards using data from multiple sources. It's helpful for integrating contextual information with data visualization to provide insights. [Google Data Studio](https://datastudio.google.com/)
* Plotly: Plotly is a platform for creating interactive plots, graphs, and dashboards. It supports various programming languages like Python, R, and JavaScript, making it versatile for data analysis and visualization tasks. [Plotly](https://plotly.com/)
* OpenRefine: OpenRefine is a powerful tool for cleaning and transforming messy data. It's useful for preprocessing data before analysis and contextualizing it by standardizing formats, correcting errors, and enriching with additional information. [OpenRefine](http://openrefine.org/)
* Google Earth Engine: Google Earth Engine is a platform for analyzing and visualizing geospatial data. It's helpful for contextualizing data by incorporating satellite imagery, environmental data, and other geospatial information. [Google Earth Engine](https://earthengine.google.com/)

## You might also be interested in….

* [Who is who in air quality environmental monitoring?](../environmental-monitoring/who-is-who-in-air-quality-environmental-monitoring.md)
* [What variables can be measured with air quality sensing devices?](../sensing-devices/what-variables-can-be-measured-with-air-quality-sensing-devices.md)
* [What are the main aspects you need to consider when managing citizen collected data?](what-are-the-main-aspects-you-need-to-consider-when-managing-citizen-collected-data.md)
