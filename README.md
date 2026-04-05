# Proyecto Movilidad - Moira Bittner

Proyecto del Taller Práctico de **Programación para la Ciencia de Datos**.

El objetivo es transformar el dataset crudo [Global Mobility Report](https://www.google.com/covid19/mobility/) en un reporte limpio y profesional, aplicando un flujo completo de ciencia de datos: limpieza, transformación, visualización y versionado con Git.

## Dataset

- **Fuente**: Google COVID-19 Community Mobility Reports
- **Archivo**: `Global_Mobility_Report.csv`
- **País analizado**: Chile
- **Período**: Febrero 2020 - Octubre 2022
- **Registros de Chile**: 68,716 filas

## Fases del Proyecto

### Fase 2: Limpieza de Datos

Se trabajó con el dataset filtrado para Chile, aplicando las siguientes técnicas:

- **Filtrado** de datos solo para Chile (`country_region == "Chile"`)
- **Eliminación de columnas** vacías o redundantes (`metro_area`, `census_fips_code`, `iso_3166_2_code`)
- **Imputación de nulos** en columnas geográficas (`sub_region_1` → `"Nacional"`, `sub_region_2` → `"Sin especificar"`)
- **Imputación con mediana** en columnas de movilidad (robusta ante outliers)
- **Verificación de duplicados** por fecha y subregión
- **Corrección de outliers** con `.loc[]` reemplazando valores fuera del rango `[-100, 200]`

### Fase 3: Transformación Avanzada (Feature Engineering)

Se prepararon los datos para análisis profesional:

- **Tipado**: Conversión de `date` a `datetime` con `pd.to_datetime()`
- **Ingeniería de features**: Creación de `movilidad_promedio` (promedio de las 6 categorías de movilidad)
- **Escalamiento**: Normalización con `MinMaxScaler` al rango `[0, 1]`
- **Codificación**: `LabelEncoder` para subregiones
- **Pipeline**: `ColumnTransformer` con `StandardScaler` + `OneHotEncoder`

### Fase 4: Entrega y Reflexión

- **Visualización**: Gráfico `sns.lineplot` de la movilidad promedio nacional a lo largo del tiempo
- **Reflexión**: Análisis de las decisiones de limpieza y la importancia de Git en el proceso
- **Entrega**: Push final del notebook documentado a GitHub

## Tecnologías Utilizadas

- Python 3
- Google Colab (Jupyter Notebook)
- Pandas
- NumPy
- Scikit-learn
- Matplotlib
- Seaborn
- Git / GitHub

## Cómo Ejecutar

1. Clonar el repositorio
2. Colocar `Global_Mobility_Report.csv` en la carpeta del proyecto
3. Abrir `Proyecto_Movilidad.ipynb` en Jupyter Notebook
4. Ejecutar todas las celdas en orden