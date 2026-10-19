# Pre-registro: corrida confirmatoria del protocolo v3

**Estudio:** Residuo del cono logarítmico y ceros de ζ (R. Pino Osorio)
**Fecha de registro:** 2026-10-12, antes de ejecutar la corrida
**Notebook:** `cono_residuo_zeta_v3_confirmacion.ipynb`

## 1. Qué se congela

- Código idéntico a v3: SHA-256 de las celdas de código de v3 = `7520302eadd60cde6617b371f329e7c6df120ab95c4527d5b58ba86bb2023c2e`.
- Las únicas diferencias del notebook confirmatorio (SHA-256 = `8f7725a923afff2f9fc56af46b677cea1d011eaa58829944d94580cc5a51ee25`) son estas:
  1. `GAMMA_MIN, GAMMA_MAX = 60.0, 100.0`. En v3 el rango era [10, 60].
  2. El chequeo de mpmath compara con `zetazero(1)` y ya no con `ZEROS[0]`. No afecta el análisis.
  3. El nombre del JSON de salida.
- Se mantienen sin cambios: X = 10⁹, X_NULL = 10⁸, V_LIST = [10, 100, 1000], N_NULL = 99, SEED0, FILTRO_MAX = 0.05, CONVENCION = "centro", DT_BIN, DGAMMA, la ventana de Hann, la tendencia de grado 3, el peso p^(-1/2) y la regla de emparejamiento (los N picos más altos, con N = número de ceros en el rango, y tolerancia de ±0.5·resolución).

## 2. Datos nuevos

En [60, 100] hay 16 ceros de ζ (calculados con mpmath): 60.8318, 65.1125, 67.0798, 69.5464, 72.0672, 75.7047, 77.1448, 79.3374, 82.9104, 84.7355, 87.4253, 88.8091, 92.4919, 94.6513, 95.8706, 98.8312.
Ningún análisis previo (v1–v3, ni las pruebas exploratorias) examinó γ > 60.

## 3. Hipótesis y regla de decisión (umbrales idénticos a v1–v3)

- **H1 = criterio (a):** al menos 70 % de los ceros emparejados en todas las v y ventanas.
- **H2 = criterio (b):** p < 0.05 frente a Cramér y frente a Cramér-mod-30 (v = 100, X_NULL = 10⁸).
- **H3 = criterio (c):** deriva máxima de los picos entre v ≤ 0.5 · resolución (v = 100, ventana completa).
- **H4 (secundaria):** sin sesgo de signo en Δ = pico − γ para v = 100 (prueba de signo, p ≥ 0.05).

**Regla:** si H1, H2 y H3 se cumplen, el veredicto es **CONFIRMA**. Si falla cualquiera de ellas, el veredicto es **NO CONFIRMA**. H4 se reporta, pero no cambia el veredicto.

**Compromiso:** el resultado se reporta tal como salga. No se repite la corrida con otros parámetros. Cualquier ajuste posterior se llamaría v4 y sería exploratorio.

## 4. Expectativa previa (riesgos conocidos, declarados antes de correr)

El resultado no es seguro. Hay tres razones para esperar que la señal se debilite en [60, 100]:

1. **Amplitud menor.** Cada cero contribuye con amplitud ∝ 1/|ρ| ≈ 1/γ, cerca de la mitad que en [10, 60], mientras el ruido no cambia.
2. **Filtro pasa-bajos residual.** En el umbral v·ln p/p = 0.05, |sinc(γΔt/2)| vale 0.66 con γ = 60 y 0.24 con γ = 100. Afecta sobre todo a la mitad baja de las ventanas con v = 100 y v = 1000.
3. **Ceros más próximos.** Hay pares separados por solo 1.22 (94.65 y 95.87) y 1.38 (87.43 y 88.81), cerca de la anchura del lóbulo principal. Pueden fundirse en un solo pico.

Por eso es plausible que H1 falle en las mitades de ventana. Si falla, el resultado se reporta igual, junto con estas causas candidatas.
