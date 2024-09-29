# ADR-011: Matching based on AI or deterministic methods

## Date:
2024-09-26

## Status:
Accepted

## Context:
We reviewed several matching processes for candidates and roles. Some of these processes utilized vector-based features that are highly effective for AI but unreadable by humans. The decision was made to use human-readable features to maintain better control over the AI and improve interpretability.
![Matching Process](./images/ADR-011-matching-process.png)

The options we considered were:
- **A) Extracting features from both the role and the story, then performing a static match.
- **B) Using features extracted by AI but made static and understandable by humans.
- **C) Letting AI directly match resumes and roles, but this was discarded due to bias concerns.
- **D) Allowing AI to assess whether a story and role should match.
- **E) Matching stories and roles using human-readable features and calculating a match score.
- **F) Each role has its own features, and candidates are evaluated based on these, but this approach was too resource-intensive.

## Decision:
We decided to proceed with Option B, where human-readable features extracted by AI are made static. This provides an ideal balance between transparency, testability, and resource efficiency.

While we considered Option F, which involves role-specific features and a static evaluation of all candidates, we ultimately ruled it out because it would be too computationally expensive. Although this option would have provided precise and detailed evaluations, the resource demands made it impractical for our current setup.

By selecting Option B, we maintain transparency and control without sacrificing performance or requiring excessive computational power.

## Consequences:
- **Transparency**: The human-readable features ensure transparency, making it easier to validate and interpret the AI’s decision-making process.
- **Control**: This approach allows for better human oversight over the AI’s matching process.
- **Resource Efficiency**: It is less computationally intensive than purely AI-driven or complex vector-based methods, making it more suitable for our needs.

