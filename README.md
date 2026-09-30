# home-infra

GitOps manifests for the home-server K3s cluster.

## Managed infrastructure

- `database` namespace
- Shared PostgreSQL 18.6
- Daily PostgreSQL backups to Cloudflare R2
- Argo CD Application for the database stack

## Secret policy

Secrets are **not stored in this repository**.

The following Kubernetes Secrets must already exist in the cluster:

- `database/postgres-admin`
- `database/postgres-backup-r2`
- `iwtc/iwtc-shared-db`
- `ddongmy/ddongmy-db`

## Database layout

The shared PostgreSQL instance currently hosts:

- `iwtc` — owner: `iwtc_app`
- `ddongmy` — owner: `ddongmy_app`

## Safety

The legacy `iwtc/postgres-0` StatefulSet and PVC are intentionally kept outside this repository during the rollback window. Do not delete them until the shared database has been stable for several days and restore procedures have been verified.
