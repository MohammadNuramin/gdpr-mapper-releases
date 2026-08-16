# GDPR Mapper — release feed

This repository exists only to publish `releases.json`, the file an installed
GDPR Mapper polls to learn that a newer version exists.

It is public because a customer deployment must be able to read it without
credentials. It contains **no source code and no data** — the product itself is
developed in a private repository.

## What the file means

```json
{
  "version":  "1.3.0",
  "digest":   "sha256:...",        // the image this version must have
  "released_at": "2026-08-16T07:54:11Z",
  "notes":    "shown in the update dialog",
  "breaking": false                 // true = changes stored data, cannot be rolled back
}
```

A deployment reads it from:

    https://raw.githubusercontent.com/MohammadNuramin/gdpr-mapper-releases/main/releases.json

The file names a **version and a digest, never a repository**. Where an update
is installed from is fixed in each deployment's own configuration, so nothing
published here can redirect an installation elsewhere.

Sites without outbound internet leave `MAPPER_UPDATE_MANIFEST_URL` empty, or
point it at their own internal mirror of this file.
