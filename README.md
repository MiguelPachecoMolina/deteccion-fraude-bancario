# 🏦 Detección de Fraude en Transacciones Bancarias mediante Técnicas de Agrupamiento y Detección de Anomalías[cite: 1]

## 📝 Descripción del Proyecto
La detección de fraude bancario enfrenta el reto del alto desbalance entre transacciones legítimas y fraudulentas[cite: 1]. Este proyecto propone un enfoque híbrido que integra aprendizaje supervisado y no supervisado para mejorar la identificación de fraudes en datos de tarjetas de crédito[cite: 1]. Se busca identificar transacciones fraudulentas de manera temprana y precisa, minimizando las pérdidas económicas y reduciendo la cantidad de falsos positivos que generan sobrecarga operativa[cite: 1].

## 👥 Equipo de Trabajo
Este proyecto de investigación y modelado fue desarrollado colaborativamente por:

*   **Miguel Alejandro Pacheco Molina**
*   **Mauricio Hamabiel Cortes Moreno**
*   **Alejandro Maldonado López**
*   **Jesús Armando Soria Martínez**

## 📊 Conjunto de Datos
*   **Fuente:** "Credit Card Fraud Detection" de la plataforma Kaggle[cite: 1].
*   **Volumen:** 284,807 transacciones realizadas con tarjetas de crédito[cite: 1].
*   **Desbalance:** Las transacciones fraudulentas representan aproximadamente el 0.172% del total (492 casos)[cite: 1].
*   **Características:** Compuesto por 29 variables numéricas (V1 a V28) obtenidas mediante Análisis de Componentes Principales (PCA) por confidencialidad, además de las variables de Tiempo y Monto[cite: 1].

## ⚙️ Metodología y Tecnologías Aplicadas
El proyecto se desarrolló bajo el estándar **CRISP-DM**, abarcando desde la comprensión del negocio hasta la evaluación del modelo[cite: 1].

1.  **Preprocesamiento y Balanceo:** Se aplicó estandarización (`StandardScaler`) y la técnica **SMOTE** (Synthetic Minority Over-sampling Technique) exclusivamente sobre el conjunto de entrenamiento (80% de los datos) para mitigar el severo desbalance de clases[cite: 1].
2.  **Aprendizaje No Supervisado (Agrupamiento):** 
    *   Se empleó **K-Means** (con k=4 determinado mediante coeficiente de silueta) para identificar patrones de comportamiento[cite: 1].
    *   Se entrenó un **Mapa Autoorganizado (SOM)**, aplicando posteriormente K-Means sobre los pesos obtenidos de sus neuronas para proyectar datos de alta dimensionalidad[cite: 1].
3.  **Ingeniería de Características:** Se crearon nuevas variables basadas en la pertenencia a los clústeres, distancias al centroide y medidas de confianza de pertenencia[cite: 1].
4.  **Aprendizaje Supervisado (Clasificación):** Se utilizó **Random Forest** como modelo base y como clasificador final para los conjuntos de datos enriquecidos (híbridos)[cite: 1].

## 🏆 Resultados Destacados
La integración de técnicas no supervisadas con modelos supervisados demostró ser una estrategia superior en entornos de alto desbalance[cite: 1].

*   **Modelo Base (Random Forest + SMOTE):** F1-score macro de 0.92 y un Recall de 0.90[cite: 1]. 
*   **Modelo Híbrido 1 (Random Forest + K-Means):** Alcanzó un F1-score macro de 0.92 y un Recall de 0.92[cite: 1]. Este modelo logró reducir considerablemente el número de falsos positivos en comparación con la línea base[cite: 1].
*   **Modelo Híbrido 2 (Random Forest + SOM + K-Means):** Obtuvo un F1-score macro de 0.92 y un Recall de 0.91[cite: 1]. Permitió capturar patrones de fraude complejos que los clasificadores tradicionales no logran identificar por sí solos[cite: 1].

## 🚀 Despliegue
Se implementó una función de evaluación que procesa nuevas transacciones individuales, realiza el escalado, asigna el clúster, calcula distancias y arroja la probabilidad final de fraude basándose en un umbral de decisión[cite: 1].
