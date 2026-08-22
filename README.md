# Datos del curso — Modelador de Riesgo de Crédito (Academia Bayes)

Datasets **100% sintéticos** para uso académico del curso. Ninguna persona ni
institución real está representada. Generados por Academia Bayes / Nexo Labs.

| Dataset | Institución ficticia | Uso en el curso |
|---|---|---|
| `austral_*` | Banco Austral | Demostraciones en clase |
| `andes_*` | Financiera Andes | Laboratorios y proyecto |

Cuatro tablas por dataset: `clientes`, `solicitudes`, `comportamiento` (panel
mensual 2023-07 a 2026-06) y `bureau` (panel mensual). Detalle de columnas en
`diccionario_austral.md` y `diccionario_andes.md`.

## Carga rápida en Google Colab

```python
import pandas as pd
BASE = "https://raw.githubusercontent.com/nexolabs-gh/datos-riesgo-credito/main"
clientes = pd.read_parquet(f"{BASE}/andes_clientes.parquet")
```

© 2026 Academia Bayes · Solo uso educativo.
