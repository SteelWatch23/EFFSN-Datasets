# EFFSN Datasets

Public download location for the cleaned EFFSN tables. This repository stays small on purpose: it does not contain source workbooks or mapping files. Those stay in the private [EFFSN-Data-Tool](https://github.com/SteelWatch23/EFFSN-Data-Tool) repository.

The GitHub Action in Data-Tool runs the cleaning pipeline, then publishes the eight CSVs onto the **`latest`** release of this repo (overwriting the previous files).

## Files

| File | Contents |
| --- | --- |
| `Plants.csv` | Plants |
| `Units.csv` | Units |
| `Companies.csv` | Companies |
| `Plants_ownership.csv` | Plant ownership |
| `Companies_simplified.csv` | Simplified company ownership |
| `Emissions_ClimateTrace.csv` | Climate TRACE emissions |
| `Emissions_EDGAR.csv` | EDGAR emissions |
| `Production.csv` | Production |

## Download URLs

Replace the filename as needed:

`https://github.com/SteelWatch23/EFFSN-Datasets/releases/download/latest/Plants.csv`

Power BI (Import, Web connector) and the EFFSN website (DuckDB `read_csv`) should use these URLs. Do not commit CSV updates to `main`; the release is the feed.

This repository must stay **public**. A private release cannot be refreshed anonymously by Power BI or the website.

## One-time GitHub setup

In **EFFSN-Data-Tool → Settings → Secrets and variables → Actions**, add:

| Secret | Value |
| --- | --- |
| `DATA_REPO_TOKEN` | Fine-grained personal access token, or a GitHub App token, with **Contents: Read and write** on `SteelWatch23/EFFSN-Datasets` only |

The first successful pipeline run on `main` creates the `latest` release. Later runs replace the same eight assets, so the URLs above do not change.
