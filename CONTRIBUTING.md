# Contributing to Awesome Object Storage

Thanks for helping keep this list accurate. Object storage pricing and features change constantly, and crowdsourced verification is the only way to keep up.

## Table of Contents

- [Submitting a Correction](#submitting-a-correction)
- [Adding a New Provider](#adding-a-new-provider)
- [Reporting Errors](#reporting-errors)
- [Code of Conduct](#code-of-conduct)
- [How Data Is Verified](#how-data-is-verified)
- [The Interactive Tool](#the-interactive-tool)

---

## Submitting a Correction

If a price, feature, or gotcha is wrong:

1. **Find the provider JSON** in `data/providers/`. Each provider has its own file (e.g., `data/providers/aws-s3.json`).
2. **Edit the relevant field** with the correct value.
3. **Add a source URL** in the `sources` array. Every factual claim must link to an official pricing page, documentation page, or verifiable third-party source.
4. **Update the `last_verified` date** to today's date (ISO 8601 format: `YYYY-MM-DD`).
5. **Submit a PR** with a clear title like: `fix(wasabi): update egress policy threshold`

Example commit:
```
fix(backblaze-b2): correct free egress from 1x to 3x storage

Source: https://www.backblaze.com/cloud-storage/pricing
Verified: 2026-04-01
```

**Do not update the README table directly.** The README is generated from the JSON data. Update the JSON and the README will be regenerated.

---

## Adding a New Provider

To add a provider that isn't listed:

1. **Copy the schema template** below into a new file at `data/providers/<provider-slug>.json`.
2. **Fill in every field.** If a field is unknown or not applicable, use `null` -- do not guess or leave it blank.
3. **Include source URLs** for every pricing and feature claim.
4. **Submit a PR** with a title like: `feat: add Seaweed Storage provider`

### Provider JSON Schema

```json
{
  "id": "provider-slug",
  "name": "Provider Display Name",
  "url": "https://provider.com",
  "pricing_url": "https://provider.com/pricing",
  "docs_url": "https://provider.com/docs",
  "s3_compat_url": "https://provider.com/docs/s3-api",
  "pricing": {
    "storage_per_gb_month": 0.006,
    "egress_per_gb": 0.01,
    "free_egress": "3x storage",
    "get_per_1k": 0.004,
    "put_per_1k": 0.005,
    "delete_per_1k": 0,
    "minimum_retention_days": null,
    "minimum_storage_charge_gb": null
  },
  "features": {
    "s3_compatible": true,
    "s3_compat_level": "full",
    "object_lock": true,
    "versioning": true,
    "server_side_encryption": true,
    "sse_kms": false,
    "max_object_size_tb": 5,
    "multipart_upload": true,
    "presigned_urls": true,
    "bucket_notifications": false,
    "lifecycle_rules": true,
    "replication": false,
    "storage_tiers": 1,
    "tier_names": ["Standard"]
  },
  "regions": ["us-east", "us-west", "eu-central"],
  "gotchas": [
    "Short description of each gotcha or limitation"
  ],
  "sources": [
    "https://provider.com/pricing",
    "https://provider.com/docs/s3-compatible-api"
  ],
  "last_verified": "2026-04-01"
}
```

### Requirements for New Providers

- The provider must offer S3-compatible object storage as a generally available product (not private beta).
- All pricing must be sourced from official provider pages.
- Include at least one "gotcha" -- every provider has at least one. If you can't find one, you haven't looked hard enough.

---

## Reporting Errors

If you notice incorrect data but don't want to submit a PR, open an issue with:

- **Provider name**: Which provider has the error.
- **Field**: Which specific data point is wrong (e.g., "egress price," "object lock support").
- **Current (incorrect) value**: What the list currently says.
- **Correct value**: What it should say.
- **Source URL**: A link to the official page that shows the correct value.

Use the issue title format: `data error: [provider] - [field]`

Example:
```
Title: data error: Wasabi - minimum retention days
Body:
  Provider: Wasabi
  Field: minimum_retention_days
  Current value: 90
  Correct value: 30 (changed in Q1 2026)
  Source: https://wasabi.com/pricing (see FAQ section)
```

---

## Code of Conduct

This project exists to provide accurate, useful data. To keep it that way:

1. **Keep it factual.** No marketing language, no superlatives ("best," "fastest," "most reliable"), no unsubstantiated claims. State what a provider offers and at what price.

2. **Source everything.** Every claim about pricing, features, or limitations must link to a verifiable source -- ideally the provider's official documentation or pricing page. Blog posts and third-party reviews are acceptable for gotchas and benchmarks, but not for pricing.

3. **No provider advocacy.** PRs that read like marketing copy will be closed. If you work for a provider, disclose it in your PR description. Contributions from provider employees are welcome as long as they're factual and include sources.

4. **Gotchas are not attacks.** Documenting a provider's limitations is not adversarial -- it's useful. Every provider has trade-offs. The goal is to help people make informed decisions, not to promote or demote any provider.

5. **Be specific.** "S3 compatibility is bad" is not useful. "Multipart uploads fail above 5 GB because max object size is 5 GB" is useful.

6. **Keep PRs focused.** One provider per PR, or one category of correction per PR. Don't bundle unrelated changes.

---

## How Data Is Verified

Maintainers verify PRs against the following sources, in order of preference:

1. **Official pricing pages** -- The provider's published pricing (e.g., `aws.amazon.com/s3/pricing/`).
2. **Official documentation** -- Feature documentation, API references, FAQs.
3. **Provider changelogs / blog posts** -- For recent changes not yet reflected in pricing pages.
4. **Independent benchmarks** -- For performance claims and gotchas.
5. **Community reports** -- GitHub issues, forum posts, HN threads -- accepted for gotchas but not for pricing.

Pricing is verified at least quarterly. If a provider changes pricing and nobody submits a PR, there may be a lag. The `last_verified` date on each provider JSON shows when the data was last checked.

If a claim cannot be verified from any of the above sources, it will be marked with a `[unverified]` tag or removed until a source is provided.

---

## The Interactive Tool

The interactive comparison tool at **[storage.mixpeek.com](https://storage.mixpeek.com)** is auto-generated from the JSON data in this repository's `data/providers/` directory.

When your PR is merged:
1. The CI pipeline validates the JSON schema.
2. The tool is rebuilt with the updated data.
3. Changes appear on the live site within a few minutes.

This means the JSON files in this repo are the single source of truth. Do not submit changes to the interactive tool directly -- update the JSON data and the tool will follow.

---

## Questions?

Open an issue with the `question` label. We'll do our best to respond quickly.
