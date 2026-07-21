# Agent Guidance

## Project Scope

This repository is the public source for the maintained Unicorn Busy Server
fork. It provides a Flask/Vite service for controlling a Pimoroni Unicorn pHAT
or Unicorn HAT Mini as a busy light.

This project is based on `estruyf/unicorn-busy-server` and is also the lineage
base for the later `unicorn-solar-server` and `unicorn-water-server` projects.

## Repository Layout

- `server.py`: Flask API and busy-light behavior.
- `lib/unicorn_wrapper.py`: hardware and dummy display wrapper.
- `frontend/`: Vite/React control panel.
- `install.sh`, `start.sh`, `busylight.service`: public install and service
  assets.

## Local Validation

Use the project README as the primary source for setup. For backend/runtime
checks, create a local virtual environment and run the server in dummy mode when
hardware is unavailable:

```bash
python3 -m venv .venv
.venv/bin/python -m pip install -r requirements.txt
.venv/bin/python server.py
```

For frontend changes:

```bash
cd frontend
npm install
npm run build
```

This repo may not have a backend unit-test suite. When no automated backend test
exists for a change, state that clearly and validate with the narrowest safe
local smoke check.

## Operating Rules

- Keep this repository public-safe. Do not add private hostnames, private paths,
  tokens, cron entries, local network details, or home deployment notes.
- Do not assume the service is currently deployed or running anywhere. Verify
  live deployment state outside this public repository before operational work.
- Keep private operation notes in a private location outside this repo.
- Preserve the public service identity documented here: `busylight.service` and
  default HTTP port `9000`.
- Only one Unicorn HAT Mini service should control the hardware at a time; keep
  service-conflict behavior explicit when changing install or systemd files.
- Preserve dummy-mode behavior for development and diagnostics without physical
  hardware.

## Change Expectations

- Keep API changes backward-compatible unless the user explicitly asks for a
  breaking change.
- Update README or public docs when public API, install behavior, or display
  behavior changes.
- For deployment-sensitive changes, propose and validate locally first; do not
  restart remote services or change private cron jobs from this repo context
  without explicit live-operation instructions.
