# ADR 001: Use Strategy Pattern for Task Sorting

## Date
2026-04-17

## Context
The Task Management CLI needs to support multiple ways of sorting tasks (by name, by priority, by due date). Implementing this logic directly inside the `TaskManager` class would violate the Single Responsibility Principle and make the class difficult to maintain and test.

## Decision
We implemented the **Strategy Design Pattern**. 
- Created an interface `ISortStrategy`.
- Created concrete classes: `SortByName`, `SortByPriority`, `SortByDate`.
- `TaskManager` holds a reference to an `ISortStrategy` and delegates the sorting behavior to it.

## Consequences
**Positive:** - Adding a new sorting method (e.g., by creation date) requires zero changes to the `TaskManager`. We just add a new class (Open/Closed Principle).
- AI agents can easily generate new sorting strategies because the boundary is strictly defined by the `ISortStrategy` interface.

**Negative:**
- Slightly increases the number of files and initial complexity of the project.
