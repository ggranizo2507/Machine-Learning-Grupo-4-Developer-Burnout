# 🔥 Predicción del Agotamiento (Burnout) del Desarrollador | Clasificación y Regresión ML

![Python](https://img.shields.io/badge/Python-3.10+-blue?logo=python)
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-1.3+-orange?logo=scikit-learn)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?logo=jupyter)
![License](https://img.shields.io/badge/License-MIT-green)
![Status](https://img.shields.io/badge/Status-Completado-brightgreen)
![GitHub Notebook](https://img.shields.io/badge/GitHub-Notebook%20Renderizado-181717?logo=github)

[![Ver Notebook en GitHub](https://img.shields.io/badge/📊%20Ver%20Gráficos%20y%20Resultados-GitHub-181717?style=for-the-badge&logo=github)](https://github.com/ggranizo2507/Machine-Learning-Grupo-4-Developer-Burnout/blob/main/Prediccion_agotamiento_desarrollador_clasificacion_ML_S2.ipynb)
[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/ggranizo2507/Machine-Learning-Grupo-4-Developer-Burnout/blob/main/Prediccion_agotamiento_desarrollador_clasificacion_ML_S2.ipynb)

---

## 📌 Descripción del Problema

El **agotamiento laboral (burnout)** es uno de los problemas más críticos en la industria del software. Este proyecto adopta un **enfoque dual basado en datos** para analizar el burnout desde dos perspectivas complementarias:

| Enfoque | Variable objetivo | Tipo de problema |
|---------|:----------------:|:----------------:|
| **Clasificación** | `burnout_level` → `Low` / `Medium` / `High` | Clasificación multiclase |
| **Regresión** | `stress_level` → escala continua 0–100 | Regresión numérica |

> **Pregunta de investigación:** ¿Es posible predecir tanto la categoría de burnout como la intensidad del estrés de un desarrollador a partir de métricas de estilo de vida y trabajo?

---

## 📊 Ver Resultados y Gráficos

| Opción | Descripción | Enlace |
|--------|-------------|--------|
| 📊 **GitHub** | Visualiza el notebook completo con todos los gráficos — sin instalar nada | [Ver ahora](https://github.com/ggranizo2507/Machine-Learning-Grupo-4-Developer-Burnout/blob/main/Prediccion_agotamiento_desarrollador_clasificacion_ML_S2.ipynb) |
| ▶️ **Google Colab** | Ejecuta el notebook interactivamente en la nube | [Abrir en Colab](https://colab.research.google.com/github/ggranizo2507/Machine-Learning-Grupo-4-Developer-Burnout/blob/main/Prediccion_agotamiento_desarrollador_clasificacion_ML_S2.ipynb) |

### Gráficos incluidos en el notebook

| # | Gráfico | Sección |
|---|---------|---------|
| 1 | Distribución de clases de burnout | EDA |
| 2 | Mapa de calor de correlaciones | EDA |
| 3 | Análisis de outliers (boxplots) | EDA |
| 4 | Correlación de features con el target | Paso 5.1 |
| 5 | Curva ROC — Regresión Logística | Modelo 1 |
| 6 | Matriz de confusión — Regresión Logística | Modelo 1 |
| 7 | Curva de complejidad — Árbol de Decisión | Modelo 2 |
| 8 | Diagnóstico de overfitting (train vs test) | Modelo 2 |
| 9 | Visualización del árbol (3 niveles) | Modelo 2 |
| 10 | Feature Importance — Random Forest | Modelo 3 |
| 11 | Curva de convergencia — Gradient Boosting | Modelo 4 |
| 12 | Curva ROC comparativa (4 modelos) | Comparación |
| 13 | Heatmap de métricas de clasificación | Comparación |
| 14 | Heatmap AUC-ROC por clase | Comparación |
| 15 | F1-Score por fold (k=8) | Cross-Validation |
| 16 | Boxplot de estabilidad por modelo | Cross-Validation |
| 17 | Impacto de max_depth en F1 | Tuning |
| 18 | Real vs Predicho — 4 regresores | Regresión |
| 19 | Interpretación de residuos | Regresión |
| 20 | Comparación R² por modelo | Regresión |
| 21 | Curvas de aprendizaje — 4 regresores | Regresión |
| 22 | Resultados consolidados Clasificación + Regresión | Consolidado |
| 23 | Pipeline completo del proyecto | Pipeline |

---

## 🗂️ Estructura del Repositorio

```
Machine-Learning-Grupo-4-Developer-Burnout/
│
├── 📓 Prediccion_agotamiento_desarrollador_clasificacion_ML_S2.ipynb
│       Notebook principal — clasificación + regresión (85 celdas)
│
├── 📊 developer_burnout_dataset.csv
│       Dataset fuente (7,000 registros × 12 variables)
│
├── 📄 README.md
│       Este archivo
│
└── 📄 LICENSE
        Licencia MIT
```

---

## 📊 Dataset

| Característica | Detalle |
|----------------|---------|
| **Fuente** | [Kaggle — Developer Burnout Prediction Dataset](https://www.kaggle.com/datasets/asifxzaman/developer-burnout-prediction-dataset7000-samples) |
| **Registros totales** | 7,000 |
| **Registros válidos** | 6,972 (tras limpiar NaN en target) |
| **Variables** | 12 (11 features + 1 target) |
| **Tipo** | Dataset sintético generado artificialmente |

### Variables del dataset

| Variable | Tipo | Rango | Descripción |
|----------|------|-------|-------------|
| `age` | Numérica | 22–60 | Edad del desarrollador |
| `experience_years` | Numérica | 0–35 | Años de experiencia |
| `daily_work_hours` | Numérica | 4–16 | Horas de trabajo diarias |
| `sleep_hours` | Numérica | 3–10 | Horas de sueño por noche |
| `caffeine_intake` | Numérica | 0–600 | Consumo de cafeína (mg/día) |
| `bugs_per_day` | Numérica | 0–20 | Bugs reportados por día |
| `commits_per_day` | Numérica | 0–15 | Commits realizados por día |
| `meetings_per_day` | Numérica | 0–10 | Reuniones por día |
| `screen_time` | Numérica | 4–18 | Tiempo frente a pantalla (horas) |
| `exercise_hours` | Numérica | 0–10 | Horas de ejercicio por semana |
| `stress_level` | Numérica | 0–100 | Nivel de estrés (escala continua) |
| `burnout_level` | Categórica | Low/Medium/High | **Variable objetivo clasificación** |

---

## 🧠 Metodología

### Pipeline completo

```
Datos Crudos (7,000 registros)
    │
    ▼
1. Limpieza y preprocesamiento
   • Eliminación de NaN en variable objetivo (fix clase fantasma nan)
   • Imputación con mediana (SimpleImputer — fit solo en train)
   • Codificación de etiquetas (LabelEncoder)
   • Tratamiento de outliers (Winsorización IQR)
   • StandardScaler
    │
    ▼
2. Análisis Exploratorio (EDA)
   • Distribuciones, skewness, curtosis
   • Correlaciones y mapa de calor
   • Análisis de valores faltantes y outliers
    │
    ▼
3. Feature Engineering (8 variables nuevas)
   • work_to_sleep_ratio    • productivity_score
   • digital_overload       • recovery_index
   • meeting_burden         • stimulant_dependency
   • stress_load            • experience_stress_ratio
    │
    ▼
4. Análisis de correlación con el target
   • Detección de features con |corr| > 0.85 (infladas)
   • Exclusión justificada si aplica
    │
    ▼
5. PARTE 1 — Clasificación (burnout_level)
   • 4 modelos: LR, DT, RF, Gradient Boosting
   • Métricas: Accuracy, Precisión, Recall, F1, AUC-ROC
   • Curvas ROC comparativas + heatmap + barplot
   • StratifiedKFold k=8 + RandomizedSearchCV (100 fits)
   • Evaluación final en test set (una sola vez)
    │
    ▼
6. PARTE 2 — Regresión (stress_level)
   • 4 modelos: Ridge, RF Regressor, GB Regressor, SVR
   • Métricas: MAE, MSE, RMSE, R²
   • Real vs Predicho + Residuos
   • Curvas de aprendizaje por modelo
    │
    ▼
7. Resultados consolidados + Pipeline completo
```

---

### ¿Por qué RandomizedSearchCV en lugar de GridSearchCV?

| Estrategia | Combinaciones | Folds | Total fits | Tiempo estimado |
|------------|:-------------:|:-----:|:----------:|:---------------:|
| GridSearchCV | 72 | 5 | 360 | 8–15 min |
| **RandomizedSearchCV** | **20** | **5** | **100** | **2–4 min** |

> Referencia: Bergstra & Bengio (2012) — *"Random Search for Hyper-Parameter Optimization"* — JMLR.

---

## 📈 Resultados

### Parte 1 — Clasificación de `burnout_level`

| Modelo | Accuracy | F1-Score | AUC-ROC |
|--------|:--------:|:--------:|:-------:|
| Regresión Logística | 0.9606 | 0.9607 | 0.9906 |
| Árbol de Decisión | 0.9942 | 0.9942 | 0.9974 |
| Random Forest | 0.9920 | 0.9920 | 0.9982 |
| **Gradient Boosting** | 0.9934 | 0.9934 | **1.0000** |

**Cross-Validation (StratifiedKFold k=8):**

| Modelo | Media F1 | Std F1 | Estabilidad |
|--------|:--------:|:------:|:-----------:|
| Regresión Logística | ~0.960 | Baja | ✅ Estable |
| Árbol de Decisión | ~0.990 | Media | ⚠️ Varianza moderada |
| Random Forest | ~0.991 | Baja | ✅ Muy estable |
| **Gradient Boosting** | **~0.993** | **Baja** | ✅ **Mejor balance** |

### Parte 2 — Regresión de `stress_level` (escala 0–100)

| Modelo | MAE | RMSE | R² |
|--------|:---:|:----:|:--:|
| **Ridge Regression** | 8.2363 | 10.3887 | **0.7961** |
| Gradient Boosting Reg. | 8.6054 | 10.7675 | 0.7810 |
| SVR | 8.8256 | 11.0567 | 0.7691 |
| Random Forest Regressor | 9.1132 | 11.3543 | 0.7565 |

---

## 🏆 Modelos Seleccionados

### Clasificación — Gradient Boosting
1. **AUC-ROC perfecto (1.0000)** en las tres clases — discriminación probabilística perfecta.
2. **Estabilidad en CV** — F1 media más alta (~0.993) con Std más baja entre los 4 modelos.
3. **Robustez** — 100 estimadores secuenciales con corrección progresiva de errores.

### Regresión — Mejor R² (ver Paso 4 del notebook)
- **R² = 0.7961** → explica el 79.61% de la varianza de `stress_level`.
- **RMSE = 10.3887** → error promedio del ~10.4% sobre escala 0-100.
- **MAE = 8.2363** → en promedio la predicción está a 8.24 puntos del valor real.
- Complementa la clasificación con una **estimación cuantitativa continua** del estrés.

> ⚠️ **Nota:** Métricas excepcionalmente altas por la naturaleza **sintética** del dataset.
> En datos reales: clasificación F1 entre **0.70–0.85**, regresión R² entre **0.50–0.70**.

### Hiperparámetros óptimos — Gradient Boosting (RandomizedSearchCV)

```python
GradientBoostingClassifier(
    n_estimators     = 200,   # optimizado
    learning_rate    = 0.05,  # optimizado
    max_depth        = 3,     # optimizado
    subsample        = 0.8,   # optimizado
    min_samples_leaf = 10,
    max_features     = 'sqrt',
    random_state     = 42
)
```

---

## 🛠️ Tecnologías utilizadas

| Librería | Uso |
|----------|-----|
| `pandas` | Manipulación de datos |
| `numpy` | Operaciones numéricas |
| `matplotlib` / `seaborn` | Visualización |
| `scikit-learn` | Modelos ML, preprocesamiento, métricas, CV |
| `scipy` | Estadísticas, winsorización |

---

## 🚀 Cómo ejecutar

### 1. Clonar el repositorio
```bash
git clone https://github.com/ggranizo2507/Machine-Learning-Grupo-4-Developer-Burnout.git
cd Machine-Learning-Grupo-4-Developer-Burnout
```

### 2. Instalar dependencias
```bash
pip install pandas numpy matplotlib seaborn scikit-learn scipy
```

### 3. Ejecutar en Google Colab
[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/ggranizo2507/Machine-Learning-Grupo-4-Developer-Burnout/blob/main/Prediccion_agotamiento_desarrollador_clasificacion_ML_S2.ipynb)

> Sube el archivo `developer_burnout_dataset.csv` a `/content/` en Colab antes de ejecutar.

### 4. Ver resultados en GitHub
[![Ver Notebook en GitHub](https://img.shields.io/badge/📊%20Ver%20Gráficos%20en%20GitHub-181717?style=for-the-badge&logo=github)](https://github.com/ggranizo2507/Machine-Learning-Grupo-4-Developer-Burnout/blob/main/Prediccion_agotamiento_desarrollador_clasificacion_ML_S2.ipynb)

---

## 📋 Contenido del Notebook (85 celdas)

| Sección | Descripción |
|---------|-------------|
| Pasos 1–4 | Instalación, carga, EDA, preprocesamiento |
| Paso 5 | Feature Engineering (8 variables nuevas) |
| Paso 5.1 | Análisis de correlación con el target |
| Modelo 1 | Regresión Logística |
| Modelo 2 | Árbol de Decisión (overfitting + poda) |
| Modelo 3 | Random Forest |
| Modelo 4 | Gradient Boosting |
| Comparación | ROC comparativa, heatmap, barplot acumulado |
| CV | StratifiedKFold k=8 — tabla, líneas, boxplot |
| Tuning | RandomizedSearchCV + evaluación final + max_depth |
| Conclusiones CV | Selección del mejor clasificador |
| Regresión Paso 1 | Preparación dataset + imputación |
| Regresión Paso 2 | 4 modelos de regresión (justificados) |
| Regresión Paso 3 | Métricas: MAE, MSE, RMSE, R² |
| Regresión Paso 4 | Tabla comparativa + selección del mejor |
| Regresión Paso 5 | Real vs Predicho + Residuos |
| Regresión Paso 6 | Comparación R² visual |
| Regresión Paso 7 | Curvas de aprendizaje |
| Regresión Paso 8 | Resultados consolidados |
| Regresión Paso 9 | Pipeline completo |
| Conclusiones Finales | Clasificación + Regresión + Limitaciones + Trabajo futuro |

---

## 👥 Autores

**Grupo 4 — Machine Learning**
Universidad de Especialidades Espíritu Santo (UEES)

| # | Nombre |
|---|--------|
| 1 | Eduardo Alejandro Ceballos Jijón |
| 2 | Guillermo Leónidas Granizo Veintimilla |
| 3 | José Farid Ulloa Manzur |
| 4 | Christian Xavier Valle Maridueña |

---

## 📄 Licencia

Este proyecto está bajo la licencia MIT. Ver el archivo [LICENSE](LICENSE) para más detalles.
