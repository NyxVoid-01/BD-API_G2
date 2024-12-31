[![Python](https://img.shields.io/badge/Python-%20-101010?style=for-the-badge&logo=python&logoColor=white&labelColor=1c9ae7)](https://www.python.org/)
[![IA-ML](https://img.shields.io/badge/IA-%20-101010?style=for-the-badge&logo=robot&logoColor=white&labelColor=6C6E6B)](https://en.wikipedia.org/wiki/Artificial_intelligence)
[![JSON](https://img.shields.io/badge/JSON-%20-101010?style=for-the-badge&logo=json&logoColor=white&labelColor=000000)](https://www.json.org/)
[![Zipfile](https://img.shields.io/badge/Zipfile-%20-101010?style=for-the-badge&logo=archive&logoColor=white&labelColor=FFC107)](https://docs.python.org/3/library/zipfile.html)
[![Pandas](https://img.shields.io/badge/Pandas-%20-101010?style=for-the-badge&logo=pandas&logoColor=white&labelColor=150458)](https://pandas.pydata.org/)
[![NumPy](https://img.shields.io/badge/NumPy-%20-101010?style=for-the-badge&logo=numpy&logoColor=white&labelColor=013243)](https://numpy.org/)
[![Matplotlib](https://img.shields.io/badge/Matplotlib-%20-101010?style=for-the-badge&logo=plotly&logoColor=white&labelColor=11557C)](https://matplotlib.org/)
[![Seaborn](https://img.shields.io/badge/Seaborn-%20-101010?style=for-the-badge&logoColor=white&labelColor=4C84A4)](https://seaborn.pydata.org/)
[![Math](https://img.shields.io/badge/Math-%20-101010?style=for-the-badge&logo=academia&logoColor=white&labelColor=00758F)](https://docs.python.org/3/library/math.html)
[![Scikit-learn](https://img.shields.io/badge/Scikit_Learn-%20-101010?style=for-the-badge&logo=scikit-learn&logoColor=white&labelColor=F7931E)](https://scikit-learn.org/)
[![SciPy](https://img.shields.io/badge/SciPy-%20-101010?style=for-the-badge&logo=scipy&logoColor=white&labelColor=8CAAE6)](https://scipy.org/)

# CorHeart

**CorHeart** es un modelo de Machine Learning diseñado para predecir enfermedades coronarias con alta precisión, utilizando información demográfica, comportamientos de salud, y condiciones previas diagnosticadas.

---

## Contexto

Este modelo fue desarrollado como parte de la competencia **[PhawAI: Predicción de enfermedades coronarias](https://www.kaggle.com/competitions/prediccion-de-sufrir-enfermedades-coronarias/overview)**. Los datos utilizados fueron proporcionados por los organizadores de Kaggle y se encuentran sujetos a sus términos de uso.

El desarrollo del modelo, análisis, preprocesamiento de datos, balanceo de clases y visualizaciones fueron realizados íntegramente por mí como parte de mi participación en la competencia. 

## Mi aporte

Durante el desarrollo de este modelo, implementé:
1. Obtención del dataset y lectura de datos.
2. Preprocesamiento y limpieza de datos.
   - Identificación de si nuestros datos son **MCAR, MAR o NMCAR.**
   - Aplicación de one-hot enconding y transformación logarítmica.
   - Imputación de valores faltantes **(usando el algoritmo MICE con IterativeImputer)**
   - Escalado y tratamiento de outliers.
3. Análisis exploratorio y visualización.
   - Uso de diferentes **métodos estadísticos, mapas de calor  y gráficos** para identificar la correlación entre variables y la variable objetivo.
   - Selección de características con un modelo ML.
4. Manejo del desbalance de clases.
   - Evaluación del mejor método para usar **(SMOTE, ADASYN SMOTEENN)**.
5. Diseño y entrenamiento del modelo predictivo.
   - Implementación de diferentes modelos **(RandomForestClassifier, Regresión Logística, Árboles de Decisión, Gradient Boosting (XGBoost) y Gradient Boosting (LightGBM)).**
6. Evaluación del desempeño.
   - Reporte de clasificación.
   - 

## Resultados
> [!NOTE]
> El siguiente reporte de clasificación es del dataset de entrenamiento.

El modelo **CorHeart** alcanzó los siguientes resultados:
| Clase | Precisión | Recall | F1-Score | Soporte |
|-------|-----------|--------|----------|---------|
| 0.0   | 0.34      | 0.10   | 0.16     | 8477    |
| 1.0   | 0.93      | 0.98   | 0.95     | 95697   |

#### **Métricas Globales**

|  |  Precisión | Recall | F1-Score | Soporte |
|----------------|--------|----------|---------|----------|
| Precisión      |   | | 0.91 | 10174  |
| Macro Avg      | 0.63|  0.54 |  0.56 | 10174|
| Weighted Avg   | 0.88 | 0.91 | 0.89 |10174|

El modelo CorHeart muestra un excelente desempeño al identificar casos de enfermedades coronarias (clase 1), con una precisión del 93% y un recall del 98%. Sin embargo, tiene dificultades significativas al predecir correctamente la clase 0 (ausencia de enfermedad), con un recall del 10% y una precisión del 34%. Esto se debe al desbalance de clases, donde la clase 1 domina los datos (~91% del total).

Aunque la precisión general es alta (91%), el bajo desempeño en la clase 0 puede llevar a errores críticos al no detectar correctamente a pacientes sanos, clasificándolos erróneamente como enfermos. Por tanto, el modelo es más adecuado para minimizar falsos negativos en la clase 1, pero requiere ajustes (como técnicas de balanceo de clases, recolección de datos o técnicas más avanzadas) para mejorar su capacidad de identificar correctamente la clase 0. Detalles adicionales pueden encontrarse en la carpeta [`results`](./results/).


## Futuras mejoras
1. Conseguir mas datos de la clase minoritaria es importante porque ayuda al modelo a aprender mejor las caracteristicas de esta clase, lo que puede mejorar su desempeño.

2. Cambiar los pesos de las clases durante el entrenamiento sirve para darle mas importancia a la clase minoritaria, así el modelo presta mas atención a esa clase y predice mejor los casos negativos.

3. Ajustar el umbral de decisión puede ayudar a que el modelo tenga un mayor recall para la clase minoritaria, aunque podría afectar la precisión. Es clave encontrar un buen equilibrio según lo que se necesite.