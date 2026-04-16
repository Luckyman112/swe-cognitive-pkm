# Experiment Log: AI-Native Pure Function Generation

## 1. Context
Following the principles of "Functional Core, Imperative Shell", I extracted the date calculation logic from the `RecurringTask` OOP class into a standalone Pure Function. 

## 2. Prompt Provided to AI
"Act as a Senior Software Engineer. I need you to implement a feature for my Python CLI Task Manager based on these BDD requirements: [Link to feature_recurring_date_calc.md]. 
Also, follow this logic flow: [Link to flow_recurring_date_calc.md]. 
Strict Constraint: Write the logic for this feature as a Pure Function in Python using the `datetime` module. It must have no side effects (stateless) and return a predictable output."

## 3. AI Output
The AI successfully generated the following pure function:

```python
from datetime import datetime, timedelta

def calculate_next_run_date(current_date: datetime, interval_days: int) -> datetime:
    if interval_days <= 0:
        raise ValueError("Interval must be strictly positive")
    return current_date + timedelta(days=interval_days)
