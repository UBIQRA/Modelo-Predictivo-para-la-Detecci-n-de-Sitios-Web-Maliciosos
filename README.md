I. Modelo Predictivo para la Detección de Sitios Web Maliciosos

Phishing Website Detection Model

II. Descripción General

Este proyecto presenta el desarrollo de un modelo de aprendizaje automático (Machine Learning) diseñado para detectar sitios web de phishing con una precisión superior al 90%.
La solución utiliza modelos supervisados entrenados con datasets de Kaggle, implementados dentro del entorno sin código de KNIME, lo que permite analizar, entrenar y comparar 
modelos predictivos de manera visual e intuitiva.

III. Objetivo

-Desarrollar e implementar un modelo de Machine Learning capaz de:
-Detectar sitios web de phishing con ≥90% de precisión.
-Alcanzar un AUC (Área Bajo la Curva ROC) superior a 0.90.
-Entrenar y evaluar múltiples algoritmos supervisados en un periodo de 3 meses.

IV. Descripción del Problema

El phishing sigue siendo una de las amenazas cibernéticas más comunes y efectivas, aprovechando la ingeniería social para engañar a los usuarios.
Muchas PYMEs y emprendedores carecen de herramientas accesibles para detectar estos ataques, lo que provoca:

-Pérdidas financieras.
-Robo de información confidencial.
-Daños reputacionales.

La detección temprana de sitios fraudulentos es clave para reducir riesgos y fortalecer la ciberseguridad organizacional.

V. Metodología de Análisis

1. Análisis Exploratorio de Datos (EDA)
   
-Identificación de relaciones, anomalías y patrones en los datos.
-Transformación y normalización para preparar el dataset para modelado.

2. Proceso ETL
   
-Limpieza y preparación de datos con nodos KNIME:
-Missing Value para completar datos faltantes.
-Number to String para conversión de tipos.
-Rule Engine para homologar variables de salida.

3. Modelado y Entrenamiento
   
-Implementación de modelos supervisados:
-Decision Tree Learner
-Random Forest Learner
-XGBoost Tree Ensemble
-Naive Bayes Learner
-Logistic Regression Learner

4. Evaluación de Modelos

Comparación mediante métricas:
-Accuracy
-Precision / Recall / F1-score
-Cohen’s Kappa
-Curva ROC y AUC

VI. Conjunto de Datos

Se emplearon dos datasets públicos de Kaggle, combinados y homologados:
-Phishing Websites Data
-Phishing Website Dataset 

Tamaño combinado: 20,000 registros
Parámetros analizados: 31 variables
Variable objetivo: Result (1: Legítimo, -1: Phishing)

VII. Características Clave del Dataset

-Basadas en URL y dominio:
Have_IP, URL_Length, Prefix_Suffix, HTTPS_Token, DNS_Record, Domain_Age

-Basadas en comportamiento:
Mouse_over, Right_Click, IFrame, PopUpWindow

-Basadas en tráfico y motores de búsqueda:
Web_Traffic, Page_Rank, Google_Index, Links_pointing_to_page

VIII. Resultados de Modelos

| Modelo                  | Accuracy   | Precision | Recall | F1-score | AUC       |
| ----------------------- | ---------- | --------- | ------ | -------- | --------- |
| **XGBoost**             | **0.8843** | 0.9338    | 0.8092 | 0.86.69  | **0.949** |
| **Decision Tree**       | 0.88       | 0.889     | 0.876  | 0.878    | 0.938     |
| **Random Forest**       | 0.8786      | 0.9678     | 0.7651  | 0.85.46    | 0.901     |
| **Logistic Regression** | 0.82       | 0.83      | 0.63   | 0.81     | 0.9      |
| **Naive Bayes**         | 0.65       | 0.66      | 0.31   | 0.64     | 0.696      |

Modelo con mejor rendimiento:
XGBoost Tree Ensemble, con AUC de 0.949 y F1-score de 0.888.

IX. Matriz de confusión para análisis de errores.

| Modelo                  |  TP  |  TN  |  FP |  FN  | 
| ----------------------- | -----| -----| ----| -----| 
| **XGBoost**             | 2384 | 3202 | 169 | 562  | 
| **Decision Tree**       | 3182 | 2376 | 570 | 189  | 
| **Random Forest**       | 2254 | 3296 | 75  | 692  |
| **Logistic Regression** | 3064 | 2102 | 844 | 307  |
| **Naive Bayes**         | 1815 | 2241 | 705 | 1556 | 

X. FPR (False Positive Rate)

Formula: FPR = FP / FP + TN 

| Modelo                  |   FPR  |  TPR  |
| ----------------------- | ------ | ----- 
| **XGBoost**             | 0.0501 | .8092 | 
| **Decision Tree**       | 0.198  |       |
| **Random Forest**       | 0.0222 | .7651 |
| **Logistic Regression** | 0.286  |       |
| **Naive Bayes**         | 0.224  |       |

XI. Análisis de errores

Formula: 

Error global = 1 − Accuracy
Clasificaciones incorrectas = FP + FN

| Modelo         | Clasificaciones incorrectas | Error global | Clasificaciones correctas |
| -------------- | --------------------------: | -----------: | --------------------------
| XGBoost        |                         731 |       11.57% |                     5586 |
| XGBoost        |                         731 |       11.57% |                      |
| Random Forest  |                         767 |       12.14% |                     5550 |

XII. Visualización y Comparativas

-Curvas ROC superpuestas para todos los modelos.
-Matriz de confusión para análisis de errores.
-FPR (False Positive Rate).
-Gráficos interactivos (Pie Chart, Bar Chart, ROC Curve) en KNIME.
-Feature Importance para interpretar las variables más influyentes.

XIII . Conclusión y Reflexión Final

-La Inteligencia Artificial se consolida como un aliado estratégico en la detección de amenazas digitales.
-Este proyecto demuestra que: Los modelos supervisados permiten una detección precisa de sitios maliciosos.
-KNIME facilita la implementación sin necesidad de programar.
-La IA, usada éticamente, potencia la inteligencia humana, no la reemplaza.
-Además, se destaca la importancia de continuar promoviendo la concientización en ciberseguridad como complemento al uso de herramientas predictivas.

Autor

Arnoldo Treviño Ceja
Ingeniero Administrador de Sistemas
Consultor en Tecnologías de la Información y Ciberseguridad
Fundador de UBIQRA

📧 artrevino@ubiqra.com
