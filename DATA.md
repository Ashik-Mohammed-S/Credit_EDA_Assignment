# Recovered data and execution

The public copies below match the filenames and schemas used by this notebook.
Original lost-file byte identity cannot be proved. URLs are pinned to source commits,
and SHA-256 checksums in dataset-sources.json prevent silent source changes.
Data is downloaded locally rather than added as new dataset blobs in this PR.

| File | Rows / tokens | Source |
| --- | --- | --- |
| `application_data.csv` | 307511 | [Pinned source](https://media.githubusercontent.com/media/sfbrigade/datasci-home-credit-default/9a5e9008a5f16f7bcd2bd54a0db3c93de0b94dd9/src/home-credit-default-risk/application_train.csv.zip) |
| `previous_application.csv` | 1670214 | [Pinned source](https://media.githubusercontent.com/media/sfbrigade/datasci-home-credit-default/9a5e9008a5f16f7bcd2bd54a0db3c93de0b94dd9/src/home-credit-default-risk/previous_application.csv.zip) |

Source repository license metadata: No explicit repository license was reported; data is restored by download and no new redistribution license is granted.

```sh
python -m pip install -r requirements.txt
python scripts/fetch_data.py
python scripts/run_notebook.py --mode quick
python -m jupyterlab
```

Install the spaCy English model first where used: `python -m spacy download en_core_web_sm`.
The notebook also restores missing reference files automatically when run from the repository root.
Set DATA_DIR to use another directory containing these same reference files.
Existing files with a different checksum are left untouched and reported as mismatches.

Both modes use all recovered rows and the original training/analysis workload. Full experiments are available with `--mode full`, or set RUN_MODE=full before
launching the notebook. Quick results demonstrate execution; they do not reproduce
the historical trained-model quality. The runner writes results/execution-report.json.

