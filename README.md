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
- **NASA POWER** (clima por comuna): The data was obtained from National Aeronautics and Space Administration (NASA)
  Langley Research Center's Prediction Of Worldwide Energy Resources (POWER) project funded through the NASA Earth
  Science Division. Versión Daily 2.10.3.
- **Sectores de la Región de Valparaíso:**
  - Zanaga, D. et al. (2022). *ESA WorldCover 10 m 2021 v200*. Zenodo. https://doi.org/10.5281/zenodo.7254221
    (CC BY 4.0).
  - Schug, F. et al. (2023). The global wildland–urban interface. *Nature*.
    https://doi.org/10.1038/s41586-023-06320-0 (CC BY 4.0).
  - Copernicus DEM: "produced using Copernicus WorldDEM-30 © DLR e.V. 2010-2014 and © Airbus Defence and Space
    GmbH 2014-2018 provided under COPERNICUS by the European Union and ESA; all rights reserved".
  - Caminos: © colaboradores de OpenStreetMap (ODbL). Se usan solo como variable del modelo; no se publican.
- **Recomendaciones:** cada texto cita el documento oficial del que sale (nombre y enlace en `fuentes` de
  `recomendaciones.json`).

El detalle de cada fuente, con su verificación, está en
[docs/fuentes.md](https://github.com/marcelo-corro/hackaton-nasa-2026-back/blob/main/docs/fuentes.md) del back.

## Equipo

Proyecto del NASA Space Apps Challenge 2026 (sede Santiago), desafío *Harmonization of MODIS and VIIRS Hot Spots*.
Por orden alfabético de apellido:

| Integrante | Rol | GitHub |
|---|---|---|
| Marcelo Corro | Software y datos · coordinación técnica | [marcelo-corro](https://github.com/marcelo-corro) |
| José De Los Santos | Interfaz y presentación | [RemLover68](https://github.com/RemLover68) |
| Katherine González | Investigación | — |
| Sebastián Ríos | Investigación | — |
| David Serrudo | Software y datos | [Daavidasc](https://github.com/Daavidasc) |

| Área | Integrantes |
|---|---|
| Datos y modelos (back) | Marcelo Corro, David Serrudo |
| Sitio web (front) | Marcelo Corro, David Serrudo, José De Los Santos |
| Investigación (fuentes de datos y respaldo de las recomendaciones) | Katherine González, Sebastián Ríos |
| Presentación | José De Los Santos |

Los roles no son fijos: cada integrante puede sumarse a otras áreas para aprender y aportar. El detalle de cada
cambio al código está en el historial de commits del
[back](https://github.com/marcelo-corro/hackaton-nasa-2026-back/graphs/contributors). Más sobre el equipo y la
historia del proyecto en [Quiénes somos](https://marcelo-corro.github.io/hackaton-nasa-2026-front/beta/quienes-somos).

## Licencia

Los archivos que genera Preaviso están bajo [CC BY 4.0](LICENSE), con «Copyright (c) 2026 Los autores de
Preaviso» (las personas de la sección [Equipo](#equipo) y quienes se sumen después). Se pueden usar para cualquier
fin citando «Preaviso, proyecto del NASA Space Apps Challenge 2026». Los datos de terceros conservan sus
condiciones (ver [Fuentes](#fuentes)).

## English

Data files published by team AIVital (NASA Space Apps 2026) for the MODIS/VIIRS hotspot harmonization challenge:
a harmonized monthly hotspot series and burning-activity calendar for each of Chile's communes. Generated
files only; do not edit by hand. Base URL above. Currently **example data** (same structure, made-up numbers).

**Team** (alphabetical by last name): Marcelo Corro (software and data, technical coordination), José De Los Santos
(interface and presentation), Katherine González (research), Sebastián Ríos (research) and David Serrudo (software
and data).

**License:** files generated by Preaviso are CC BY 4.0 (see [LICENSE](LICENSE)); third-party data keep their
own terms.
