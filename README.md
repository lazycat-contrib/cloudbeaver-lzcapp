# CloudBeaver (LazyCat LPK)

Web database client (DBeaver's browser edition).

- Upstream: https://github.com/dbeaver/cloudbeaver
- Image: `dbeaver/cloudbeaver:26.2.4` (Docker Hub, mirror mode, digest-matched)
- License: Apache-2.0 (full text in `content/licenses/LICENSE`)
- Containers: single. Client tool only — ships no database.

## Notes

- Port 8978, entry `launch-product.sh`.
- **Account is created in the first-run setup wizard**, not by env vars. Checked
  `config/core/initial-data.conf` (only team/subject definitions, no password field) and
  `deploy/scripts/launch-product.sh` (no CB_* admin vars). So there is no built-in credential and
  no deploy params needed.
- Because the admin lives in the workspace, `/opt/cloudbeaver/workspace` MUST persist —
  mounted at `/lzcapp/var/workspace`. Without it the wizard would run again after every restart
  and saved connections would vanish.
- Saved connection passwords live inside that workspace (encrypted by CloudBeaver), which is why
  the usage text tells the operator to protect the app login.
- Version tags are plain `x.y.z` (26.2.4); `26.2` / `26` also exist but the regex excludes them.
- Not yet verified on a real device.
