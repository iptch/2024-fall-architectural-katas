# Architecture Characteristics
Architecture characteristics, often referred to as quality attributes (ilities) or non-functional requirements, define the properties of an architecture to meet the technical and business goals.

## Define needed characteristics
Starting from the business requirements the following important characteristics were deemed as relevant for the ClearView product:

| **Term**             | **Definition**                                                                                                                                   |
|----------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| **security**         | The ability of the system to restrict access to sensitive information or functionality                                                            |
| **interoperability** | The ability of the system to interface and interact with other systems to complete a business request                                              |
| **feasibility** | Taking into account timeframes, budgets, and developer skills when making architectural choices; tight timeframes and budgets make this a driving architectural characteristic |
| **fault tolerance**  | When fatal errors occur, other parts of the system continue to function                                                                           |
| **testability**      | The ease of and completeness of testing                                                                                                           |
| **adaptability**     | The ease in which a system can adapt to changes in environment and functionality                                                                  |
| **scalability**      | A function of system capacity and growth over time; as the number of users or requests increase in the system, responsiveness, performance, and error rates remain constant |
| **observability** | The ability of a system or a service to make available and stream metrics such as overall health, uptime, response times, performance, etc. |
| **extensibility**    | The ease in which a system can be extended with additional features and functionality                                                             |
| **configurability**  | The ability of the system to support multiple configurations, as well as support custom on-demand configurations and configuration updates         |
| **abstraction**      | The level at which parts of the system are isolated from other parts of the system (both internal and external system interactions)               |


## Choosing the driving characteristics

Key characteristics prioritized:

- **Security**: Essential, as the product’s USP is resume anonymization.
- **Interoperability**: Crucial for seamless integration with various HR systems.
- **Feasibility**: Cost-effective decisions minimize variance in basic functionality costs, offsetting the uncertainty of AI integration and maintenance.
- **Fault Tolerance**: Ensures product stability even if integrated HR systems experience downtime.
- **Testability**: Robust regression tests are needed for non-deterministic AI systems to ensure quality.
- **Adaptability**: Rapid iteration is necessary to keep up with evolving AI technologies and requirements.
- **Scalability**: A scalable system is required to handle the quadratic time complexity of the matching process.

Reduced priorities:

- **Extensibility**: Largely covered by adaptability.
- **Configurability**: Not a priority, as HR system integrations will be handled via new releases, not on-demand changes.
- **Abstraction**: Necessary at the code level, but not at the architectural level, for managing AI models and HR systems.

## Selecting the Top 3

- TODO
