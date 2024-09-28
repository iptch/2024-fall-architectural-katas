# 2024-fall-architectural-katas
A (hopefully) pragmatic approach to the O'Reilly Autumn Architectural Kata 2024

## Team
![Team](/ArchitectureCharacteristics/images/team.png)

- Stefano Tassone, [Linkedin](https://ch.linkedin.com/in/stefano-tassone)
- James Dermelj, [Linkedin](https://ch.linkedin.com/in/james-dermelj-493446119)
- Tobias Heller, [Linkedin](https://ch.linkedin.com/in/tobias-heller)

## Introduction
TODO -> What is Diversity Equity Counsil about, what is the goal of ClearView?

## Requirements
TODO

## Event Storming
TODO

## Architecture Characteristics
Starting from the business requirements(Add link) and the [Event Storming](/EventStorming) we determined the [architecture characteristics](/ArchitectureCharacteristics/Characteristics.md).

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
