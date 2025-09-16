# Docker

# Título del Informe
> _Resumen en 1–3 líneas sobre el objetivo y el resultado principal._

[![Estado del build](https://img.shields.io/badge/build-passing-brightgreen)](#)
[![Licencia](https://img.shields.io/badge/licencia-MIT-blue)](LICENSE)

## Tabla de contenidos
- [Objetivos](#objetivos)
- [Alcance](#alcance)
- [Metodología](#metodología)
- [Datos](#datos)
- [Resultados](#resultados)
- [Análisis](#análisis)
- [Conclusiones](#conclusiones)
- [Recomendaciones](#recomendaciones)
- [Trabajo futuro](#trabajo-futuro)
- [Evidencias](#evidencias)
- [Anexos](#anexos)

## Objetivos
- Objetivo 1
- Objetivo 2

## Alcance
- Lo que **sí** cubre.
- Lo que **no** cubre.

## Metodología
1. Paso 1
2. Paso 2
3. Paso 3

> [!NOTE]
> Usa blockquotes con admonitions como NOTE/TIP/IMPORTANT/CAUTION/WARNING para llamar la atención.

## Datos
| Fuente | Descripción | Formato | Tamaño |
|---|---|---:|---:|
| `data/dataset.csv` | Registros de X | CSV | 12 MB |
| API Foo | Métricas en tiempo real | JSON | — |

- Variables clave: `fecha`, `id`, `monto`, `categoria`.[^diccionario]
- Limpieza: outliers, faltantes, codificación UTF-8.

## Resultados
- **Métrica A**: 98.7%
- **Métrica B**: 1234 items

```bash
# Reproducir localmente (ejemplo)
python -m venv .venv
source .venv/bin/activate  # Windows: .venv\Scripts\activate
pip install -r requirements.txt
python scripts/generar_reporte.py
