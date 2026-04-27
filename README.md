# 🔥 Predicción del Agotamiento (Burnout) del Desarrollador | Clasificación ML

![Python](https://img.shields.io/badge/Python-3.10+-blue?logo=python)
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-1.3+-orange?logo=scikit-learn)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?logo=jupyter)
![License](https://img.shields.io/badge/License-MIT-green)
![Status](https://img.shields.io/badge/Status-Completado-brightgreen)

---

## 📌 Descripción del Problema

El **agotamiento laboral (burnout)** es uno de los problemas más críticos en la industria del software. Este proyecto adopta un **enfoque basado en datos** para predecir el nivel de burnout de desarrolladores de software (`Low`, `Medium`, `High`) a partir de métricas de estilo de vida y trabajo.

> **Pregunta de investigación:** ¿Es posible predecir el nivel de agotamiento de un desarrollador a partir de variables como horas de trabajo, nivel de estrés, horas de sueño y métricas de productividad?

---

## 🗂️ Estructura del Repositorio

```
Machine-Learning-Grupo-4-Developer-Burnout/
│
├── 📓 Prediccion_agotamiento_desarrollador_clasificacion_ML_S2.ipynb
│       Notebook principal con todo el pipeline de ML
│
├── 📊 developer_burnout_dataset.csv
│       Dataset fuente (7,000 registros × 12 variables)
│
└── 📄 README.md
        Este archivo
```

---

## 📊 Dataset

| Característica | Detalle |
|----------------|---------|
| **Fuente** | [Kaggle — Developer Burnout Prediction Dataset](https://www.kaggle.com/datasets/asifxzaman/developer-burnout-prediction-dataset7000-samples) |
| **Registros** | 7,000 |
| **Variables** | 12 |
| **Variable objetivo** | `burnout_level` → `Low` / `Medium` / `High` |
| **Tipo de problema** | Clasificación multiclase |

### Variables del dataset

| Variable | Tipo | Descripción |
|----------|------|-------------|
| `age` | Numérica | Edad del desarrollador |
| `experience_years` | Numérica | Años de experiencia |
| `daily_work_hours` | Numérica | Horas de trabajo diarias |
| `sleep_hours` | Numérica | Horas de sueño por noche |
| `caffeine_intake` | Numérica | Consumo de cafeína (mg/día) |
| `bugs_per_day` | Numérica | Bugs reportados por día |
| `commits_per_day` | Numérica | Commits realizados por día |
| `meetings_per_day` | Numérica | Reuniones por día |
| `screen_time` | Numérica | Tiempo frente a pantalla (horas) |
| `exercise_hours` | Numérica | Horas de ejercicio por semana |
| `stress_level` | Numérica | Nivel de estrés (escala 1-10) |
| `burnout_level` | Categórica | **Variable objetivo** |

---

## 🧠 Metodología

### Pipeline completo

```
Datos Crudos
    │
    ▼
1. Limpieza y preprocesamiento
   • Eliminación de NaN en variable objetivo
   • Imputación con mediana (SimpleImputer)
   • Codificación de etiquetas (LabelEncoder)
   • Tratamiento de outliers (Winsorización IQR)
    │
    ▼
2. Análisis Exploratorio (EDA)
   • Distribuciones, skewness, curtosis
   • Correlaciones y mapa de calor
   • Análisis de valores faltantes
    │
    ▼
3. Feature Engineering (8 variables nuevas)
   • work_to_sleep_ratio, productivity_score
   • digital_overload, recovery_index
   • meeting_burden, stimulant_dependency
   • stress_load, experience_stress_ratio
    │
    ▼
4. Análisis de correlación con el target
   • Opción 1: Detección de features infladas
   • Opción 2: Exclusión justificada de features
    │
    ▼
5. Entrenamiento de modelos (4 algoritmos)
   • Regresión Logística
   • Árbol de Decisión (con búsqueda de profundidad óptima)
   • Random Forest
   • Gradient Boosting
    │
    ▼
6. Evaluación y comparación
   • Métricas: Accuracy, Precisión, Recall, F1, AUC-ROC
   • Curvas ROC comparativas
   • Matrices de confusión
   • Heatmap y barplot de comparación
    │
    ▼
7. Validación cruzada (StratifiedKFold k=8)
   • F1 por fold, boxplot de estabilidad
    │
    ▼
8. Ajuste de hiperparámetros (GridSearchCV)
   • Optimización de Gradient Boosting
   • Evaluación final en test set (una sola vez)
```

---

## 📈 Resultados

### Métricas de clasificación (test set)

| Modelo | Accuracy | Precisión | Recall | F1-Score | AUC-ROC |
|--------|:--------:|:---------:|:------:|:--------:|:-------:|
| Regresión Logística | 0.9606 | 0.9608 | 0.9606 | 0.9607 | 0.9906 |
| Árbol de Decisión | **0.9942** | **0.9942** | **0.9942** | **0.9942** | 0.9974 |
| Random Forest | 0.9920 | 0.9921 | 0.9920 | 0.9920 | 0.9982 |
| **Gradient Boosting** | 0.9934 | 0.9935 | 0.9934 | 0.9934 | **1.0000** |

### AUC-ROC por clase

| Modelo | High | Low | Medium |
|--------|:----:|:---:|:------:|
| Regresión Logística | 0.9959 | 0.9947 | 0.9860 |
| Árbol de Decisión | 0.9957 | 0.9984 | 0.9977 |
| Random Forest | 0.9988 | 0.9992 | 0.9974 |
| **Gradient Boosting** | **1.0000** | **1.0000** | **0.9999** |

---

## 🏆 Modelo Seleccionado: Gradient Boosting

Se seleccionó **Gradient Boosting** como modelo final por las siguientes razones:

1. **AUC-ROC perfecto (1.0000)** en las clases High y Low, y 0.9999 en Medium — separa perfectamente las distribuciones de probabilidad entre las tres clases.
2. **F1-Score competitivo (0.9934)** — segundo mejor resultado, a menos de 0.001 del árbol de decisión.
3. **Mayor robustez** — resultado de 100 estimadores secuenciales con corrección progresiva de errores, más confiable que un árbol único.

> ⚠️ **Nota:** Todos los modelos presentan métricas excepcionalmente altas (> 0.96) debido a la naturaleza **sintética** del dataset. En datos reales de burnout se esperarían métricas entre 0.70 y 0.85.

### Hiperparámetros óptimos (GridSearchCV)

```python
GradientBoostingClassifier(
    n_estimators  = 200,    # optimizado
    learning_rate = 0.05,   # optimizado
    max_depth     = 3,      # optimizado
    subsample     = 0.8,    # optimizado
    min_samples_leaf = 10,
    max_features  = 'sqrt',
    random_state  = 42
)
```

---

## 🛠️ Tecnologías utilizadas

| Librería | Uso |
|----------|-----|
| `pandas` | Manipulación de datos |
| `numpy` | Operaciones numéricas |
| `matplotlib` / `seaborn` | Visualización |
| `scikit-learn` | Modelos ML, preprocesamiento, métricas |
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
Abre el notebook directamente en Colab:

[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/ggranizo2507/Machine-Learning-Grupo-4-Developer-Burnout/blob/main/Prediccion_agotamiento_desarrollador_clasificacion_ML_S2.ipynb)

> Recuerda actualizar la ruta del dataset en la celda de carga de datos apuntando a tu Google Drive.

---

## 📋 Contenido del Notebook

| Sección | Descripción |
|---------|-------------|
| Paso 1 | Instalación e imports |
| Paso 2 | Carga y exploración del dataset |
| Paso 3 | Análisis Exploratorio (EDA) |
| Paso 4 | Preprocesamiento y limpieza |
| Paso 5 | Feature Engineering (8 features nuevas) |
| Paso 5.1 | Análisis de correlación con el target |
| Modelo 1 | Regresión Logística |
| Modelo 2 | Árbol de Decisión (con diagnóstico de overfitting) |
| Modelo 3 | Random Forest |
| Modelo 4 | Gradient Boosting |
| Comparación | Curvas ROC, heatmap y barplot comparativo |
| CV | StratifiedKFold k=8 |
| Tuning | GridSearchCV + evaluación final |
| Conclusiones | Selección y justificación del mejor modelo |

---

## 👥 Autores

**Grupo 4 — Machine Learning**
Universidad de Especialidades Espíritu Santo (UEES)
Eduardo Alejandro Ceballos Jijón 
Guillermo Leónidas Granizo Veintimilla 
José Farid Ulloa Manzur 
Christian Xavier Valle Maridueña
---

## 📄 Licencia

Este proyecto está bajo la licencia MIT. Ver el archivo [LICENSE](LICENSE) para más detalles.
