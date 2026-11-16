# hackaton-nasa-2026-datos

Datos publicados por el equipo **AIVital** para NASA Space Apps Challenge 2026, desafío
[*Harmonization of MODIS and VIIRS Hot Spots*](https://www.spaceappschallenge.org/2026/challenges/modis-and-viirs-hot-spots/).

Este repo **solo contiene archivos generados**: una serie armonizada de focos de calor MODIS y VIIRS por comuna de
Chile, con su calendario mensual de actividad de quema. El código que los genera está en [hackaton-nasa-2026-back](https://github.com/marcelo-corro/hackaton-nasa-2026-back).
**No editar a mano:** se regeneran y publican desde el back.

**URL base:** https://marcelo-corro.github.io/hackaton-nasa-2026-datos

> **Estado actual: datos reales de las 345 comunas de Chile** (contrato v0.2, `"ejemplo": false`).
> - **Serie armonizada** MODIS/VIIRS de noviembre de 2000 a diciembre de 2025, método
>   `factor_unico_snpp_2012-2017_v1`, en focos equivalentes MODIS.
> - **Generada el 2026-11-14** (`generado_utc` en `manifest.json`).
> - **El riesgo es para el 2026-01-01** (a 24 h): los datos llegan hasta el 31-12-2025, así que es el último día
>   que se puede pronosticar con ellos. No es un pronóstico en tiempo real.
> - El modelo (`hgb_firms_v1`) se probó en 2022-2025; sus métricas están en `metricas.json`.

## Archivos

| Ruta | Contenido |
|---|---|
| `/manifest.json` | Versión del contrato, fecha de generación, período y lista de comunas |
| `/regiones.geojson` | Contornos simplificados de las comunas (WGS84) |
| `/calendario/{region_id}.json` | Matriz mes × año: focos MODIS, VIIRS, serie armonizada con incertidumbre, mediana histórica, percentil y nivel |
| `/riesgo/ultimo.json` | Riesgo de focos para mañana por comuna |
| `/focos/{region_id}.csv` | Focos de la comuna, para descargar |
| `/metricas.json` | Desempeño del modelo de riesgo |

`region_id` es el código único territorial de la comuna, como texto de 5 dígitos (`"05109"` = Viña del Mar).

## Fuentes

- **NASA FIRMS.** We acknowledge the use of data and/or imagery from NASA's Fire Information for Resource
  Management System (FIRMS) (https://earthdata.nasa.gov/firms), part of NASA's Land, Atmosphere Near real-time
  Capability for Earth observations (LANCE) (https://earthdata.nasa.gov/lance) and NASA's Earth Science Data and
  Information System (ESDIS).
  - Giglio, L., Schroeder, W., & Justice, C. O. (2016). The collection 6 MODIS active fire detection algorithm and
    fire products. *Remote Sensing of Environment*, 178, 31-41. https://doi.org/10.1016/j.rse.2016.02.054
  - Schroeder, W., Oliva, P., Giglio, L., & Csiszar, I. A. (2014). The New VIIRS 375m active fire detection data
    product: algorithm description and initial assessment. *Remote Sensing of Environment*, 143, 85-96.
    https://doi.org/10.1016/j.rse.2013.12.008
- **Límites comunales:** Biblioteca del Congreso Nacional de Chile, *División comunal: polígonos de las comunas de
  Chile*, https://www.bcn.cl/siit/mapas_vectoriales. Material referencial.

## English

Data files published by team AIVital (NASA Space Apps 2026) for the MODIS/VIIRS hotspot harmonization challenge:
a harmonized monthly hotspot series and burning-activity calendar for each of Chile's communes. Generated
files only; do not edit by hand. Base URL above. Currently **example data** (same structure, made-up numbers).
