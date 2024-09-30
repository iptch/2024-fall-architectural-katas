# Diversity Cyber Council - ClearView | O'Reilly Architectural Kata (Autumn 2024)
A (hopefully) pragmatic approach to the O'Reilly Autumn Architectural Kata 2024

- [Team](#team)
- [Introduction](#introduction)
- [Event Storming](#event-storming)
- [Requirements](#requirements)
- [Architecture Characteristics](#architecture-characteristics)
- [Architecture style](#architecture-style)
- [Architecture](#architecture)
  - [Context diagram (C1)](#context-diagram-c1)
  - [Container diagram (C2)](#container-diagram-c2)
  - [Components diagram (C3)](#components-diagram-c3)
- [Known Limitations](#known-limitations)
- [Diagrams](#diagrams)


## Team
![Team](./ArchitectureCharacteristics/images/team.png)

- Stefano Tassone, [Linkedin](https://ch.linkedin.com/in/stefano-tassone)
- James Dermelj, [Linkedin](https://ch.linkedin.com/in/james-dermelj-493446119)
- Tobias Heller, [Linkedin](https://ch.linkedin.com/in/tobias-heller)

## Introduction
The [Diversity Cyber Council](https://www.diversitycybercouncil.com/) is a Non-Profit that helps under-represented demographics in the tech-industry with education, staffing and training opportunities.

The *ClearView* program aims to harness AI to facilitate matches between candidates and job positions using anonymized resumes.

**Key Objectives:**

- **Develop an AI-Powered Matching Platform:** Create an effective system that minimizes bias in the hiring process.
  - Our main contributions for this objective are:
    - Research, such as [interview with an AI-expert](/Requirements/Research/interview-ai-expert.md) and 
    [token estimation of a sample prompt](/Requirements/Research/token-estimation.md) leading to many
    [assumptions and requirements](/Requirements/requirements-and-assumptions.md), 
    - Matching algorithm considerations, such as [ADR-010](/ADR/ADR-010-create-features-from-story-not-resumes.md) and
    [ADR-011, deterministic matching](/ADR/ADR-011-deterministic-matching.md), 
    and the corresponding [visualization](/C4/C3-components-matching.md)
    - Other architectural considerations, such as [ADR-006](/ADR/ADR-006-ai-models-run-on-separate-containers.md),
      [ADR-007](/ADR/ADR-007-use-of-external-llms.md)

- **Analyze Hiring Disparities:** Utilize metrics and surveys to uncover disparities between selected candidates and those who were not hired.
  - Our main contributions for this objective are design decisions such as:
    - [ADR-003](/ADR/ADR-003-batch-for-analytics.md)
    - [ADR-018](/ADR/ADR-018-location-of-survey-triggers.md)
    - [ADR-019](/ADR/ADR-019-data-transmission-for-analytics.md)
    - [ADR-020](/ADR/ADR-020-externalizing-survey-processes.md)
  
- **Seamless HR Integration:** Implement a streamlined integration with employers' HR systems to ensure a smooth interview experience.
  - Our main contributions for this objective are design decisions such as:
    - Asynchronous trigger: [ADR-016](/ADR/ADR-016-matches-published-as-events.md)
      - Fault-tolerant and scalable HR Integration Service: [ADR-023](/ADR/ADR-023-adapters-for-hr-systems.md) and its
      [visualization](/C4/C3-components-hr-integration.md)


## Event Storming
We used [Event Storming](./EventStorming/event_storming.md) to explore and map out various domains within our business processes. The session focused on capturing and documenting the flow of events, actors, and interactions between systems. This document summarizes our outcomes and serves as a guide to understanding our approach.

## Glossary

The [glossary](/Requirements/glossary.md) defines terms we use.

## Requirements

Based on the problem description, our [Event Storming](./EventStorming/event_storming.md), and research, we compiled a list of [functional
and non-functional requirements](/Requirements/requirements-and-assumptions.md) complemented by a set of assumptions.
The requirements and assumptions are numbered and are referenced in the following way:
- Ri (f. ex. [R2](/Requirements/requirements-and-assumptions.md)), for functional requirements 
- Qi (f.ex. [Q13](/Requirements/requirements-and-assumptions.md)), for non-functional requirements
- Ai (f. ex. [A22](/Requirements/requirements-and-assumptions.md)) , for assumptions

We typically link to the file, but due to markdown limitations, the specific entry can not be referenced in the link.

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

An interaction of the Containers and Components is documented in the Use Case: [Upload and Publish a Resume](/UseCases/use-case-upload-a-resume.md)

## Known Limitations
The current architecture has the following limitations:

- **Matching Algorithm Limitations**:  
  The matching algorithm utilizes a predefined set of human-readable features, as described in [ADR-011](/ADR/ADR-011-deterministic-matching.md). Defining these features comprehensively for all S.M.A.R.T stories and job positions can be challenging.

- **Delayed Matching Process**:  
  Matching is executed as a periodic background process rather than in real-time, as detailed in [ADR-008](/ADR/ADR-008-ui-reactivity.md).

- **External AI Service Rate Limiting**:  
  Since AI services run independently as external entities, as described in [ADR-007](/ADR/ADR-007-use-of-external-llms.md), appropriate rate limiting is necessary to control costs.

- **User Administration**:  
  User administration through the UI is not yet part of the current concept and is dependent on initial technology decisions, such as the presence of existing Identity Providers (IdPs) at Diversity Cyber Council. For more information, see [ADR-022](/ADR/ADR-022-initial-technology-decisions.md). The current approach is to use a local user account that has access to the Identity Provider's UI.

## Diagrams

The diagrams in this project were created using [https://www.drawio.com/](https://www.drawio.com/). They can be viewed and edited directly by importing or opening the corresponding .drawio files.

