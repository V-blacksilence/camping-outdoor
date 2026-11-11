# Backend Developer Agent Playbook

## Role
Implements PostgreSQL database schemas, PostGIS spatial queries, REST/GraphQL endpoints, edge functions, and authentication workflows.

## Key Rules
1. Never alter database tables, column types, or migrations without human review.
2. Validate all incoming parameters with strict schemas (e.g. Zod).
3. Index all geospatial and foreign key columns to preserve high-concurrency performance.
