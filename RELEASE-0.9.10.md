# Cloud recovery 0.9.10

Runtime marker: `2026-10-03-cloud-recovery-v1`.

Based on the deployed 0.9.8 server. Changes are limited to account persistence protection, bounded upstream requests, correct OTP vs provider failure classification, and redacted diagnostics. Native UI and OCR engine changes are not included in this cloud release.

Validation: 42 automated tests passed, including 10 cloud transport/persistence/HTTP regression tests with isolated accounts and simulated upstream failures. No real OTP is sent by automated tests.

Build command: `tar -xzf travel-bill-source-0.9.10.tar.gz && npm install`
Start command: `node server.mjs`

Preserve existing environment variables, encryption keys and Supabase project. Do not reapply generated keys from render.yaml or reinitialize databases.

Archive allowlist: server.mjs, lib, public, test, test-support, supabase/schema.sql, package.json, pnpm-lock.yaml, render.yaml. No local data, media, credentials, node_modules, native builds or user source images.

Rollback: restore the previous build command `tar -xzf travel-bill-source-0.9.8.tar.gz && npm install` and deploy. There are no database migrations in this release. Version 0.9.8 lacks the new fail-closed protection, so rollback should only be used after diagnosing a verified regression.
