# Cloud Native design patterns

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
Treat backing services as attached resources

V. Build, release, run
Strictly separate build and run stages

VI. Processes
Execute the app as one or more stateless processes

VII. Port binding
Export services via port binding

VIII. Concurrency
Scale out via the process model

IX. Disposability
Maximize robustness with fast startup and graceful shutdown

X. Dev/prod parity
Keep development, staging, and production as similar as possible

XI. Logs
Treat logs as event streams

XII. Admin processes
Run admin/management tasks as one-off processes
