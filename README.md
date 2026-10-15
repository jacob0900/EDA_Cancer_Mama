# EDA: cáncer de mama

Análisis exploratorio de datos (EDA) sobre el diagnóstico de tumores de mama como **benignos (B)** o **malignos (M)**, a partir de mediciones de núcleos celulares. Es un trabajo de curso escrito en R Markdown y publicado como libro con **bookdown**.

**Ver el informe:** https://jacob0900.github.io/EDA_Cancer_Mama/

## Datos

- **Dataset:** [Breast Cancer Wisconsin (Diagnostic)](https://archive.ics.uci.edu/dataset/17/breast+cancer+wisconsin+diagnostic), del UCI Machine Learning Repository.
- **Tamaño:** 569 pacientes. La variable objetivo es `Diagnosis` (B/M).
- **Archivo:** `wdbc.csv`, incluido en el repositorio. El informe lo lee directamente desde GitHub, así que no hace falta descargarlo aparte.

El dataset original tiene 30 variables numéricas: diez características del núcleo (radio, textura, perímetro, área, suavidad, compacidad, concavidad, puntos cóncavos, simetría y dimensión fractal), cada una medida como media, error estándar y valor máximo. En el análisis se usan las 10 medias como variables representativas.

## Contenido del informe

1. **Carga de datos** y descripción de las variables
2. **Exploración inicial:** estructura y dimensión del dataset
3. **Limpieza y optimización:** reducción de 30 a 10 variables, revisión de valores faltantes y tratamiento de valores atípicos con transformación logarítmica
4. **Análisis univariante** de variables numéricas y categóricas
5. **Análisis bivariante:** numérica vs. categórica, numérica vs. numérica (matriz de correlación) y categórica vs. categórica (heatmap)
6. **Análisis multivariante** de radio, textura y perímetro
7. **Conclusiones**
8. **Posibles formas de proceder:** preparación para modelado, modelos de clasificación y validación

## Principales resultados

- El dataset no tiene valores faltantes.
- El 62,7 % de los tumores son benignos y el 37,3 % malignos.
- Los tumores malignos tienen radios mayores y más variabilidad; los benignos tienen una distribución más compacta.
- El radio y el perímetro están casi perfectamente correlacionados (r ≈ 0,998). La textura casi no se correlaciona con las demás variables.
- Como siguiente paso se proponen modelos de clasificación como regresión logística, Random Forest, SVM, redes neuronales y XGBoost.

## Estructura del repositorio

```
EDA_Cancer_Mama/
├── index.Rmd            # informe principal
├── JCOBO.Rmd            # borradores de cada integrante
├── chamorro.Rmd
├── Jesu.Rmd
├── wdbc.csv             # datos
├── _bookdown.yml        # configuración del libro
├── _output.yml
├── docs/                # sitio generado (GitHub Pages)
└── bookdown-demo.Rproj  # proyecto de RStudio
```

## Cómo generarlo

Requisitos: R y RStudio.

1. Abre `bookdown-demo.Rproj` en RStudio.
2. Instala los paquetes:

   ```r
   install.packages(c("bookdown", "knitr", "kableExtra", "dplyr", "ggplot2", "readxl",
                      "tibble", "readr", "Amelia", "reshape2", "gridExtra", "GGally",
                      "patchwork"))
   ```

3. Genera el libro:

   ```r
   bookdown::render_book("index.Rmd", "bookdown::gitbook")
   ```

   El resultado queda en `docs/`, que es la carpeta que publica GitHub Pages.

## Autores

- Jacobo Londoño
- Jesús David Barrios Valdés
- Samuel Chamorro

## Licencia

[CC0 1.0 Universal](LICENSE)
