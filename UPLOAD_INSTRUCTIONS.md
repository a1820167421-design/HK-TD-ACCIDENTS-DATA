# Zenodo Upload Instructions

You have two paths. **Path A** (GitHub-linked) gives the most reproducible
chain (commit hash + Zenodo DOI bound together). **Path B** (manual web
upload) is faster (about 10 minutes).

## Path A — GitHub-linked Zenodo deposit (recommended for paper SI)

This is what most TRD-tier papers use. The advantage is that the Zenodo
record is permanently bound to a specific GitHub commit, which is what
reviewers expect.

### Steps

1. Sign in to https://zenodo.org with your GitHub account.
2. Go to the **GitHub** tab on Zenodo (https://zenodo.org/account/settings/github/),
   find your fork or a fresh repository for the snapshot, and toggle
   the **archiving switch** to ON for that repo.
3. Create a new GitHub repository under your account, for example
   `liaobo-nmti-hk-accidents-snapshot`.
4. Upload the contents of this folder (CSVs + README + LICENSE +
   CHECKSUMS + METADATA) to the new repo.
5. Create a release (e.g. `v1.0`). Zenodo will automatically archive the
   release and mint a DOI within ~5 minutes.
6. Copy the DOI (looks like `10.5281/zenodo.NNNNNNN`) and insert it into
   the paper text and SI.

### What to put in the GitHub repo

```
liaobo-nmti-hk-accidents-snapshot/
  README.md           (use this archive's README.md)
  LICENSE.txt         (MIT, this archive's LICENSE.txt)
  CHECKSUMS.sha256
  data/
    hk_accidents.csv
    hk_casualties.csv
    hk_vehicles.csv
  metadata.json       (optional, this archive's METADATA_zenodo.json)
```

Note: GitHub free repos cap individual files at 100 MB; our largest CSV is
21.6 MB, so we are safely under.

## Path B — Direct Zenodo web upload (fast)

If you want a DOI within 10 minutes without creating a GitHub repo:

1. Sign in to https://zenodo.org (you can register with ORCID).
2. Click **New upload** at https://zenodo.org/deposit/new.
3. Drag the four files from this folder into the upload box:
   - `hk_accidents.csv`
   - `hk_casualties.csv`
   - `hk_vehicles.csv`
   - `CHECKSUMS.sha256`
   - `LICENSE.txt`
   - `README.md`
4. Fill the form using values from `METADATA_zenodo.json` in this folder:
   - Upload type: **Dataset**
   - Title, Description, Authors, Keywords, License: paste from JSON
   - License: **MIT** (Open Source Initiative)
   - Access right: Open Access
   - Related identifiers: add the GitHub URL of the upstream hkdatasets
     repo with relation `isDerivedFrom`
5. Save and **Publish**. Zenodo mints a DOI immediately.

## After upload

1. Note the DOI Zenodo gives you (looks like `10.5281/zenodo.NNNNNNN`).
2. Insert that DOI into:
   - Paper §3.6 ¶2 (Hong Kong data-source statement)
   - Paper Data Availability statement
   - SI table of data sources
3. The DOI is permanent. The paper can cite it even if the upstream
   GitHub repo is later moved or removed.

## What you do NOT need to do

- You do **not** need to contact the Hong Kong Transport Department for
  permission. The MIT license inherited from hkdatasets covers
  redistribution, and the data was already publicly released through the
  Freedom of Information request and onward through the MIT-licensed
  package.
- You do **not** need to anonymize further. The upstream package already
  performed the anonymization at the level of the public record.
- You do **not** need to register the dataset with any other repository.
  Zenodo (run by CERN with EU data-protection compliance) is recognized
  by Elsevier journals (TRD's publisher) as an acceptable archive.

## Recommendation

Use Path A for the formal paper SI (cleanest reproducibility chain).
Path B is fine if the deadline is tight. Either path produces a valid
permanent DOI.
