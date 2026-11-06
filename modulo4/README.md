# Módulo 4: Análisis Espacial con QGIS

## Resumen del Proyecto

En este módulo se trabajó en el procesamiento y manejo de datos alfanuméricos y geográficos a través de Sistemas de Información Geográfica (SIG) en **QGIS**, junto con la integración de consultas espaciales.

El objetivo central es brindar al perfil de ingeniería industrial herramientas avanzadas de ingeniería de datos y análisis territorial para optimizar la toma de decisiones logísticas y de localización.

## Actividad 1: Red logística de fábricas conserveras y empacadoras de fruta en Mendoza

Se analizó la distribución espacial de 16 plantas procesadoras y empacadoras de fruta en el **Gran Mendoza y Zona Este** (Guaymallén, Maipú, Luján de Cuyo y San Martín). Se tuvieron en cuenta el empleo, la capacidad de procesamiento en toneladas, la superficie de los predios y el impacto hídrico de cada una.

### Metodología

1. **Capas vectoriales y ráster:** puntos de fábricas conserveras importados desde `.csv`, polígonos de predios digitalizados y un mapa de zonas agrícolas georreferenciado.
2. **Edición de atributos:** se calcularon `Ha = $area / 10000` e `Imp_hidric`, que vale `Bajo` para menos de 30 ha, `Medio` para 30–100 ha y `Alto` para 100 ha o más. Todo se trabajó en **EPSG:32719 (UTM 19S)**.
3. **Análisis espacial:**
   - **Polígonos de Voronoi:** zona de acopio y abastecimiento de materia prima de cada fábrica.
   - **Triangulación de Delaunay:** red de vecindad para la logística de transporte interplanta.
4. **Exportación web:** con `qgis2web` (OpenLayers), en un mapa que permite activar y desactivar capas.

### Resultados

| Indicador | Valor |
| --- | --- |
| Mayor zona de influencia (Voronoi) | Frutas Seleccionadas Russell – 38.641 ha |
| Menor zona de influencia (Voronoi) | AgroPlanta Luján – 2.125 ha |
| Finca de mayor superficie | Finca 5 – 106,3 ha |
| Impacto hídrico (Bajo / Medio / Alto) | 13 / 2 / 1 |
| Triángulos de Delaunay | 24 |

Las plantas empacadoras de Guaymallén y Maipú están a menos de 4 km entre sí, así que comparten zonas de abastecimiento chicas y compiten por la misma materia prima. San Martín y Luján de Cuyo, más dispersos, duplican en promedio el área de cobertura respecto al área metropolitana.

*Empleados y capacidad son valores estimados con fines didácticos.*

🌐 Mapa Web Interactivo

👉 [Ver Mapa Interactivo de Fábricas Conserveras de Mendoza](https://julivalle1.github.io/Tecnicas-y-Herramientas-II/M%C3%B3dulo_4/qgis2web_2026_11_06-15_16_09_364076/index.html)

## Actividad 2: Nieve en el Valle de las Lágrimas

Se comparó la superficie cubierta por nieve en el sector cordillerano de Mendoza que incluye el **Valle de las Lágrimas** (Malargüe), en dos fechas de la misma época del año: **24/10/2024** y **27/10/2026**.

### Metodología

1. **Imágenes ráster:** dos GeoTIFF descargados de NASA Worldview[cite: 20].
2. **Proyección:** se pasó de EPSG:4326 (grados) a **EPSG:32719 (UTM 19S, metros)** para medir las áreas sin distorsión.
3. **Vectorización:** se digitalizaron las masas de nieve de cada fecha en dos capas, `vieja_poligono` y `actual_poligono`.
4. **Cálculo de superficies:** con la Calculadora de Campos, `$area / 10000`, para obtener hectáreas.

### Resultados

| Fecha | Superficie nevada (ha) |
| --- | --- |
| 24/10/2024 | 2.916.618,21 |
| 27/10/2026 | 3.662.147,07 |
| **Variación** | **+745.528,86 ha (+25,6 %)** |

La cobertura de nieve de 2026 fue un 25,6 % mayor. Coincide con la nevada histórica de julio de 2026 en Malargüe ([Los Andes](https://www.losandes.com.ar/)).

🌐 **Mapa Web Interactivo**

👉 [Ver Mapa Interactivo del Valle de las Lágrimas](https://julivalle1.github.io/Tecnicas-y-Herramientas-II/M%C3%B3dulo_4/qgis2web_2026_11_06-17_19_33_593044/index.html)


### 📥 Descargas

* [Descarga aquí el paquete de la Actividad 1 (.zip)](./qgis2web_2026_11_06-15_16_09_364076.zip)
* [Descarga aquí el paquete de la Actividad 2 (.zip)](./qgis2web_2026_11_06-17_19_33_593044.zip)
