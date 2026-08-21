# energy-proof-data

Public, machine-generated energy snapshot feed for **https://mklab.homes/energy-lab**.

- `energy-proof-ha-snapshot.json` — sanitized Home Assistant metering snapshot, refreshed roughly every 15 minutes by a Mac-local collector.
- The file holds only the public metrics already shown on the page: device display name, model, protocol, and kWh / W / V / A facts. **No tokens, no HA entity IDs, no HA URL, no credentials.**

## Why a separate repo

The site reads this snapshot at request time through its `/api/energy-proof-snapshot` function. Keeping the high-frequency data in its own repo — one the site's host does not watch — means a data update never triggers a site rebuild. The site code stays static; the snapshot stays live.

Consumed by raw URL:

```
https://raw.githubusercontent.com/Ming-kun/energy-proof-data/main/energy-proof-ha-snapshot.json
```

## Naming

The repo name, the JSON filename, and the API path all keep the `energy-proof` wording from the page's earlier title. The public page is now **MK's Energy Testing Lab** at `/energy-lab`, and the old `/energy-proof` URL redirects there. These identifiers were deliberately left unchanged so the collector and the feed URL keep working.

This repo is a telemetry feed, not a source of truth. Do not edit it by hand; the collector overwrites it.
