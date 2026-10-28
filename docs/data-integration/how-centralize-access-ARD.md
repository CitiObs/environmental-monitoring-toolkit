---
icon: cloud-check
---

# How to centralize access to Analysis Ready Data?

## Overview

Environmental observations are often stored on separate platforms, making it difficult to find and use data from different monitoring initiatives together.

VirtualAir provides a common access point for participating observatories that use compatible SensorThings API services. Observatory operators register their service, while data users can discover and request observations through a shared interface.

This page explains how VirtualAir connects these services, how to access the available data and how to register an observatory.

## Platform Components

VirtualAir provides a unified way to centralize and access Analysis Ready Data (ARD) from distributed air quality observatories. The platform supports OGC SensorThings API (STA) compatible observatories

It uses a two-tier architecture that separates observatory registration from data access, enabling integration of STA-based sensor networks while ensuring full interoperability through standardized APIs.

Observations are not stored in VirtualAir. They remain in each source observatory and are fetched live on every request. Only the registry — service addresses and metadata — is a database, and the observatory list is cached for about 10 minutes.

### **1. VirtualAirApi**

Central registry service for **SensorThings observatory metadata**.

### **2. VirtualAirDataApi**

Standardized data access layer implementing **OGC SensorThings API v1.1**.

### **3. Web Interface**

User-friendly portal for registering and managing **STA-compatible observatories**.

***

## What This Architecture Enables

* **Register observatories once** in a central catalog
* **Expose data through a unified, interoperable STA endpoint**
* Provide **Analysis Ready Data** with automatic aggregation and processing
* Enable **cross-network data discovery** across multiple SensorThings observatories

## Why is this relevant?

### 1. Interoperability Across Sensor Networks

VirtualAir reduces fragmentation by:

* Implementing the **OGC SensorThings API** standard
* Providing a **neutral, harmonized data model**
* Supporting **OData-style queries** (`$filter`, `$expand`, `$top`, `$skip`)

***

### 2. Aggregation and quality

VirtualAir forwards raw observations unchanged by default. On top of that:

* **Source quality fields are passed through** — where the underlying platform provides them (e.g. `quality_level`, screening flags, uncertainty), they are carried on each observation unchanged.
* **Optional hourly aggregation** on request via **MultiDatastreams**: mean, min, max and standard deviation.
* A **completeness count** (number of observations per hour) is returned with each aggregate.

> [!NOTE]
> VirtualAir provides a custom `/v1.1/MultiDatastreams` endpoint for hourly aggregation. VirtualAir computes these aggregates from source Datastream and Observations. Upstream platforms do not need to support MultiDatastreams. This functionality does not imply full support for the standard MultiDatastream extension

***



### 3. Simplified Data Discovery

Users can:

* Query a **single endpoint** for all observatories
* Explore sensors, parameters, and locations
* Access **real-time and historical** observations

***

### 4. Minimal Integration Effort

* Observatory operators **register once**
* Data consumers integrate **once**
* No need to maintain multiple observatory connections

***

### 5. Standards Compliance

VirtualAir supports:

* **OGC SensorThings API v1.1** (standard STA; STAplus endpoints are also supported but not required)
* **ISO 8601** time formats
* **GeoJSON**
* **OGC O\&M** (Observation & Measurements)

***

## System Architecture

* Observatory owners register their SensorThings API endpoint using the VirtualAir Web Interface or by calling the VirtualAirApi directly.
* The VirtualAirApi records the endpoint and stores its metadata (base URL, version, extensions, unique code) in the PostgreSQL registry database.
* Data consumers query the VirtualAirDataApi, a unified STA-compatible gateway.
* The Data API:
  * Retrieves metadata from the registry
  * Connects to the registered SensorThings observatories
  * Fetches observations
  * Optionally aggregates observations by hour when requested (via MultiDatastreams)
* The merged response is returned to the consumer as a standardized SensorThings API v1.1 JSON response.

