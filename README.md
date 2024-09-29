# Diversity Cyber Council - ClearView | O'Reilly Architectural Kata (Autumn 2024)
A (hopefully) pragmatic approach to the O'Reilly Autumn Architectural Kata 2024

TODO -> Update

- [Team](#team)
- [Introduction](#introduction)
- [Requirements](#requirements)
- [Event Storming](#event-storming)
- [Architecture Characteristics](#architecture-characteristics)
- [Architecture style](#architecture-style)
- [Architecture](#architecture)
  - [Context diagram (C1)](#context-diagram-c1)
  - [Container diagram (C2)](#container-diagram-c2)
  - [Components diagram (C3)](#components-diagram-c3)
- [Usecases](#usecases)
- [Known Limitations](#known-limitations)


## Team
![Team](/ArchitectureCharacteristics/images/team.png)

- Stefano Tassone, [Linkedin](https://ch.linkedin.com/in/stefano-tassone)
- James Dermelj, [Linkedin](https://ch.linkedin.com/in/james-dermelj-493446119)
- Tobias Heller, [Linkedin](https://ch.linkedin.com/in/tobias-heller)

## Introduction
The [Diversity Cyber Council](https://www.diversitycybercouncil.com/) is a Non-Profit that helps under-represented demographics in the tech-industry with education, staffing and training opportunities.

The *ClearView* program aims to harness AI to facilitate matches between candidates and job positions using anonymized resumes.

**Key Objectives:**

- **Develop an AI-Powered Matching Platform:** Create an effective system that minimizes bias in the hiring process.
  
- **Analyze Hiring Disparities:** Utilize metrics and surveys to uncover disparities between selected candidates and those who were not hired.
  
- **Seamless HR Integration:** Implement a streamlined integration with employers' HR systems to ensure a smooth interview experience.


## Requirements
TODO

## [Event Storming](./EventStorming/event_storming.md)
We used Event Storming to explore and map out various domains within our business processes. The session focused on capturing and documenting the flow of events, actors, and interactions between systems. This document summarizes our outcomes and serves as a guide to understanding our approach.


## Architecture Characteristics
Starting from the business requirements(Add link) and the [Event Storming](./EventStorming/event_storming.md) we determined the [architecture characteristics](/ArchitectureCharacteristics/Characteristics.md).

The selection of characteristics provides the basis for the selection of an Architectural Type. We selected the following seven characteristics and focused our attention on the three most important characteristics.

![ArchitecturalCharacteristics](/ArchitectureCharacteristics/images/architecture-characteristics.png)

## Architecture style
According to the TOP 3 [driving characteristics](/ArchitectureCharacteristics/Characteristics.md):
- interoperability
- feasibility
- testability

a service-based architecture [ADR-002](/ADR/ADR-002-architecture-style.md) with event-streaming capabilities where needed, was selected to leverage the optimal balance between feasibility and testability.

![Architecture style](/ADR/images/ADR-002-architecture-style.png)

## Architecture
By utilizing the [C4](https://c4model.com/) approach to visualize software architecture, we can effectively illustrate the dependencies between various components of our application while emphasizing hierarchical relationships. Our primary focus will be on the C1 and C2 views to provide an initial overview, before delving into the C3 view to examine the core components in greater detail.

###  Context diagram (C1)
The context view allows us to get a first grasp of the actors and the external components interacting with the ClearView system.

![Context diagram  (C1)](/C4/images/C1-Context.png)

The full Context diagram with the description of the Actors and Systems can be found [here](/C4/C1-context.md).


### Container diagram (C2)
The Container diagram shows the high-level shape of the software architecture and how responsibilities are distributed across it. 
It also shows how the containers communicate with each another. 

![Container diagram (C2)](/C4/images/C2-Container.png)

The full Container diagram with the descriptions of the containers and  ADRs describing the decisions can be found [here](/C4/C2-container.md).


### Components diagram (C3)
To address the main challenges of this system, we created a components diagram:

- **[HR Integration Components](/C4/C3-components-hr-integration.md)**: This diagram illustrates how we integrate **Interoperability** and **Fault Tolerance** into our architecture.
- TODO -> Stefano AI -> testability

## Usecases
TODO (Sequence diagram)

## Known Limitations
