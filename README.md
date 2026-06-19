# energy-proof-data

Public, machine-generated energy snapshot feed for **https://mklab.homes/energy-proof**.

- `energy-proof-ha-snapshot.json` — sanitized Home Assistant metering snapshot, refreshed ~every 15 minutes by the Mac-local collector (`com.mk.energy-proof-ha-collector`).
- The file holds only public demo metrics already shown on the Energy Proof page: device display name, model, protocol, kWh / W / V / A facts. **No tokens, no HA entity IDs, no HA URL, no credentials.**

## Why a separate repo

The Energy Proof site (`Ming-kun/website-MK`, private → Vercel) reads this snapshot at request time via its `/api/energy-proof-snapshot` function. Keeping the high-frequency data here, in a repo Vercel does **not** watch, means data updates never trigger a site rebuild — the site code stays static and the snapshot stays live.

Consumed by raw URL:

```
https://raw.githubusercontent.com/Ming-kun/energy-proof-data/main/energy-proof-ha-snapshot.json
```

This repo is a telemetry feed, not a source of truth. Do not edit by hand; the collector overwrites it.
