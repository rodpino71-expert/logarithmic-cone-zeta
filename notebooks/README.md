# Notebooks

Each version comes in two files: the clean notebook and the same notebook executed at X = 10⁹ (with all printed outputs kept). The notebooks are written in Spanish; each one opens with its amendment log.

| Version | Clean notebook | Executed at 10⁹ | Change | Verdict |
|---|---|---|---|---|
| v1 | `cono_residuo_zeta.ipynb` | `cono_residuo_zeta_ejecutado_1e9.ipynb` | γ ∈ [10, 60] | Not conclusive: (a) 46 %, (c) drift 0.289 > 0.273 |
| v2 | `cono_residuo_zeta_v2.ipynb` | `cono_residuo_zeta_v2_ejecutado_1e9.ipynb` | Filter v ln p / p < 0.05 | Robust signal; peaks biased low (13/13 negative) |
| v3 | `cono_residuo_zeta_v3.ipynb` | `cono_residuo_zeta_v3_ejecutado_1e9.ipynb` | Span centre, 99 null sequences | Robust signal; no sign bias (3/13 negative, p = 0.09) |
| Confirmation | `cono_residuo_zeta_v3_confirmacion.ipynb` | `cono_residuo_zeta_v3_confirmacion_ejecutado.ipynb` | Code of v3 frozen; γ ∈ [60, 100] | Not confirmed: (a) 38 %; (b) and (c) met |

v1 to v3 are the exploratory versions summarised in Table 1 of the paper. The confirmation notebook is the pre-registered run of Table 2: its code differs from v3 in exactly the three places the pre-registration lists: the γ range, one sanity check (`zetazero(1)` instead of the first zero of the range) and the name of the output file. The pre-registration document it refers to is in [`../preregistration/`](../preregistration/).

Requirements: `numpy`, `matplotlib`, `mpmath`. A v3 run at 10⁹ with 99 + 99 null sequences takes about 18 minutes on two virtual CPUs and peaks at about 1.3 GB of memory.
