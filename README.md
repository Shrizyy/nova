# NOVA — Neural Operations & Versatile Assistant

Your personal Windows assistant, coding workspace and local computer tools, based on OpenJarvis (Apache-2.0).

## Download and restore

Download `NOVA-Windows-source.zip` from this repository and extract it into a new folder. It contains the source, frontend, tests, Windows helpers and guides. The bundled macOS Ollama executable is omitted; Windows uses its separately installed Ollama.

This is a source backup. GitHub stores the files; NOVA runs on your computer. Your existing installation remains at `S:\jarvis`.

### Existing laptop

Use your **NOVA + OmniRoute** desktop shortcut. Do not replace your existing data folder when restoring source.

### New Windows setup

Install Python 3.12, Node.js, uv and (for local models) Ollama. In the extracted source folder run:

```powershell
uv sync --extra server --extra computer-control --extra inference-google
cd frontend
npm.cmd ci
npm.cmd run build
cd ..
```

This regenerates dependency resolution if the computer-control extra is newer than the saved lockfile; avoid `--frozen` during initial restoration.

Keep credentials in environment variables: `OMNIROUTE_API_KEY`, `OMNIROUTE_BASE_URL` (normally `http://127.0.0.1:20128/v1`), and optional `GEMINI_API_KEY`. Enter your own values locally; never commit them. Install/start OmniRoute separately and reconnect your providers. Its credentials/database are not in this backup.

For a basic local server:

```powershell
$env:OPENJARVIS_SQLITE_FALLBACK='1'
$env:JARVIS_CODING_WORKSPACE=Join-Path $PWD 'projects'
uv run jarvis serve --host 127.0.0.1 --port 8000
```

Open http://127.0.0.1:8000/. Review `docs/NOVA-computer-guide.md` before setting up Windows computer controls. The `windows-host` scripts document the original host layout; their scheduled tasks must be recreated on a new laptop. They are not an automatic installer.

See the included `UPSTREAM-README.md` and `docs` for REA/MCP and backend configuration. Reinstall external REA/native tools and update their local paths; external tool installs are not bundled.

## What is excluded

API keys, local chat databases, saved accounts, Windows-protected pairing tokens, logs, personal projects, virtual environments and installed dependencies. The source archive has no upstream Git history. Keep your local data backup separately if you want conversations restored.

## Attribution

Derived from https://github.com/open-jarvis/OpenJarvis. Original LICENSE and source attribution are preserved inside the archive.
