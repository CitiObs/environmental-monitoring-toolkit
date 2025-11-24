---
icon: head-side-gear
---

# How to generate Decision Ready Information based on Analysis Ready Data?

## Description

Low-cost sensor networks are now able to deliver rich local measurements of air pollution. In the context of the CitiObs toolkit we refer to these cleaned, validated and harmonised datasets as Analysis-Ready Data (ARD). ARD is not raw sensor output, but data that has passed quality‐control and is ready for further processing. The next step is to convert ARD into Decision-Ready Information (DRI): maps, indicators or information products that can reliably support action, awareness and policy.

To do this, the toolkit presents two key pathways. First, for neighbourhood and city-scale work, ARD can be integrated into high-resolution urban air‐quality models by means of data assimilation. Second, for regional to continental scale, ARD from citizen science networks are incorporated into a machine-learning framework known as S‑MESH, enabling PM₂.₅ mapping at ~1 km resolution across Europe. These two workflows make full use of citizen-observatory data and advance it into forms that support decision-making.

## Why is this relevant?

Communities and city governments increasingly want to understand not just whether pollution is high, but where, when and why. Traditional monitoring stations alone are too sparse to resolve city‐scale or neighbourhood‐scale variation. Citizen science networks fill this gap, but only when the data are made trustworthy and spatially complete. By starting from ARD and then applying either local-scale data assimilation or regional-scale machine learning, practitioners and citizen groups can obtain maps and indicators that are both locally meaningful and scientifically robust. These DRI products can inform strategic decisions, support citizen engagement, guide interventions (for example near busy roads or in vulnerable neighbourhoods), and enrich policy discussions with evidence grounded in community-based monitoring.

## Methodological summary
### Local-Scale Approach: Data Assimilation

The local-scale methodology, described in CitiObs Deliverable D2.3 ([Add URL]), relies on merging LCS ARD with output from a high-resolution urban air-quality model such as uEMEP or EPISODE. The model provides a physically consistent but sometimes overly smooth estimate of pollution across the city. ARD from LCS networks captures real conditions at specific points but may include local biases. Data assimilation merges these two information sources while taking into account their respective uncertainties. First, the model prediction and sensor ARD are compared, and the differences are quantified. A mathematical representation of how much each observation should influence its surroundings, the background error covariance, determines how these differences spread across the map. Areas near sensors are corrected more strongly, while influence decreases with distance. The final product is a new map (the “analysis”) that reflects both real-world observations and the physical behaviour of pollution. This produces neighbourhood-scale detail (50–200 m), enabling reliable identification of urban hotspots and local exposure patterns.

### Regional / Continental Approach: S-MESH Machine Learning
For larger regions, CitiObs uses [S-MESH](https://www.sciencedirect.com/science/article/pii/S0013935124022709), a machine-learning framework that integrates ARD from LCS networks with satellite aerosol information, meteorological data, land-use characteristics, chemical transport model forecasts (CAMS) and reference-grade monitoring. The system learns statistical relationships between these diverse inputs and observed PM₂.₅ concentrations. Two strategies for incorporating LCS information were tested. A method that treated LCS measurements as additional training targets led to lower accuracy. A more effective method transformed the LCS network into a smoothed spatial layer representing the local pollution structure and used this as an input feature. This helped the model recognise fine-scale urban patterns while still relying on high-quality reference monitors for calibration. The result is a set of daily PM₂.₅ maps at 1 km resolution across Central Europe, with significantly improved accuracy in areas where LCS networks are present. This approach is especially valuable for identifying large-scale pollution events and for comparing air-quality conditions across cities and regions.

## Useful resources
- [Journal article](https://www.sciencedirect.com/science/article/pii/S0013935124022709) describing the S-MESH framework (without LCS data)
- The CitiObs Deliverable D2.3 “ValAir and MapAir toolkit” describes the methodology from both approaches. Available from: URL
- A manuscript draft “Evaluating the Role of Low-Cost Sensors in ML-based European PM2.5 Monitoring” describes the S-MESH integration of low-cost sensor networks and is currently under review. Once published it will be available from: [Add URL]
- The [ValAir/FILTER framework](https://www.sciencedirect.com/science/article/pii/S030147972501076X) for ensuring LCS data quality, which forms the basis of ARD in CitiObs.

## You might also be interested in
- The page “I want to generate insights & results from our data & knowledge by analysing the data” in the Citizen Observatory toolkit. [Add link]
- “TAPIS: A Simple Web Tool for Analysing Citizen-Generated Data” – describes how citizen observatories can explore sensor networks. 
CitiObs [Add link]
- The broader “Using Low-Cost Sensors Toolkit” section of the CitiObs site, which covers sensor selection, deployment, data platforms and data-quality workflows. 
