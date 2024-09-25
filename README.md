# 2024-fall-architectural-katas
A (hopefully) pragmatic approach to the Architectural Kata 2024

## Team
![Team](/ArchitectureCharacteristics/images/team.png)

- Stefano Tassone, [Linkedin](https://ch.linkedin.com/in/stefano-tassone)
- James Dermelj, [Linkedin](https://ch.linkedin.com/in/james-dermelj-493446119)
- Tobias Heller, [Linkedin](https://ch.linkedin.com/in/tobias-heller)

## Domain
TODO

## Event Storming
TODO

## Architecture Characteristics
Starting from the business requirements(Add link) and the [Event Storming](/EventStorming) we determined the [architecture characteristics](/ArchitectureCharacteristics/Characteristics.md).

The selection of characteristics provides the basis for the selection of an Architectural Type. We selected the following seven characteristics and focused our attention on the three most important characteristics.

![ArchitecturalCharacteristics](/ArchitectureCharacteristics/images/architecture-characteristics.png)

## Architectural Type
According to the [driving characteristics](/ArchitectureCharacteristics/Characteristics.md):
- interoperability
- feasibility
- testability

a service-based architecture [ADR-002](/ADR/ADR-002-architecture-style.md) was selected to leverage the optimal balance between feasibility and testability.

![Architectural Type](TODO)

## Architecture
By utilizing the [C4](https://c4model.com/) approach to visualize software architecture, we can effectively illustrate the dependencies between various components of our application while emphasizing hierarchical relationships. Our primary focus will be on the C1 and C2 views to provide an initial overview, before delving into the C3 view to examine the core components in greater detail.

###  Context diagram (C1)
The context view allows us to get a first grasp of the actors and the external components interacting with the ClearView system.

![Context diagram  (C1)](/C4/images/C1-Context.png)

The full Context diagram with the description of the Actors can be found [here](/C4/C1-context.md).

## Known Limitations
