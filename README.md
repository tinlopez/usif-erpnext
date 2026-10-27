# usif-erpnext

Custom ERPNext image for US International Foods (S1200 server).

- `apps.json` lists the apps baked into the image: ERPNext (version-16) + Frappe CRM.
- GitHub Actions builds it with the official `frappe_docker` layered Containerfile and pushes:
  - `ghcr.io/<owner>/usif-erpnext:v16` (latest build)
  - `ghcr.io/<owner>/usif-erpnext:v16-<run number>` (fixed, use this in Coolify)
- No secrets live here: only public app sources. The GHCR package is public, so the server pulls without a login.

To add an app (e.g. Frappe Drive): add it to `apps.json`, push, wait for the build, change the tag in Coolify, redeploy, then
`bench --site erp.usinternationalfoods.com install-app <app>` and `bench --site erp.usinternationalfoods.com migrate`.
