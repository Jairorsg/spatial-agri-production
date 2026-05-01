# Agrospatial-ML descubrimiento de microclimas y predicción de rendimientos mediante inteligencia artificial

[![Python](https://img.shields.io/badge/Python-3.14-blue.svg)](https://www.python.org/)
[![Framework](https://img.shields.io/badge/Framework-Scikit--Learn-orange.svg)](https://scikit-learn.org/)
[![Spatials](https://img.shields.io/badge/Geo-GeoPandas-green.svg)](https://geopandas.org/)
[![Deployment](https://img.shields.io/badge/Deployment-Streamlit-FF4B4B.svg)](https://streamlit.io/)

Framework analítico basado en **Machine Learning espacial** para cuantificar la vulnerabilidad del sector agrícola en la región Puno, Perú, ante perturbaciones climáticas extremas como el fenómeno de del Niño.

## Executive summary

Este proyecto implementa un pipeline integral de Ciencia de Datos para transformar datos meteorológicos satelitales en crudo en *insights* de decisión económica[cite: 1]. A través de algoritmos de clustering y regresión, el modelo demuestra que los impactos climáticos no son uniformes, permitiendo una focalización estratégica de recursos y seguros agrarios[cite: 1, 2].

## Analytical pipeline

### 1. Data engineering & integration
* **Remote Sensing:** Ingesta de datos en tiempo real mediante la **API NASA POWER** (temperatura, precipitación, humedad relativa)[cite: 1].
* **Vector Data:** Procesamiento de cartografía provincial del INEI 2023 con `GeoPandas`[cite: 1].
* **Normalization:** Estandarización de rendimientos históricos (Ton/Ha) del MINAGRI[cite: 1].

### 2. Unsupervised learning: Microclimate discovery
Se aplicó el algoritmo **K-Means** para segmentar la región en 3 zonas agroclimáticas latentes, validadas mediante el **coeficiente de silhouette (0.466)** y el método del Codo[cite: 1, 2]. Esta técnica permite una gestión del riesgo basada en ecosistemas reales y no en divisiones administrativas arbitrarias[cite: 2].

### 3. Predictive modeling & Validation
Entrenamiento de un **Random Forest Regressor** (500 estimadores) bajo un esquema de validación **Leave-One-Out (LOO-CV)**[cite: 2].
* **Generalización:** RMSE de 0.233 T/Ha, garantizando robustez ante la restricción del tamaño muestral ($n=13$ provincias)[cite: 2].
* **Auditoría de Datos:** Identificación de provincias atípicas mediante **Isolation Forest** (Contaminación: 0.15)[cite: 2].

## Results & Simulation

Sometimos el modelo a un escenario de **shock climático** (el Niño): $+2 ^\circ\text{C}$ de temperatura y $-30\%$ de precipitación[cite: 2].

### Critical insights
* **Vulnerabilidad crítica:** La provincia de **Azángaro** presenta el mayor riesgo relativo, con una caída proyectada del **-9.2%** en el rendimiento[cite: 2].
* **Asimetría de impacto:** Zonas de ceja de selva (Sandia) muestran resiliencia, evidenciando que la reducción de humedad puede ser beneficiosa en ecosistemas saturados[cite: 2].
* **Feature Importance:** La **precipitación anual** se consolida como el predictor de mayor peso estructural en la varianza del rendimiento agrícola[cite: 2].

## Visualization & Deployment

El proyecto incluye capas de visualización avanzada para comunicación de resultados:
* **Interactive Maps:** Visualización de dispersión geoespacial con `Plotly Mapbox`.
* **3D Geospatial Modeling:** Renderizado de cilindros de rendimiento y semáforos de riesgo con `PyDeck` (CartoDB Style).
* **Exploratory Data Analysis:** Reportes técnicos generados con `Matplotlib` y `Seaborn`.

## Public policy implications

1. **Focalización del seguro agrario:** Orientación de subsidios hacia el núcleo de vulnerabilidad detectado en el corredor Azángaro-Lampa[cite: 2].
2. **Infraestructura estratégica:** Evidencia técnica para la priorización de proyectos de riego tecnificado en zonas con mayor sensibilidad hídrica[cite: 1, 2].

---
**Author:** Jairo Roberto Sequeiros Gallegos  
**Status:** Estudiante de ingenieria economica | Universidad Nacional del Altiplano  
**Topic:** Data Science, Spatial Econometrics, AgriTech
