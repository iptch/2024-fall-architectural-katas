# Components Diagram (C3) - Job Candidate

In the C4 model, the C3 diagrams show how components within a container interact to manage different processes.

For the **Job Candidate Management** container, we want to outline how candidates submit their resumes, request AI-based tips, and manage their data.

### Job Candidate Overview

- **AI-Powered Resume Tips**  
  The resume submission process allows candidates to request feedback through the AI-based **Resume Tips Adapter**, which provides suggestions to improve their resume. Once the tips are returned, they are passed back to the **Resume Service** and stored in the job candidate's record.

![Components Diagram (C3) - Job Candidate](/C4/images/C3-components-job-candidate.png)

TODO: DB outside, Actor add?, get tips asyncronous

ADR-005, ADR-007

## Data Flow

### Requesting AI Resume Tips

1. The **Candidate** requests resume tips through the **Candidate API**.
2. The **Candidate API** forwards the request to the **Resume Service**.
3. The **Resume Service** invokes the **AI Resume Tips Adapter**.
4. The **AI Resume Tips Adapter** sends the resume data to the **AI Resume Tips System**.
5. The **AI Resume Tips System** generates the tips and sends them back to the **AI Resume Tips Adapter**.
6. The **AI Resume Tips Adapter** passes the tips back to the **Resume Service**.
7. The **Resume Service** stores the resume tips in the **Job Candidate Database** for future reference by the candidate.

### Submitting a Resume for Anonymization

1. The **Candidate** submits their resume through the **Candidate API**.
2. The **Candidate API** forwards the resume to the **Resume Service**.
3. The **Resume Service** sends the resume to the **Story Container**.
4. The **Story Container** handles the anonymization of the resume data.
TODO -> Dont store resume ADR-007
5. Once anonymized, the **Story Container** returns the anonymized resume to the **Resume Service**.
6. The **Resume Service** stores the anonymized resume in the **Job Candidate Database**.

### Managing Candidate Information

1. The **Candidate** can update or modify their information through the **Candidate API**.
2. The **Candidate API** communicates with the **Candidate Service**, which accesses and updates the **Job Candidate Database**.
3. The **Candidate Service** retrieves or stores the updated data in the database as needed.
