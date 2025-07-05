# Clasificación de Ritmo Cardíaco con Machine Learning

Este proyecto implementa un pipeline de clasificación supervisada para distinguir ritmos cardíacos normales (`N`) de fibrilación auricular (`A`) a partir de señales ECG reales del PhysioNet/CinC Challenge 2017. Se utilizan estadísticas del intervalo RR como características y modelos clásicos de ML (Random Forest).

---

## Estructura del proyecto

```
PROYECTO_ML/
├── data/
│   ├── training2017/         # Señales originales (.mat, .hea, REFERENCE.csv)
│   └── ecg_rr_features_curado.csv   # Dataset preprocesado con estadísticas RR
├── notebooks/
│   ├── Exploracion_Inicial.ipynb      # Análisis de señales, extración de estadísticas RR
│   ├── Exploracion_Estadisticas.ipynb # Análisis de características RR
│   └── Modelo.ipynb                   # Entrenamiento, validación y evaluación del modelo
├── Informe final.pdf                  # Reporte escrito del proyecto
└── README.md
```

---

## Datos

- Se utilizaron señales de ECG reales del PhysioNet 2017 (`training2017`).
- El dataset curado (`ecg_rr_features_curado.csv`) contiene:
  - `mean_rr`, `std_rr`, `skew_rr`, `kurt_rr`: estadísticas de intervalos RR
  - `label`: clase (`N` o `A`)
  - `record`: ID del registro

---

## Tecnologías y librerías usadas

- Python 3.8+
- `scikit-learn`, `pandas`, `seaborn`, `matplotlib`, `wfdb`, `feature-engine`, `imblearn`, `neurokit2`

Instalación de dependencias:

```bash
pip install numpy pandas matplotlib seaborn scikit-learn imbalanced-learn neurokit2 wfdb feature-engine
```

---

## Ejecución

Puedes correr el flujo completo desde Jupyter Notebook:

1. **Exploración**:  
   `notebooks/Exploracion_Inicial.ipynb`  
   Gráficos de señales, análisis básico del dataset original, extracción de estadísticas RR.

2. **Extracción de características**:  
   `notebooks/Exploracion_Estadisticas.ipynb`  
   Análisis estadístico de características RR.

3. **Entrenamiento y evaluación del modelo**:  
   `notebooks/Modelo.ipynb`  
   - Limpieza de outliers (`OutlierTrimmer`)
   - Balanceo de clases (`SMOTE`)
   - Búsqueda de hiperparámetros (`GridSearchCV`)
   - Entrenamiento con `RandomForestClassifier`
   - Matriz de confusión e importancia de variables.

---

## Resultados esperados

- **Métrica principal**: F1 ponderado
- **Visualizaciones**:
  - Distribuciones de variables por clase
  - Gráficos de estadísticas RR
  - Diagramas de caja
  - Matriz de confusión
  - Importancia de características

---

## Contexto clínico

La fibrilación auricular es la arritmia sostenida más frecuente. Se caracteriza por la **irregularidad en los intervalos RR**, y su detección temprana puede prevenir eventos como ACV. Este proyecto simula un sistema automático de clasificación para señales cortas de ECG de una sola derivación, imitando escenarios reales de dispositivos portátiles.

---

## Referencias

- PhysioNet/CinC Challenge 2017:  
  https://physionet.org/content/challenge-2017/1.0.0/

---

## Autor

Diego Salvador – Ingeniería Civil en Computación 
Universidad de Talca
