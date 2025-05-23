# 🚀 Proyecto Júpiter: Reconocimiento de Emociones (PontiaWorld)

[![GitHub - Language](https://img.shields.io/github/languages/top/Xara-cio/Proyecto-Jupiter-Reconocimiento-de-emociones?style=flat-square)](https://github.com/Xara-cio/Proyecto-Jupiter-Reconocimiento-de-emociones)
[![GitHub - Last Commit](https://img.shields.io/github/last-commit/Xara-cio/Proyecto-Jupiter-Reconocimiento-de-emociones?style=flat-square)](https://github.com/Xara-cio/Proyecto-Jupiter-Reconocimiento-de-emociones/commits/main)
[![Git LFS](https://img.shields.io/badge/LFS-Used-blue?style=flat-square)](https://git-lfs.github.com/)

Este proyecto aborda el **reconocimiento de emociones** en el contexto del parque de atracciones **PontiaWorld**, utilizando técnicas de **Machine Learning** y **Deep Learning**. Además, se integra una innovadora herramienta de **Inteligencia Artificial Generativa** para optimizar la experiencia y las operaciones internas.

---

## 1. ✨ Introducción

El **Proyecto Júpiter** es una iniciativa de análisis de datos y desarrollo de IA, enfocada en mejorar la experiencia del visitante y la eficiencia operativa en PontiaWorld.

### 1.1. 👨‍💻 Equipo del Proyecto

Este proyecto es el resultado de un esfuerzo colaborativo, con decisiones consensuadas y un enfoque multidisciplinar.

* **Ana:** 📊 Limpieza, transformación y resultados de `Procedencia` y `Tickets`. Creación de BBDD, preguntas de negocio, Modelo ML DL CNN y Dashboard PBI.
* **Leticia:** 📝 Limpieza, transformación y resultados de `Emociones`. Modelo ML XGBOOST, Herramienta de IA y presentación PPT.
* **Sara:** 🎢 Limpieza, transformación y resultados de `Atracciones`. Creación y conexión BBDD con Python, Dashboard PBI y Modelo ML-KNN. Herramienta IA.
* **Cristopher:** 📈 Limpieza, transformación y resultados de `Valoraciones`. Creación diagrama E-R y Modelo ML.
* **Irene:** ⏱️ Limpieza, transformación y resultados de `Duración`. Modelo ML.

### 1.2. 🎯 Objetivos Principales

* Diseño e implementación de un **modelo de datos relacional**.
* Identificación de **patrones de errores e incidencias** en los datos.
* Cálculo y visualización de **KPIs útiles para el negocio**.
* **Automatización de la detección de emociones**.
* Propuesta de **soluciones de IA Generativa** para optimizar procesos.

---

## 2. 🗄️ Modelo Relacional

Diseño de una base de datos relacional a partir de seis CSV (`entradas`, `atracciones`, `emociones`, `duración`, `procedencia`, `valoraciones`), modelados como tablas individuales.

La tabla central es **`emoción`** (`t_id` como PK), con `t_id` como FK en el resto de tablas. Se incorporó una clave primaria interna autoincremental (`*_id`) para unicidad y trazabilidad. La arquitectura permite consultas eficientes y la conexión Python automatiza análisis avanzados.

*(Veáse imagen Diagrama en Informe , archivo word subido a la plataforma Pontia como entregable)*

---

## 3. 🧹 Limpieza de Datos

Se aplicaron criterios generales y específicos para garantizar la calidad y coherencia de los datos.

### Consideraciones Generales:

* **`Id_visitante`**: Extracción de información de JSON anidado.
* **Registros duplicados**: Eliminación por `t_id` para asegurar unicidad.
* **`t_id`**: Separación del valor previo al guión bajo para clasificación (Training, Testing).

### Condiciones Específicas por Conjunto de Datos:

* **Emociones:** Emociones no detectadas imputadas a **"neutral"**.
* **Atracciones:** Tratamiento de valores negativos en `comienzo_atracción` (pruebas pre-apertura) y valores vacíos. `tiempo_espera` negativo imputado a `0`.
* **Tickets:** Asunción de múltiples tipos de entradas por visitante en el mismo mes.
* **Procedencia:** Creación de `procedencia_frecuente` para usuarios con múltiples orígenes.
* **Valoraciones:** Normalización al rango `[0, 10]`, corrigiendo valores atípicos.
* **Duración:** Eliminación de columnas irrelevantes, tratamiento de nulos, codificación de categóricas y ajuste de formatos de tiempo. Imputación de valores atípicos.

---

## 4. 🧠 Metodología de Machine Learning (ML)

Exploración y entrenamiento de diversos modelos para el reconocimiento de emociones:

* **DL CNN (Deep Learning - Redes Convolucionales):** 🖼️ Especializadas en procesamiento de imágenes para predicción de emociones.
* **KNN (K-Nearest Neighbors):** 🫂 Clasificación de imágenes usando características de MobileNetV2 y ResNet50.
* **RF (Random Forest):** 🌳 Modelos en dos enfoques: con datos tabulares y extrayendo características de imágenes mediante **HOC** para clasificación.
* **XGBoost (Extreme Gradient Boosting):** 🚀 Eficiente para clasificación multiclase en datos tabulares, combinando información tabular con imágenes vectorizadas.

---

## 5. 📊 Comparación de Modelos

| Modelo              | Precisión                                                                                                    | Pérdida                                |
| :------------------ | :----------------------------------------------------------------------------------------------------------- | :------------------------------------- |
| **CNN** | F1 Score (macro): 0.61 <br> Precisión (macro): 0.64 <br> Recall (macro): 0.60 <br> Accuracy: 0.65               | val_loss: 0.97                         |
| **KNN ResNet50** | F1 Score (macro): 0.41 <br> Precisión (macro): 0.44 <br> Recall (macro): 0.40 <br> Accuracy: 0.45               | Log Loss: 4.47 <br> MSE: 0.085         |
| **HOC-RF** | F1 Score (macro): 0.4387 <br> Precisión (macro): 0.5796 <br> Recall (macro): 0.4137 <br> Accuracy: 0.4763       | Log Loss: 1.45                         |
| **XGBoost** | F1 Score (macro): 0.3274 <br> Precisión (macro): 0.3919 <br> Recall (macro): 0.3335 <br> Accuracy: 0.3565       | Log Loss: 2.6280                       |

### Conclusiones y Posibles Mejoras:

* **Confusión entre emociones** debido a la similitud facial y posible baja calidad de imagen.
* Mejorar la **calidad de las cámaras**.
* Reducir a **3 clases** (`positiva`, `neutral`, `negativa`) en lugar de 7 para simplificar y mejorar la precisión.

---

## 6. 🤖 Herramienta de Inteligencia Artificial Integrada

Una solución de IA Generativa con dos funcionalidades principales, apoyadas en el mismo flujo de preprocesado de datos:

* **Sistema Conversacional:** 💬 Permite consultas en lenguaje natural sobre datos del parque (GPT-4o conectado a scripts Python para filtrar y responder).
* **Generación de Contenido para Redes Sociales:** ✍️ Crea textos personalizados a partir de emociones detectadas, optimizando el trabajo de comunicación.

### Beneficios Comunes:

* **Automatización de tareas repetitivas.**
* **Acceso ágil a información relevante.**
* **Mejora de la eficiencia operativa y comunicativa.**

---

## 🔗 Acceso al Proyecto

* **Repositorio GitHub:** [https://github.com/Xara-cio/Proyecto-Jupiter-Reconocimiento-de-emociones](https://github.com/Xara-cio/Proyecto-Jupiter-Reconocimiento-de-emociones)
* **Archivos grandes (Data y Modelos):** [https://drive.google.com/drive/folders/1XUOeHuKz-iecvuudFOiYwJpXJKhbQ1Li?usp=drive_link](https://drive.com/drive/folders/1XUOeHuKz-iecvuudFOiYwJpXJKhbQ1Li?usp=drive_link)

---
