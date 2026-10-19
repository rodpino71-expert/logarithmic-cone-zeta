# Pre-registration of the confirmatory run

`preregistro_confirmacion.md` (in Spanish) fixes, before the run, the code to be frozen, the new γ range [60, 100], the hypotheses, the decision rule and the risks expected in advance. `preregistro_confirmacion.sha256` holds its SHA-256 digest and the registration time stated by the author (2026-10-12, 08:22:23 UTC); the same digest is printed in footnote 1 of the paper.

## How to check it

**The document is the one the paper cites.**

```bash
sha256sum preregistro_confirmacion.md
# 883963ad640caec1fd97a9d63c6354cc1686e7ec73b5e3545ec302a7583155c1
```

**The confirmatory code differs from v3 only where the document says.** Comparing the code cells of `notebooks/cono_residuo_zeta_v3.ipynb` and `notebooks/cono_residuo_zeta_v3_confirmacion.ipynb` gives exactly three differences: the γ range, the mpmath sanity check and the name of the output file.

```python
import json, difflib
code = lambda f: "\n".join("".join(c["source"]) for c in json.load(open(f))["cells"]
                           if c["cell_type"] == "code").splitlines()
a = code("../notebooks/cono_residuo_zeta_v3.ipynb")
b = code("../notebooks/cono_residuo_zeta_v3_confirmacion.ipynb")
print("\n".join(difflib.unified_diff(a, b, "v3", "confirmation", n=0, lineterm="")))
```

## What these files do not prove

The registration time is the author's own record, not a third-party timestamp. The executed notebook's cell metadata shows the run starting at 08:22:34 UTC on the same day, eleven seconds after the stated registration time; that metadata is also self-reported. A public deposit (for example on Zenodo) timestamps the documents from the date of deposit onward.

The notebook digest and the digest of the v3 code cells quoted inside the document were computed with a method that is not recorded, and they do not match the files as saved here; notebooks change bytes when they are re-saved. The code comparison above is the check that can be reproduced.
