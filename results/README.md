# Result files

Each notebook writes one JSON file with its parameters, the matched peaks, the robustness table, every null-sequence count, the p-values, the z-scores and the automatic verdict. Keys are in Spanish (`nulos` = null sequences, `aciertos` = matched zeros, `deriva` = drift, `veredicto` = verdict).

| File | Version | numpy | Verdict |
|---|---|---|---|
| `resultados_cono_zeta.json` | v1 | 2.1.3 | NO CONCLUYENTE |
| `resultados_cono_zeta_1e9.json` | v1, second run | 2.5.3 | NO CONCLUYENTE |
| `resultados_cono_zeta_v2_1e9.json` | v2 | 2.5.3 | SEÑAL ROBUSTA |
| `resultados_cono_zeta_v2_segunda_corrida.json` | v2, second run | 2.1.3 | SEÑAL ROBUSTA |
| `resultados_cono_zeta_v3.json` | v3 | 2.1.3 | SEÑAL ROBUSTA |

The JSON of the pre-registered confirmation (`resultados_confirmacion.json`) is not included; its full output is printed in `notebooks/cono_residuo_zeta_v3_confirmacion_ejecutado.ipynb`.

## What the files show about reproducibility

- **v1, two runs with different numpy versions.** Every count is identical, including the 40 null sequences; floating-point values differ by at most 2.5 × 10⁻¹⁴ (relative).
- **v3, two separate runs.** `resultados_cono_zeta_v3.json` (numpy 2.1.3, peak memory 1,174 MB) and the executed v3 notebook (peak memory 1,329 MB) come from different runs. The 13 matched peaks agree to the four decimals the notebook prints, and all 198 null-sequence counts are identical.
- **v2, two runs with different numpy versions.** Every count is identical, including the 40 null sequences; floating-point values differ by at most 4.7 × 10⁻¹³ (relative). The first file and the executed v2 notebook come from the same run (peak memory 1,282 MB in both); the second run peaked at 1,295 MB. The second file was found under the name `otro.json` and renamed here.
