# Components Diagram (C3) - Matching System

In this C3 diagram, we illustrate how different components within the matching system interact to save and rate stories and roles, and how the system generates matches between them.

## Matching System Overview

The **Matching System** manages the processes of saving stories and roles, rating them using AI, and matching stories to roles.

TODO: Add actors -> CRUD on matching directly
TODO: Move db outside,  direct access through db
TODO: Maybe rename story and role -> Rating Service rename to Scoring Service
TODO: Scoring not AI, Feature extraction AI -> ADR-011
TODO: MAybe seperate Feature extraction

![Components Diagram (C3) - Story Processing](/C4/images/C3-components-matching.png)

### Story Saving

1. The **Story Container** sends the story data to the **Matching API**.
2. The **Matching API** forwards the story to the **Story Component**.
3. The **Story Component** stores the story in the **Database**.

### Role Saving

1. The **Employer Container** sends role data to the **Matching API**.
2. The **Matching API** forwards the role to the **Role Component**.
3. The **Role Component** stores the role in the **Database**.

### Story Rating

TODO: Add scheduling (clock)

1. The **Story Container** checks for stories without a rating.
2. If unrated stories are found, they are sent to the **AI Rating Adapter**.
3. The **AI Rating Adapter** sends the stories to the **AI Rating System**.
4. The **AI Rating System** returns the ratings to the **AI Rating Adapter**.
5. The **AI Rating Adapter** passes the ratings back to the **Story Container**.
6. The **Story Container** writes the ratings to the **Database**.

### Role Rating

1. The **Role Container** checks for roles without a rating.
2. If unrated roles are found, they are sent to the **AI Rating Adapter**.
3. The **AI Rating Adapter** sends the roles to the **AI Rating System**.
4. The **AI Rating System** returns the ratings to the **AI Rating Adapter**.
5. The **AI Rating Adapter** passes the ratings back to the **Role Container**.
6. The **Role Container** writes the ratings to the **Database**.

### Create Match
TODO: Add scheduling (clock)

1. The **Match Engine** periodically checks for new stories and roles.
2. If new or unmatched stories and roles are found, the **Match Engine** compares the unrated or unmatched stories with open roles.
3. If a match is found, the **Match Engine** stores the match in the **Database**.
4. The **Match Engine** notifies the **Matches Publisher**.
5. The **Matches Publisher** sends a notification to the **Match Topic Queue**.
