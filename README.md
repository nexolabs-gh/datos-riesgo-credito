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

## Generación B (desde septiembre 2026)

La carpeta `generacion_b/` reúne, bajo una sola URL base, las cuatro tablas crudas y las tablas
intermedias que usa cada clase (por ejemplo `austral_poblacion`: una fila por solicitud con su
target y su motivo de exclusión, y `austral_matriz_modelable`: las 108 variables candidatas).
Los archivos de la raíz no cambian.

```python
import pandas as pd
BASE = "https://raw.githubusercontent.com/nexolabs-gh/datos-riesgo-credito/main/generacion_b"
poblacion = pd.read_parquet(f"{BASE}/austral_poblacion.parquet")
```

© 2026 Academia Bayes · Solo uso educativo.
