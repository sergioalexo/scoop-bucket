# sergioalexo scoop bucket

A [Scoop](https://scoop.sh) bucket for tools by [Sergio Alexo](https://sergioalexo.com).

```powershell
scoop bucket add sergioalexo https://github.com/sergioalexo/scoop-bucket
scoop install <app>
```

## Apps

| App | Description |
|---|---|
| **revaudit** | Audits released Onshape assemblies for drawing / release gaps and checks production-file (DXF/SAT/PDF/STEP) coverage. [Source](https://github.com/sergioalexo/revaudit) |

### revaudit

```powershell
scoop install revaudit
```

Pulls in Python if missing and adds four commands to your PATH:

| Command | Runs |
|---|---|
| `revaudit` | the CLI (`revaudit ASM-12345 --dxf-dir "\\share\DXF FILES"`) |
| `revaudit-serve` | the single-user web UI |
| `revaudit-oauth` | the multi-user OAuth app |
| `revaudit-launch` | the double-click launcher (browser + server) |

`.env` (Onshape API key) and `revaudit.conf` (folders, port, advertised address)
are **persisted** — `scoop update revaudit` swaps the code and leaves your settings
in place. First install seeds both from the bundled templates and points the report
folder at a persisted directory so audit history also survives updates.

```powershell
scoop prefix revaudit    # open the install folder; edit .env and revaudit.conf
revaudit-serve
```

## Updating manifests

Each manifest carries `checkver` + `autoupdate` metadata, so:

```powershell
scoop update
# or, to refresh the manifest against upstream tags:
.\bin\checkver.ps1 revaudit -Update    # when run from a full Scoop bucket checkout
```
