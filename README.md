# 🚗 GLM vs Machine Learning: Claim Frequency Modeling

<p align="center">
  <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white">
  <img src="https://img.shields.io/badge/Pandas-2C2D72?style=for-the-badge&logo=pandas&logoColor=white">
  <img src="https://img.shields.io/badge/Numpy-777BB4?style=for-the-badge&logo=numpy&logoColor=white">
  <img src="https://img.shields.io/badge/scikit_learn-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white">
  <img src="https://img.shields.io/badge/statsmodels-3776AB?style=for-the-badge&logo=python&logoColor=white">
  <img src="https://img.shields.io/badge/Jupyter-F37626.svg?&style=for-the-badge&logo=Jupyter&logoColor=white">
</p>

<p align="center">
  <img src="https://img.shields.io/badge/status-completed-success?style=flat-square">
  <img src="https://img.shields.io/badge/dataset-freMTPL2-blue?style=flat-square">
  <img src="https://img.shields.io/badge/observations-679%2C513-orange?style=flat-square">
</p>

## Can Machine Learning replace Generalized Linear Models for predicting claim frequency?

Evidence from the French car insurance sector.

---

## 📋 Summary

This project tests if Machine Learning algorithms can actually replace Generalized Linear Models (GLMs), which are the standard tool used by insurance companies to predict how often people will file claims. Using the *freMTPL2* dataset, I compared three different approaches: **Poisson**, **Negative Binomial (NB2)**, and **Random Forest**.

## 🔬 Methodology

| Stage | What I did |
|---|---|
| 🧹 **Data Cleaning & Pipeline** | Wrote a custom `Cleaning` class to drop columns that cause data leakage and fix skewed variables. This is wrapped in a `ColumnTransformer` to handle missing values, scaling, and one-hot encoding automatically. |
| 📐 **Statistical Models** | Poisson and NB2 fitted using maximum likelihood. I built them from scratch and validated them against `statsmodels`. |
| 🤖 **Machine Learning** | Random Forest trained on claim frequency, with corrections to fix overfitting and exposure bias. |
| 📊 **Evaluation** | Deviance, MAE, $R^2$ (Tweedie), and the predicted vs actual ratio. |
| 🔍 **Interpretability** | Compared the GLM coefficients directly against the Random Forest feature importance. |

## 📈 Key Results

| Metric | Poisson | NB2 | Random Forest |
|---|---|---|---|
| AIC | 249,724 | **244,839** | — |
| Deviance (test) | — | 0.350 | **0.326** |
| R^2 (Tweedie) | — | 0.007 | **0.075** |
| Pred/Actual Ratio | — | 1.037 | **1.003** |

After testing, the Machine Learning algorithm didn't show a huge predictive advantage that would justify throwing away GLMs completely. GLMs are still better because their coefficients are directly interpretable, which is a must-have when you need to justify premium prices to regulators and clients. 

However, Random Forest shouldn't be tossed aside either. It works great as a diagnostic tool to spot non-linear variables (like vehicle age). It basically tells you exactly where your traditional GLM needs extra math transformations to price risk better.

## Author: David Sebastián Rodríguez Guzmán

> 🌐 **[Read the English version above]**

---

## Versión en Español

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

Evidencia desde el sector asegurador de automóviles francés

---

## 📋 Resumen

Este proyecto evalúa si los algoritmos de Machine Learning pueden sustituir a los Modelos Lineales 
Generalizados (GLM) los cuales son el estandar general y normativo para el modelado de frecuencia de siniestros automotrices. Usando el dataset 
*French Motor Third-Party Liability Claims* (freMTPL2), se comparan tres enfoques bajo la misma 
metodología de evaluación: **Poisson**, **Binomial Negativa (NB2)** y **Random Forest Regressor**.

## 🔬 Metodología

| Etapa | Qué se hizo |
|---|---|
| 🧹 **Limpieza y pipeline** | Clase `Cleaning` personalizada que elimina columnas con fuga de datos y transforma variables sesgadas, integrada en un `ColumnTransformer` reproducible con imputación, escalado y codificación one-hot para variables numéricas y categóricas |
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

Para el modelado de frecuencia de siniestros, el algoritmo de Machine Learning que utilicé no demuestra una ventaja predictiva lo suficientemente abrumadora que justifique el reemplazo total de los Modelos Lineales Generalizados(GLM). Los GLM siguen siendo superiores gracias a que sus coeficientes son directamente interpretables, lo cual es vital para justificar el cálculo de primas ante entes reguladores y clientes.  No obstante, herramientas como Random Forest no deben descartarse; fungen como excelentes recursos de diagnóstico para detectar variables con comportamiento no lineal (como VehAge), indicando dónde los GLM tradicionales necesitan transformaciones matemáticas adicionales para perfeccionar la tarificación del riesgo. 

## Autor: David Sebastián Rodríguez Guzmán
