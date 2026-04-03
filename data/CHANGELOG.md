# Data Changelog

Track of when provider data was verified and what changed. Each entry includes the provider, date, and what was updated.

For per-provider last-verified dates, see the `verified` field in each provider's JSON file.

---

## April 2026

### Verified (no changes)
- **Amazon S3** — All pricing and features confirmed against [aws.amazon.com/s3/pricing](https://aws.amazon.com/s3/pricing/). (Apr 2)
- **Google Cloud Storage** — Pricing and features confirmed against [cloud.google.com/storage/pricing](https://cloud.google.com/storage/pricing). (Apr 2)
- **Azure Blob Storage** — Pricing confirmed. S3 compat endpoint still in preview. (Apr 2)
- **Cloudflare R2** — Pricing confirmed. IA tier added at $0.01/GB/mo with 30-day minimum. (Apr 2)
- **Tigris** — Pricing and tiers confirmed. Now 4 tiers (Standard, IA, Archive Instant, Archive). (Apr 2)
- **Backblaze B2** — Pricing confirmed at $0.006/GB. Still 3 regions. (Apr 2)
- **Wasabi** — 90-day minimum retention confirmed. Reasonable use egress policy unchanged. (Apr 2)
- **DigitalOcean Spaces** — $5/mo minimum, 5 GB max object confirmed. (Apr 2)
- **MinIO** — AGPL-3.0 confirmed. AIStor Enterprise is the commercial option. (Apr 2)
- **IDrive e2** — $0.004/GB confirmed. Reasonable use egress policy unchanged. (Apr 2)
- **OVHcloud** — Free egress confirmed (since January 2026). 30-day min retention on all tiers. (Apr 2)
- **IBM Cloud Object Storage** — 14 nines durability confirmed. Complex pricing tiers verified. (Apr 2)
- **Nebius** — Pricing and 4-tier structure confirmed. EU-only (Finland). (Apr 2)
- **Storj** — $0.004/GB and $0.007/GB egress confirmed. 9 nines durability. (Apr 2)

### Updated
- **Cloudflare R2** — Added Infrequent Access tier data (new tier launched). (Apr 2)
- **Tigris** — Updated from 2 to 4 storage tiers after they added Archive tiers. (Apr 2)

## March 2026

### Initial data collection
- **Hetzner** — Initial entry. EU-only (Germany, Finland). No lifecycle policies. (Mar 28)
- **Oracle Cloud OCI** — Initial entry. 10 TB/mo free egress (!), 46 regions. (Mar 28)
- **Scaleway** — Initial entry. EU-only. Unusual GET pricing ($0.0044/1K = same as PUT). (Mar 28)
- **Vultr** — Initial entry. 5 GB max object, no SSE, durability not published. (Mar 28)
- **Akamai / Linode** — Initial entry. 5 GB max object, Akamai CDN integration. (Mar 28)
- **Impossible Cloud** — Initial entry. EU-focused, free egress, newer provider. (Mar 28)
- **Fastly** — Initial entry. Newer entrant (2024 launch), fewer features than R2. (Mar 28)

---

## How to Read This

- **Verified (no changes)**: Data was checked against official sources and confirmed accurate.
- **Updated**: A field value changed — the old and new values are noted.
- **Initial data collection**: First time this provider was added to the dataset.

Each provider JSON file has a `verified` field with the month it was last checked. If you find an error, [open an issue](https://github.com/mixpeek/awesome-object-storage/issues) or submit a PR with the correction and source URL.
