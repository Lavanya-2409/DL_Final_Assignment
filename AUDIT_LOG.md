# AUDIT LOG — Operation Cyber-Histology

## data.py

| # | File | Manifestation | Root Cause | Fix | Commit Hash |
|---|---|---|---|---|---|
| 1 | data.py | FileNotFoundError at runtime | Wrong filename suffix `_data.pt` | Changed to `{data}.pt` | `426482a` |
| 2 | data.py | Silent data leakage | Train set not sliced before val split | Applied `[:val_start]` slice | `8f2625e` |
| 3 | data.py | Incorrect loss computation | Labels shaped `[N,1]` instead of `[N]` | Applied `.squeeze(1)` on all label sets | `314693c` |
| 4 | data.py | Biased validation split | Data not shuffled before splitting | Added `torch.randperm` shuffle | `b48c528` |
| 5 | data.py | Unstable/slow training | Raw pixel values `[0-255]` not normalized | Divided by `255.0` | `44da953` |
