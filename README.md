# 🚗 GLM vs Machine Learning: Modelado de Frecuencia de Siniestros

<p align="center">
  <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white">
  <img src="https://img.shields.io/badge/Pandas-2C2D72?style=for-the-badge&logo=pandas&logoColor=white">
  <img src="https://img.shields.io/badge/Numpy-777BB4?style=for-the-badge&logo=numpy&logoColor=white">
  <img src="https://img.shields.io/badge/scikit_learn-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white">
  <img src="https://img.shields.io/badge/statsmodels-3776AB?style=for-the-badge&logo=python&logoColor=white">
  <img src="https://img.shields.io/badge/Jupyter-F37626.svg?&style=for-the-badge&logo=Jupyter&logoColor=white">
</p>

<p align="center">
  <img src="https://img.shields.io/badge/status-completado-success?style=flat-square">
  <img src="https://img.shields.io/badge/dataset-freMTPL2-blue?style=flat-square">
  <img src="https://img.shields.io/badge/observaciones-679%2C513-orange?style=flat-square">
</p>

## ¿Pueden los algoritmos de Machine Learning sustituir a los Modelos Lineales Generalizados en el modelado de frecuencia de siniestros?

Evidencia desde el sector asegurador de automóviles francés 🇫🇷

---

## 📋 Resumen

Este proyecto evalúa si los algoritmos de Machine Learning pueden sustituir a los Modelos Lineales 
Generalizados (GLM) los cuales son el estandar general y normativo para el modelado de frecuencia de siniestros automotrices. Usando el dataset 
*French Motor Third-Party Liability Claims* (freMTPL2), se comparan tres enfoques bajo la misma 
metodología de evaluación: **Poisson**, **Binomial Negativa (NB2)** y **Random Forest Regressor**.

## 🔬 Metodología

| Etapa | Qué se hizo |
|---|---|
| 🧹 **Limpieza y pipeline** | `ColumnTransformer` reproducible para variables numéricas y categóricas |
| 📐 **Modelos estadísticos** | Poisson y NB2 ajustados por máxima verosimilitud (implementados desde cero y con `statsmodels`) |
| 🤖 **Machine Learning** | Random Forest entrenado sobre tasa de siniestralidad, corrigiendo sobreajuste y sesgo por exposición |
| 📊 **Evaluación** | Deviance, MAE, R² (Tweedie) y ratio predicho/real |
| 🔍 **Interpretabilidad** | Comparación de coeficientes del GLM vs feature importance de Random Forest |

## 📈 Resultados clave

| Métrica | Poisson | NB2 | Random Forest |
|---|---|---|---|
| AIC | 249,724 | **244,839** | — |
| Deviance (test) | — | 0.350 | **0.326** |
| R² (Tweedie) | — | 0.007 | **0.075** |
| Ratio pred/real | — | 1.037 | **1.003** |

Para el modelado de frecuencia de siniestros, El algoritmo de Machine Learning que utilic'e no demuestra una ventaja predictiva abrumadora que justifique el reemplazo total de los GLM. Los Modelos Lineales Generalizados siguen siendo superiores gracias a que sus coeficientes son directamente interpretables, lo cual es vital para justificar el cálculo de primas ante entes reguladores y clientes.  No obstante, herramientas como Random Forest no deben descartarse; fungen como excelentes recursos de diagnóstico para detectar variables con comportamiento no lineal (como VehAge), indicando dónde los GLM tradicionales necesitan transformaciones matemáticas adicionales para perfeccionar la tarificación del riesgo. 

Autor: David Sebastián Rodríguez Guzmán
