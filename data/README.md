# data/

- `raw/` holds raw inputs and is **not committed** (see `.gitignore`). Record each raw file here: source, date obtained, and checksum.
- `processed/` holds small derived tables that are safe to commit.

## Raw data record

| File | Source | Date | md5 |
|---|---|---|---|
| | | | |

Generate checksums with `md5sum data/raw/* > data/raw-checksums.txt` and commit that file.
