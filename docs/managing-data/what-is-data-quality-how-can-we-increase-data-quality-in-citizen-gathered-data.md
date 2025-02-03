# What is data quality? How can we increase data quality in citizen gathered data?

## Description

Data quality in the context of environmental monitoring refers to the accuracy, reliability, completeness, and relevance of the data collected and analysed to assess the condition of the environment. In environmental monitoring, data quality is crucial for making informed decisions regarding environmental management, policy development, and regulatory compliance. Official environmental monitoring, also known as regulatory monitoring, requires adherence to standardized protocols, rigorous quality assurance and quality control procedures. In Citizen Science and Citizen Observatories, data quality assurance poses unique challenges. However, with appropriate training, protocols, and quality assurance measures, CS/CO initiatives can produce valuable datasets that contribute to scientific knowledge and inform decision-making.

The quality of data required varies depending on the specific application or purpose for which the data will be used, while high-quality data is preferred and often essential for scientific research and critical decision-making, the required level of data quality depends on the specific application, context, and objectives of the data use.

## Why is this relevant?

The relevance of data quality in Citizen Science cannot be overstated. It plays a critical role in the success, credibility, and impact of CS/CO initiatives. That said, it is important to state that for the data to be valuable, we do not always require data of the highest quality, but rather data of known quality. Understanding the trade-offs between data quality and other factors such as cost, time, and resources is crucial for effectively leveraging data to support informed decisions and achieve desired outcomes.

## How can this be done?

Understanding data quality from sensing devices, requires us to be familiar with these terms:

1. **Accuracy:** accuracy is how close a given set of measurements are to their true value. You can assess the accuracy of the sensor measurements by comparing them to reference measurements from validated instruments or established monitoring stations. For air quality, some governments have reference monitoring stations.
2. **Precision:** precision is a measure for how close the measured data lie together. You can evaluate the precision of the sensor measurements by assessing their repeatability and consistency over time. Repeat measurements under controlled conditions can help determine the sensor's precision and variability. You can also check how different sensors compare to each other by having them measuring at the same location.
3. **Cross-sensitivity:** sensing devices may exhibit cross-sensitivity to other gases or environmental factors, leading to potential inaccuracies in the measurements. The devices’ performance can vary under different environmental conditions, such as temperature and humidity. Extreme environmental conditions may also affect accuracy and reliability. Understanding the sensor's selectivity and potential for cross-sensitivity is important to avoid misinterpretation of the data.
4. **Response time:** consider the sensors’ response time, which refers to the time it takes to detect changes in air quality. Faster response times are desirable for capturing rapid changes in pollution levels, especially for mobile monitoring.
5. **Signal Drift:** sensing devices may exhibit drift over time, leading to gradual changes in baseline readings or sensor response. Checking for sensor drift involves monitoring changes in sensor readings over time and comparing them to expected behavior or reference measurements. Plot the data over time to visually inspect for any gradual shifts or trends in the baseline readings. Drift may manifest as a consistent increase or decrease in sensor values over time.
6. **Relative vs absolute data:** in some cases, sensors are not accurate enough to provide absolute values (i.e. air quality concentration levels) but they still can provide valuable relative data. Relative data can be useful for detecting trends and patterns in air quality over time (e.g. seasonal trends) or across different locations (e.g. identifying hotspots). A sensor should exhibit stability and consistency in its response over time and under varying environmental conditions. Stability ensures that the sensor's baseline remains unchanged over extended periods, while consistency ensures that the sensors’ responses to similar conditions are reproducible and predictable.

A Citizen Science project can increase data quality when using sensing devices through several strategies:

1. **Standardized protocols:** clearly define data collection methods, sampling protocols, device deployment techniques, and data recording formats to minimize variability and enhance data quality. Provide comprehensive training and educational resources to citizen scientists to ensure they understand the protocols.
2. **Contextualization:** provide contextual information to help interpret and contextualize the sensor data collected by citizen scientists. Encourage participants to verify their data and provide feedback on data quality issues or anomalies encountered during data collection. Establish protocols for reporting data discrepancies, sensor malfunctions, or environmental factors that may affect data quality.
3. **Data verification and feedback:** check routinely the data collected in the project and encourage participants to do the same. Establish communication channels for reporting data discrepancies and sensing device malfunctions and provide timely feedback and support to address these issues.
4. **Noise reduction through data averaging:** implement techniques for noise reduction by averaging sensor data over time or space. Averaging data over multiple time intervals (e.g., hourly, daily) or spatial locations can help mitigate random fluctuations or short-term variations in readings, resulting in smoother and more stable datasets.
5. **Increase provenance:** air quality data obtained from government agencies, environmental monitoring networks, or research institutions typically comes with well-established provenance information. While citizen-collected data may lack the institutional backing and formal validation processes of official sources, providing comprehensive provenance information is a good way for enhancing data credibility and usability. Citizen Science projects can increase provenance by documenting sensor specifications, calibration procedures, data collection protocols, and any quality assurance measures and data calibration implemented to ensure data quality and reliability.

## Useful resources

* [Development and Implementation of a Platform for Public Information on Air Quality, Sensor Measurements, and Citizen Science](https://www.mdpi.com/2073-4433/10/8/445). A scientific paper reflecting on the experiences of the Dutch Institute for Public Health and the Environment (RIVM) with the use of low-cost sensors, particularly NO2 and PM10/PM2.5-sensors, and related Citizen Science, over the last few years.
* [Seasonal Influence on the Performance of Low-Cost NO2 Sensor Calibrations](https://www.mdpi.com/1424-8220/21/23/7919/htm). Scientific paper exploring the added value of calibration models based on (multiple) linear regression including cross terms on the performance of an electrochemical NO2 sensor, (B43F manufactured by Alphasense).

## You might also be interested in….

* [What are the main aspects you need to consider when managing citizen collected data?](broken-reference)
* [Why is it important to document context and how does it help better understand collected data?](broken-reference)
