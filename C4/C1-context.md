# Context Diagram (C1)

The context diagram offers an overview of the software system, including the users interacting with it and the external systems connected to the application.

![Context Diagram](/C4/images/C1-Context.png)

The survey system was designated as an external system in [ADR-xx](TODO). Similarly, the mail server, as defined in [ADR-xx](TODO), is also considered an external system for this application.

## Persons
The persons were derived from the Actors discovered in the [EventStorming](/EventStorming).

| **Person**         | **Description**                                         |
|--------------------|---------------------------------------------------------|
| Job Candidate      | A job candidate who uses the platform to find a matching position |
| Hiring Manager     | A hiring manager who uploads job positions, views matches, and unlocks resumes.  |
| Employer           | Provides employer and HR Integration information |
| Administrator      | Administers users and employers. Has access to reports and analytics. |


## Software Systems
- **ClearView**: The system under development.
- **HR System**: Various HR platforms, such as *SAP SuccessFactors*, *Workday*, and others.
- **Mail Server**: An external mail server used to send system notifications and reports.
- **Survey System**: An external service, such as SurveyMonkey, used for creating and managing surveys.
