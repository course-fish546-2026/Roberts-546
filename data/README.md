# data/

- `raw/` holds raw inputs and is **not committed** (see `.gitignore`). Record each raw file here: source, date obtained, and checksum.
- `processed/` holds small derived tables that are safe to commit.

## Raw data record

| File | Source | Date | md5 |
|---|---|---|---|
| | | | |

Generate checksums with `md5sum data/raw/* > data/raw-checksums.txt` and commit that file.

## Derived files not committed

These folders are committed, but the large files inside them are excluded in the top-level `.gitignore`. All of them are rebuilt from the raw reads by [`code/03-eDNA.qmd`](../code/03-eDNA.qmd). The QC reports (`*_fastp.html`, `*_fastp.json`, `*_cutadapt.log`, MultiQC HTML) in the same folders **are** committed.

| Excluded files | Files | Size | Made by (section in `03-eDNA.qmd`) |
|---|---|---|---|
| `trimmed/eDNA-yellow_island-2023/*.fastq.gz` | 118 | ~1.2 GB | Trim reads with fastp |
| `trimmed/eDNA-yellow_island-2023/multiqc/multiqc_data/` | — | ~65 MB | Summarize fastp reports with MultiQC |
| `primer-trimmed/eDNA-yellow_island-2023/{V9,COI}/*.fastq.gz` | 216 | ~1.5 GB | Remove primers and split by marker with cutadapt |
| `trimmed-qc/eDNA-yellow_island-2023/{V9,COI}/*.fastq.gz` | 216 | ~0.7 GB | Quality trim each marker with fastp |
| `trimmed-qc/eDNA-yellow_island-2023/{V9,COI}/multiqc/*_multiqc_report_data/` | — | ~120 MB | Summarize quality-trimmed reports with MultiQC |
| `qiime2/eDNA-yellow_island-2023/{V9,COI}/demux.qza` | 2 | — | QIIME 2 import (copy of the trimmed-qc reads) |

Raw input: 119 `.fastq.gz` files from <https://owl.fish.washington.edu/nightingales/eDNA-yellow_island-2023/>, downloaded to `raw/eDNA-yellow_island-2023/` and checked against the server's `.md5` files (see "Check that downloads are complete" in `03-eDNA.qmd`).

To rebuild, render or run `code/03-eDNA.qmd` from the `code/` folder in order: download → trim → cutadapt → fastp per marker → MultiQC.
