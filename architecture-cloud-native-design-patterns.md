# Cloud Native design patterns

## Cloud native definition

Architecture of applications to be easily deployed into cloud in a resilent and fault-tolerant manner. It's about how to create applications, not about where to run them.

Requirements:
- Zero downtime
- Short delivery cycle
- Multi-client (mobile, web, IoT, desktop, etc)
- Data intensive

General traits:
- Modular
- Redundant

Consequences:
- Distributed
- Constantly changing

Cloud native design embraces failure as normal, not exception.

Three components:
- apps
- backing services
  - stateful services (data or apps)
  - stateless services (apps)

## 12 Factor applications

I. Codebase
- One codebase tracked in revision control, many deploys
- One code repository per deployable
- One application, multiple environments
- Trunk based development, short-living branches

II. Dependencies
- Explicitly declare and isolate dependencies
- Bundle dependencies into deployables
- Avoid system-level dependencies (shared libraries, CLI commands, etc)

III. Config
- Store config in the environment
- Config can vary between environments, code can't
- Solution: environment variables or config server
- Configuration set per environment, not environment-specific properties

IV. Backing services
- Treat backing services as attached resources
- Change of attached backing service should be possible on configuration level (not code)

V. Build, release, run
- Strictly separate build and run stages
- You **build** artfact from code
- Artifact plus configuration is a **release**
- Release can be **run** against given environment 
- Separate these stages in CI/CD pipeline

VI. Processes
- Execute the app as one or more stateless processes
- No local persistency, only via backing services
- Avoid sticky sessions

VII. Port binding
- Export services via port binding
- Self-contained execution units, avoid deployment into servers
- Runtime server embedded into deployable

VIII. Concurrency
- Scale out via the process model
- Vertical vs horizontal scalability
- Rely on scheduler to manage processes 

IX. Disposability
- Maximize robustness with fast startup and graceful shutdown
- Cattle vs Pets
- Application should be robust against sudden death

X. Dev/prod parity
Keep development, staging, and production as similar as possible

XI. Logs
Treat logs as event streams

XII. Admin processes
Run admin/management tasks as one-off processes
