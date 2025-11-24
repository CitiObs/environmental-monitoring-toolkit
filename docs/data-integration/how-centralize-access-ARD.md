---
icon: cloud-check
---

# How to centralize access to Analysis Ready Data?

## Overview

VirtualAir provides a unified way to centralize and access Analysis Ready Data (ARD) from distributed air quality observatories. The platform supports OGC SensorThings API (STA) compatible observatories

It uses a two-tier architecture that separates observatory registration from data access, enabling integration of STA-based sensor networks while ensuring full interoperability through standardized APIs.


## Platform Components

### **1. VirtualAirApi**
Central registry service for **SensorThings observatory metadata**.

### **2. VirtualAirDataApi**
Standardized data access layer implementing **OGC SensorThings API v1.1**.

### **3. Web Interface**
User-friendly portal for registering and managing **STA-compatible observatories**.

---

## What This Architecture Enables

- **Register observatories once** in a central catalog  
- **Expose data through a unified, interoperable STA endpoint**  
- Provide **Analysis Ready Data** with automatic aggregation and processing  
- Enable **cross-network data discovery** across multiple SensorThings observatories

  
## Why is this relevant?

### 1. Interoperability Across Sensor Networks
VirtualAir reduces fragmentation by:
- Implementing the **OGC SensorThings API** standard  
- Providing a **neutral, harmonized data model**  
- Supporting **OData-style queries** (`$filter`, `$expand`, `$top`, `$skip`)  

---

### 2. Analysis Ready Data Built-In
VirtualAir delivers ARD features out of the box:
- Automated **hourly aggregations** (min, max, avg, stddev)  
- **Quality metrics** for each aggregation window  
- **Temporal aggregation** via MultiDatastreams  
- **Standardized units** (e.g., μg/m³)  

---

### 3. Simplified Data Discovery
Users can:
- Query a **single endpoint** for all observatories  
- Explore sensors, parameters, and locations  
- Access **real-time and historical** observations  

---

### 4. Minimal Integration Effort
- Observatory operators **register once**  
- Data consumers integrate **once**  
- No need to maintain multiple observatory connections  

---

### 5. Standards Compliance
VirtualAir supports:
- **STAPLUS**  
- **ISO 8601** time formats  
- **GeoJSON**  
- **OGC O&M** (Observation & Measurements)  

---

## System Architecture

- Observatory owners register their SensorThings API endpoint using the VirtualAir Web Interface or by calling the VirtualAirApi directly.
- The VirtualAirApi validates the endpoint and stores its metadata (base URL, version, extensions, unique code) in the PostgreSQL registry database.
- Data consumers query the VirtualAirDataApi, a unified STA-compatible gateway.
- The Data API:
  - Retrieves metadata from the registry
  - Connects to the registered SensorThings observatories
  - Fetches observations
  - Performs automatic aggregation (hourly, daily, etc.)
  - Produces Analysis Ready Data (ARD)
- The ARD is returned to the consumer as a standardized SensorThings API v1.1 JSON response.

## How to Use VirtualAir

### For Observatory Operators

#### **Option 1: Web Interface (recommended)**

Visit: https://web-virtualair.nilu.no/

Register your **STAPLUS-compatible SensorThings observatory**.

Provide:

- **Base URL** (SensorThings API)
- **API version**
- Optional extensions

After registration you will:

- Receive a **unique 4-character observatory code**
- Your observatory becomes accessible via VirtualAir


### Option 2: API Registration

**Endpoint:**  
`POST /observatory` → https://api-virtualairco.nilu.no/

**Authentication:**  
JWT

---

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

Implements the **full SensorThings API v1.1**.

### Example Queries

1. **Discover all observatories**
```http
GET /Things
```

2. **Observations from a Datastream
```http
GET /Things(1)/Datastreams(123)/Observations
```

3. **Filter by time
 ```http
GET /Datastreams(123)/Observations?$filter=phenomenonTime ge 2024-01-01T00:00:00Z and phenomenonTime le 2024-01-31T23:59:59Z
```
4. **Hourly aggregated ARD
 ```http
GET /MultiDatastreams?$filter=properties/aggregateUnit eq 'Hours' and properties/aggregateFor eq '/Datastreams(123)'&$expand=Observations
```

**Response includes:**

- Averages
- Min / Max values
- Standard deviation
- Observation counts
- Expand related entities

5. **Expand related entities
 ```http
GET /Things?$expand=Locations,Datastreams
```

## Technical Implementation

### Technologies
- .NET 8
- PostgreSQL
- Dapper
- Docker
- Swagger / OpenAPI
- JWT Authentication

### Features
- Caching
- Pagination
- OData query support
- Standardized error responses
- CORS support

---

## Useful Resources

### Standards
- [OGC SensorThings API](https://www.ogc.org/standards/sensorthings)
- ISO 8601
- EEA Units of Measurement

### VirtualAir
- Web Interface: [https://web-virtualair.nilu.no/](https://web-virtualair.nilu.no/)
- Data API: [https://api-virtualair.nilu.no/v1.1](https://api-virtualair.nilu.no/v1.1)
- Registration API: [https://api-virtualairco.nilu.no/](https://api-virtualairco.nilu.no/)

### Developer Resources
- GitHub Repositories:  
  - [VirtualAir Web](https://github.com/CitiObs/virtualair-web)  
  - [VirtualAir API](https://github.com/CitiObs/virtualair-api)  
  - [VirtualAir Deployment](https://github.com/CitiObs/virtualair-deployment)  

---

## Getting Started
1. Explore the API
2. Register your observatory
3. Query data
4. Integrate VirtualAir into your applications

## Support
- Consult API documentation
- Review the SensorThings API standard
---

## You might also be interested in

* [How to offer observations with a neutral data model and in an interoperable API?](../data-platforms/how-to-offer-obs-data-model-API.md)
