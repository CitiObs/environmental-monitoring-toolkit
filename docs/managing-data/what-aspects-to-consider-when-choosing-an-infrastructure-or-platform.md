# What aspects to consider when choosing an infrastructure or platform??

## Description

A sensor data platform serves as a comprehensive framework tailored to gather, analyze, store, manage, and leverage data emanating from deployed sensing devices across diverse settings. Primarily utilized in environmental monitoring, it is typically associated with an established sensing apparatus. Selecting appropriate hardware involves key considerations. Essential components encompass data ingestion from distributed sensor networks capturing physical parameters, mechanisms for data processing, storage solutions for efficient organization and archival, visualization tools for effective data representation, and security protocols ensuring data integrity and privacy protection. Moreover, additional functionalities may encompass integration with external sources for contextual enhancement and scalability to accommodate expanding data volumes. This segment describes the primary factors to contemplate when opting for a sensor data platform.

## Why is this relevant?

Sensor data platforms allow collecting, processing and sharing data from distributed networks of sensing devices. However, there are many factors to consider when choosing what data platform to use (sometimes, this decision will be made for us by choosing a device). These factors can be both technical and non-technical. In this section we highlight some key aspects to consider, as the proliferation of multiple platforms in recent years shows both the diversity in approaches, but also the difficulty to choose the right platform among this diversity.

## How can this be done?

Below, we list a series of factors to consider when choosing a platform, classified by data policy and principles, and technical features.

* **Data policy and principles**:
  * **FAIR Data Principles**: FAIR (Findable, Accessible, Interoperable, and Reusable) data principles ensure that sensor data is managed in a manner that maximizes its usability and impact. A platform supporting FAIR Data principles will make use of metadata standards and adopt standardized data formats and protocols. This will enable integration with other datasets and analysis tools. Check that the platform defines clearly data sources, collection methods, and processing steps.
  * **Security and privacy**: make sure that the platforms have means to prevent unauthorized access, data breaches, and privacy violations. This involves checking for encryption, access control mechanisms, authentication, and auditing features to safeguard data integrity and confidentiality throughout the data lifecycle if needed.
  * **Regulatory compliance**: check for compliance with relevant regulations and standards governing data privacy, security, and environmental monitoring. This includes adhering to laws such as GDPR (General Data Protection Regulation) and ensuring data collection and storage practices align with industry-specific regulations.
  * **Data governance, ownership**: check data ownership, access rights, and responsibilities. This involves having clear answers to questions about who owns the data collected by devices, who has permission to access it, and how it can be used and shared. Typically, this will be defined by the data and software licenses.
  * **Sustainability and long-term viability**: review that the platform has a defined lifetime, or it has a plan for deprecation. Projects with low update rate (or none at all) are a red flag.
  * **CARE data principles**: CARE (Collective Benefit, Authority to Control, Responsibility, and Ethics) data principles prioritize that data collection and usage works towards collective benefits, respect individual rights, and uphold ethical standards. Platforms supporting CARE principles follow the above recommendations in one way or another and prioritize providing individuals with the authority to control their data, implementing measures to ensure data responsibility, promote ethical data practices and mitigate risks associated with data misuse or harm.
* **Technical features**:
  * **Performance and scalability:** check (or ask) if there are performance benchmarks for the data platform in question and, if needed, if the scale of your project is suited for the platform itself (i.e. if you are planning to use a large number of devices, make sure that it will not collapse the sensor platform). Consult with the platform providers or designers what **safeguards are in place to guarantee data robustness** and check that data will be safely stored, no matter what, either on the platform or locally on the sensing device if that fails.
  * **Traceability**: check if your sensor data will be traceable with metadata such as data source, acquisition timestamp, and processing history. This is key to trace the origins of sensor data and track any transformations or modifications it undergoes. This will allow you to verify the accuracy, reliability, and integrity of sensor data. Additionally, traceability facilitates compliance with regulatory requirements and quality assurance standards, providing assurance regarding the authenticity and trustworthiness of sensor data for various applications and use cases.
  * **Data quality assurance**: a nice to have feature, is the presence of data quality checks, implemented with data cleaning processes, or error detection and correction mechanisms.
  * **Contextualization**: check if there is the possibility to enhance data from sensors with contextual information. This is a nice to have feature, improving relevance and usability by providing insights into the conditions under which measurements were made. Contextual factors such as location, environmental conditions, sensor configuration, and operational context help interpret sensor readings and understand their significance. This will also support data quality assessment and validation by enabling anomaly detection, error correction based on contextual discrepancies and facilitate data fusion if your use case requires it.

## Useful resources

* [European Citizen Science Platform](https://www.ecsa.ngo/working-groups/european-citizen-science-platform/). This working group aims to be the central place of exchange for those interested in sustaining the [EU-Citizen.Science platform](https://eu-citizen.science/), building it further and expanding it (e.g. adopting/making use of the platform source code, freely available, to set up a national/regional platform).
* [ECSA WG on Projects, data, tools and technology](https://www.ecsa.ngo/working-groups/projects-data-tools-and-technology/). This working group aims to formalize a common understanding of interests in the Citizen Science data space, analyzing problems that Citizen Science projects face regarding data (e.g. interoperability, reliability, privacy, intellectual property rights).

## You might also be interested in….

* [What are the main aspects you need to consider when managing citizen collected data?](broken-reference)
* [What is data quality? How can we increase data quality in citizen gathered data?](broken-reference)
* [Why is it important to document context and how does it help better understand collected data?](broken-reference)
