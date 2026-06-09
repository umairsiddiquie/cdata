# cdata

Chains Data is a comprehensive dataset of 2,619 blockchain networks with RPC endpoints, explorers, and metadata.

---

Copyright © 2026 Umair Abbas (UA)
ORCID: 0009-0008-3968-2252
All Rights Reserved.

---

Table of contents
- About
- Dataset summary
- File structure
- Data schema
- Examples (loading & querying)
- How to contribute
- Updating the dataset
- License & attribution
- Contact

About

This repository contains a curated dataset derived from a `chains.json` source. The dataset contains metadata for 2,619 blockchain networks including network names, chain IDs, native currency metadata, RPC endpoints, block explorers, faucets, features, and status fields.

Dataset summary

- Networks: 2,619
- Formats: CSV (.csv) and Excel (.xlsx)
- Typical fields included:
  - network_name
  - chain_id
  - native_currency_name
  - native_currency_symbol
  - native_currency_decimals
  - rpc_endpoints (one or more)
  - block_explorers (one or more)
  - faucets (optional)
  - features (array)
  - status (active / deprecated / testnet / other)

File structure

- /data
  - chains.csv
  - chains.xlsx
  - (other raw or processed data files)
- /docs
  - overview.md
  - schema.md
- /examples
  - usage examples (scripts, notebooks)
- README.md
- CONTRIBUTING.md
- .gitignore
- LICENSE

Data schema (recommended fields)

Below is a suggested canonical schema for the dataset. Not every row will contain every field — some fields are optional or may contain arrays.

- id: unique identifier for the dataset row (string)
- network_name: human-readable name (string)
- chain_id: numeric chain id (integer)
- short_name: short identifier (string, optional)
- native_currency_name: (string)
- native_currency_symbol: (string)
- native_currency_decimals: (integer)
- rpc_endpoints: array of objects [{"name": "", "url": "", "type": "public|archive|archive-light"}] or a semicolon-separated string
- block_explorers: array of objects [{"name": "", "url": ""}] or a semicolon-separated string
- faucets: array or string (optional)
- features: array[string] (e.g., ["EVM", "Layer2", "zK"])
- status: string (e.g., "active", "deprecated", "testnet")
- notes: free-form notes (string, optional)

Examples (loading & querying)

Python (pandas)

```python
import pandas as pd

# load CSV
df = pd.read_csv('data/chains.csv')

# show networks that support a particular feature
evm_chains = df[df['features'].str.contains('EVM', na=False)]

# filter by status
active = df[df['status'] == 'active']
```

Command-line (csvkit)

- csvcut, csvgrep, csvstat are useful for quick exploration.

How to contribute

See CONTRIBUTING.md for full contribution guidelines. In short:
- Open an issue if you find incorrect or missing metadata.
- Fork the repository and submit a pull request with changes to the CSV/XLSX or docs.
- Include tests or a short explanation for data fixes.

Updating the dataset

If you re-run the `chains.json` extraction, include:
- a brief summary of changes in CHANGELOG.md (new networks, removed, updated endpoints)
- the source and extraction script in /docs or /scripts for reproducibility

License & attribution

License: To be specified. Please see the LICENSE file.

Citation

If you use this dataset in research, please cite:

Umair Abbas (UA). cdata: Chains Data (2026). ORCID: 0009-0008-3968-2252

Contact

For questions or issues, please open an issue in this repository or contact the maintainer (Umair Abbas).
