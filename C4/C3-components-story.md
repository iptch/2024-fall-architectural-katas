# Components Diagram (C3) - Story

In the C4 model, the C3 diagrams highlight how the components within a container operate and interact.

For the Story Processing container, we want to show how we incorporate the characteristics of *automation* and *data anonymization*.

### Story Processing Overview

- **AI-Driven Automation**  
  The story processing pipeline leverages AI-based adapters to automate the rating and anonymization of job candidate resumes, as described in [ADR-006 AI Models run on separate containers](/ADR/ADR-006-ai-models-run-on-separate-containers.md). The process ensures consistency and efficiency in the handling of candidate data.

![Components Diagram (C3) - Story Processing](/C4/images/C3-components-story.png)

TODO: Asynchronous to adapter

## Data flow

### Sending a Resume for Story

1. The **Candidate** container submits a resume through the system interface.
2. The resume is sent to the **Story API**.
3. The **Story API** forwards it to the **Resume Service**.
4. The **Resume Service** forwards it to the **AI Anonymize Adapter**.
5. The **AI Anonymize Adapter** sends it to the **AI Anonymize System**.

### Storing the Story

1. Once the **AI Anonymize System** anonymizes the resume, it returns the processed story to the **AI Anonymize Adapter**, which sends the story back to the **Resume Service**.
2. The **Resume Service** (or **Story Processor**) stores the anonymized story directly in the **Matching Database** (or **Central Matching Database**) for further use in the matching process.
3. In case of processing failures, the resume is queued for retry, ensuring no data is lost during the process.