## How to Use VirtualAir

### For Observatory Operators

#### **Option 1: Web Interface (recommended)**

Visit: https://web-virtualair.nilu.no/

Register your **SensorThings API v1.1 observatory** (STAplus is optional).

Provide:

* **Base URL** (SensorThings API)
* **API version**
* Optional extensions

After registration you will:

* Receive a **unique 4-character observatory code**
* Your observatory becomes accessible via VirtualAir

### Option 2: API Registration

**Endpoint:**\
`POST /observatory` → https://api-virtualairco.nilu.no/

**Authentication:**\
JWT

***

### Request Body

```json
{
  "baseurl": "https://your-observatory.example.com/v1.1",
  "version": "1.1",
  "extension": null,
  "formatnavlinks": null
}
```

### Response

```json
{
  "id": 1,
  "code": "ABCD",
  "baseurl": "https://your-observatory.example.com/v1.1"
}
```

## For Data Consumers

**Base URL:** https://api-virtualair.nilu.no/v1.1

Exposes a **SensorThings API v1.1** gateway across all registered observatories.

**A complete example**

```http
GET https://api-virtualair.nilu.no/v1.1/Observations?$top=2
```

Each observation contains: `@iot.id` (the namespaced ID, e.g. `KNJV_1`), `result` (the measured value; its unit is on the parent Datastream), `phenomenonTime` (when it was measured), `parameters` (source quality fields, passed through unchanged), and `properties.origin` (added by VirtualAir to show the source observatory). Follow `@iot.nextLink` for the next page.

### Example Queries

1. **List all sensor devices across all observatories**

```http
GET /Things
```

2. \*\*Observations from one Datastream

```http
GET /Datastreams('KNJV_5001')/Observations?$top=3
```

3. \*\*Filter by time

```http
GET /Datastreams(‘KNJV_5001’)/Observations?$filter=phenomenonTime ge 2024-01-01T00:00:00Z and phenomenonTime le 2024-01-31T23:59:59Z
```

4. \*\*Hourly aggregated ARD

```http
GET /MultiDatastreams?$filter=properties/aggregateUnit eq 'Hours' and properties/aggregateFor eq '/Datastreams(KNJV_5001)'&$expand=Observations
```

**Response includes:**

* Averages
* Min / Max values
* Standard deviation
* Observation counts

5. \*\*Expand related entities

```http
GET /Things?$expand=Locations,Datastreams
```

## Technical Implementation

### Technologies

* .NET 8
* PostgreSQL
* Dapper
* Docker
* Swagger / OpenAPI
* JWT Authentication

### Features

* Caching of the observatory list (10 minutes; observations are always fetched live)`
* Pagination
* OData query support
* Standardized error responses
* CORS support

***

## Useful Resources

### Standards

* [OGC SensorThings API](https://www.ogc.org/standards/sensorthings)
* ISO 8601
* EEA Units of Measurement

### VirtualAir

* Web Interface: [https://web-virtualair.nilu.no/](https://web-virtualair.nilu.no/)
* Data API: [https://api-virtualair.nilu.no/v1.1](https://api-virtualair.nilu.no/v1.1)
* Registration API: [https://api-virtualairco.nilu.no/](https://api-virtualairco.nilu.no/)

### Developer Resources

* GitHub Repositories:
  * [VirtualAir Web](https://github.com/CitiObs/virtualair-web)
  * [VirtualAir API](https://github.com/CitiObs/virtualair-api)
  * [VirtualAir Deployment](https://github.com/CitiObs/virtualair-deployment)

***

## Getting Started

1. Explore the API
2. Register your observatory
3. Query data
4. Integrate VirtualAir into your applications

## Support

* Consult API documentation
* Review the SensorThings API standard

***

## You might also be interested in

* [How to offer observations with a neutral data model and in an interoperable API?](../data-platforms/how-to-offer-obs-data-model-API.md)
