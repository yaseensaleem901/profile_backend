# Day 02 — Design the relationships

[Previous day](day-01.md) · [Plan](../learning-plan.md) · [Next day](day-03.md)

**Goal:** Draw the data before creating tables.

- [ ] Learn: a table holds rows; a primary key identifies a row; a foreign key links rows; a unique constraint blocks duplicates; a join table models many-to-many relationships.
- [ ] Sketch Account → Profile → Projects; shared Services ↔ Profiles through Offerings; Review → author/target; Collection ↔ Project through Items; Blog → author. Keep industry distinct from category.
- [ ] Sketch one `Web Development` service linked to two offerings: Yaseen at USD 10/hour and Abdullah at USD 15/hour. Predict which record changes when Abdullah updates his rate. Discuss deletion and publication behavior; record unanswered choices in `USER_STORIES.MD`.

**Done when:** We can explain the diagram and agree the first table to migrate. No schema change today.
