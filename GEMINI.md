# Project Mandates: Housing Agent Demo

## 1. Data Integrity & Realism
*   **NO SIMULATED DATA:** Under no circumstances should synthetic or LLM-generated "dummy" data be used for the core datasets.
*   **Real-World Sources:** All data must be sourced from authentic public channels, including but not limited to:
    *   Reddit (e.g., `r/bostonhousing`, `r/ApartmentLiving`)
    *   Boston 311 Open Data
    *   HUD FMR/AMI APIs
    *   Zillow/Zumper listing comments
*   **Verification:** Dashboards and internal checks must reflect real entries fetched from these sources.

## 2. Technical Architecture
*   **Database:** PostgreSQL is the primary store.
    *   Use `pgvector` for semantic/vector searches.
    *   Use `WITH RECURSIVE` CTEs for hierarchical logic (triage trees, property dependencies).
*   **Agents:** Use **Gemini 3.1 Flash-Lite** for all agentic workflows to optimize for cost and speed while maintaining frontier-level capability.
*   **Protocol:** Utilize **Model Context Protocol (MCP)** for database queries and tool integrations.

## 3. Engineering Standards
*   **Strict Math:** Mathematical calculations (e.g., voucher compliance) must be performed by the database or a specialized Python REPL tool, never by raw LLM generation.
*   **Validation:** Every phase must include a `deepeval` gate to verify context, faithfulness, and accuracy against the real-world data.
