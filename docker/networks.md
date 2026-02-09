# Docker Network Isolation

- RW SQL is on a private network
- Only worker + ingestion containers can access RW
- RO SQL is accessible to Power BI and DecisionLens
- DecisionLens has no route to RW SQL
