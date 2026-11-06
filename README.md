# collective-passdown-demo
Interactive demo of Collective Passdown, a configuration-driven semiconductor manufacturing operations platform integrating equipment status, maintenance, work orders, and operational priorities.



# Collective Passdown
### A Configurable Semiconductor Manufacturing Operations Platform

**Interactive demonstration of a manufacturing operations application independently developed, deployed, and maintained since 2019.**

Collective Passdown was created to solve a problem in semiconductor manufacturing: critical operational information was scattered across disconnected systems, making it difficult for technicians to efficiently monitor equipment and communicate important information between shifts.

What began as a solution for one manufacturing area evolved into a configurable application supporting operations across multiple manufacturing facilities.

This repository contains a **standalone demonstration using simulated manufacturing data**, designed to showcase the application's interface, functionality, and underlying engineering concepts without requiring access to production systems.

---

###  Live Interactive Demo
[Launch Collective Passdown](https://aralzina.github.io/collective-passdown-demo/)

Explore the application using simulated semiconductor manufacturing data.
No login or installation required.


## The Problem

Before Collective Passdown, technicians relied heavily on verbal communication, work orders, and multiple independent reporting systems to understand equipment conditions and ongoing operational issues.

Relevant information was distributed across systems containing:

- Equipment status and availability
- Maintenance work orders
- Statistical Process Control (SPC) data
- Equipment alarms
- Automated monitoring information
- Manufacturing Execution System (MES) events
- Equipment history and operational comments

Retrieving the information needed to understand equipment conditions could require several minutes or longer.

There was also no convenient, centralized mechanism for preserving operational context between shifts.

The objective was to create a unified interface that reduced repetitive information gathering while improving the accessibility and continuity of manufacturing information.

---

## The Solution

Collective Passdown consolidates manufacturing information into a configurable, equipment-focused application.

Users can organize equipment into customized views, retrieve relevant operational information, and maintain settings appropriate to their manufacturing responsibilities.

Rather than requiring a separate application for every manufacturing area, the system uses a configuration-driven architecture that supports different equipment groups and operational requirements.

### Core Capabilities

**Configurable Equipment Views**
- Dynamically generated equipment interfaces
- User-defined equipment configurations
- Persistent preferences and settings
- Support for different manufacturing areas

**Operational Data Integration**
- Equipment status and availability
- Maintenance work orders
- Equipment alarms
- Preventive maintenance information
- Operational comments
- Manufacturing priorities and exceptions

**Asynchronous Data Processing**
- REST API integration in the production application
- Concurrent request management
- Client-side data transformation
- On-demand information refresh

**Operational Priorities**
- Equipment downtime information
- High-priority work orders
- Tracer-related conditions
- Consolidated presentation of operational exceptions

---

## Technical Architecture

The production application uses a combination of SQL, enterprise reporting datasets, REST APIs, and client-side JavaScript.

```text
       Manufacturing Data Sources
                  |
                  v
       SQL Queries and Data Logic
                  |
                  v
       Shared Reporting Datasets
                  |
                  v
           REST / OData API
                  |
                  v
       JavaScript Data Retrieval
                  |
                  v
       Client-Side Transformation
                  |
                  v
      Configuration-Driven Interface
                  |
                  v
         Manufacturing Personnel
```

### Technologies

| Technology | Application |
|---|---|
| JavaScript | Application logic, data processing, and dynamic rendering |
| HTML5 | Application structure |
| CSS3 | Responsive interface and visual presentation |
| SQL / IBM Db2 | Data retrieval, filtering, aggregation, and transformation |
| REST / OData | Communication with enterprise reporting datasets |
| XMLHttpRequest | Asynchronous data retrieval |
| JSON | Data exchange and configuration |
| Browser Local Storage | Persistent user preferences and configuration |
| Power BI Report Server environment | Production application hosting and reporting integration |

### Engineering Design Decisions

#### Configuration-Driven Data Retrieval

One of the application's architectural improvements was eliminating hardcoded equipment filters.

Earlier implementations required manually modifying SQL queries whenever another manufacturing area needed different equipment.

The application was redesigned to derive equipment filtering parameters from the user's configuration.

This allowed the data retrieval layer to adapt to different equipment groups without requiring manual SQL modifications for each deployment.

#### Database and Client-Side Processing

Data processing is distributed between SQL and JavaScript according to application requirements.

SQL is used to retrieve relevant records efficiently, perform database-side transformations, and reduce unnecessary data transfer.

JavaScript performs additional transformations when the application needs multiple representations of the same retrieved dataset.

This approach helps avoid redundant requests while preserving flexibility in how information is presented.

#### Asynchronous Request Management

The application coordinates multiple reporting dataset requests while controlling concurrency.

This helps manage requests to shared reporting infrastructure and allows different parts of the interface to retrieve information asynchronously.

#### Operational Data Modeling

Some reporting requirements involve combining equipment state history, work orders, comments, and operational priorities.

These datasets require specialized SQL logic to preserve relationships between equipment, events, and maintenance activities.

The resulting data is structured for direct consumption by the application.

---

## Demonstrated Adoption

Collective Passdown has been deployed across manufacturing locations in the United States and internationally.

Internal reporting statistics from one manufacturing campus demonstrate the following usage:

| Metric | Recorded Value |
|---|---:|
| Unique equipment-status dataset users, 30 days | **387** |
| Unique equipment-status dataset users, 7 days | **333** |
| Equipment-status dataset opens, 30 days | **103,104** |
| Equipment-status dataset opens, 7 days | **23,827** |
| Equipment-status dataset executions, cumulative | **47,467** |

**Important:** These figures represent reporting dataset usage at one manufacturing campus, not independently measured application sessions. They should not be interpreted as total usage across all deployed locations.

The application has been continuously developed and maintained since 2019.

### Operational Impact

Collective Passdown has helped:

- Centralize information previously distributed across multiple systems.
- Reduce the time required to locate relevant equipment information.
- Improve access to operational context between shifts.
- Reduce repetitive manual information gathering.
- Support configurable equipment views without maintaining separate applications.
- Make operational priorities more visible to manufacturing personnel.

These improvements are based on observed operational experience. Formal time-savings and financial ROI measurements have not been established.

---

## Individual Engineering Ownership

Collective Passdown was independently conceived, architected, developed, deployed, and maintained by a single developer while working as a semiconductor manufacturing technician.

Responsibilities include:

- Application architecture and design
- Frontend development
- SQL query development and optimization
- Reporting dataset integration
- REST API integration
- Data transformation and presentation
- Configuration management
- Deployment to additional manufacturing locations
- Troubleshooting and technical support
- Feature development and long-term maintenance

The application was developed incrementally in response to real manufacturing requirements and operational feedback.

AI-assisted development tools have been used for selected styling changes, newer features, and SQL syntax troubleshooting. Core application development, architecture, integration, deployment, and ongoing technical ownership remain the responsibility of the sole developer.

---

## Running the Demo

The demonstration is contained in a standalone HTML file.

1. Download or clone this repository.
2. Open `Passdown-Demo.html` in a modern desktop browser.
3. Explore the equipment interface, configuration options, and operational information.

No database connection, authentication, or enterprise reporting environment is required.

### Demonstration Environment

The demo replaces production data access with a simulated data service.

It includes:

- Synthetic manufacturing equipment and operational records
- Simulated dataset responses
- Local browser storage for demonstration state
- Simulated request behavior
- No required external network connections

Changes made within the demonstration do not affect production systems.

To restore the initial demonstration state, clear the demo's locally stored browser data.

---

## Production vs. Demonstration

This repository is intended to demonstrate the application's functionality and engineering concepts.

The production implementation operates within an enterprise manufacturing environment and integrates with internal reporting infrastructure.

The demonstration substitutes simulated data for production reporting sources.

**The demonstration should not be interpreted as a complete representation of the production infrastructure, data volumes, performance characteristics, or security environment.**

---

## Project Background

Collective Passdown began in 2019 as an attempt to eliminate a recurring operational frustration.

Manufacturing technicians needed information that already existed, but obtaining it required navigating multiple systems and relying on informal communication.

Instead of accepting that fragmentation as an unavoidable part of manufacturing operations, I began building a centralized solution.

Over time, the application evolved to support additional equipment types, manufacturing areas, reporting requirements, and facilities.

The project represents an ongoing effort to make complex manufacturing information more accessible, reduce unnecessary manual work, and improve the systems people depend on every day.

---

## Author

**Independent Developer and System Architect**

Semiconductor Manufacturing Technician specializing in manufacturing systems, SQL optimization, JavaScript application development, operational automation, and data integration.

*Collective Passdown is a professional engineering portfolio demonstration based on an application developed in a semiconductor manufacturing environment.*