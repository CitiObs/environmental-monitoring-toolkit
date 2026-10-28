---
icon: calendar-check
---

# How to validate sensor data to create Analysis Ready Data?



## Description

Sensor measurements can contain errors and unusual readings. Before analysing the data, it is important to identify potential quality problems and understand whether corrections are appropriate.

The Framework for Improving Low-cost Technology Effectiveness and Reliability (FILTER) provides statistical methods to flag potential erroneous data and correct measurement values. It is designed to work across different sensing devices without requiring each device to be placed alongside a reference monitoring station. However, the version described here requires nearby reference stations or sensors so that measurements can be compared across a network.

FILTER helps prepare data for analysis, but processed data still need to be assessed against the requirements of your monitoring question. Keep the original measurements, quality flags and details of any corrections so that users can understand how the data were prepared.&#x20;

## Why is this relevant?

Harmonized, quality-controlled, and corrected datasets from various low-cost sensor networks are generally lacking. In order to increase the uptake of data from sensing devices, it is important that the user knows the quality of the data. Lack of  data standardization and data of unknow quality limits the use of citizen generated data for official environmental assessments, policymaking, and scientific research.&#x20;

FILTER is a tool comprising a set of statistical algorithms for quality flagging and value correction. The FILTER tool is available on MATLAB and integrated as an open-source R package. The R package includes the full FILTER methodology along with detailed use cases to support applications to both historical and near real-time datasets.

## Useful resources

Scientific paper describing the methodology: Hassani, A., Salamalikis, V., Schneider, P., Stebel, K., Castell, N. (2025).[ A scalable framework for harmonizing, standardization, and correcting crowd-sourced low-cost sensor PM2.5 data across Europe. Journal of Environmental Management](https://www.sciencedirect.com/science/article/pii/S030147972501076X), 380, 125100.

Validated Dataset for Europe: [https://doi.org/10.6084/m9.figshare.27195720.v1](https://doi.org/10.6084/m9.figshare.27195720.v1) &#x20;

## You might also be interested in

* [What is data quality? How can we increase data quality in citizen gathered data?](../managing-data/what-is-data-quality-how-can-we-increase-data-quality-in-citizen-gathered-data.md)
* [What are the main aspects you need to consider when managing citizen collected data?](../managing-data/what-are-the-main-aspects-you-need-to-consider-when-managing-citizen-collected-data.md)

