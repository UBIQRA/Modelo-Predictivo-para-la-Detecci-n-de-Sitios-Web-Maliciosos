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

| Modelo                  | Accuracy   | Precision | Recall | F1-score | AUC       |  Cohen´s Kappa |
| ----------------------- | ---------- | --------- | ------ | -------- | --------- | -------------- |
| **XGBoost**             | **0.8843** | 0.9338    | 0.8092 | 0.8669   | **0.949** |  0.766         |
| **Decision Tree**       | 0.8798     | 0.9263    | 0.8065 | 0.8623   | 0.938     |  0.757         |
| **Random Forest**       | 0.8786     | 0.9678    | 0.7651 | 0.8546   | 0.901     |  0.753         |
| **Logistic Regression** | 0.8178     | 0.8726    | 0.7135 | 0.7851   | 0.9       |  0.630         |
| **Naive Bayes**         | 0.6421     | 0.5902    | 0.7607 | 0.6647   | 0.696     |  0.294         |

Modelo con mejor rendimiento:
XGBoost Tree Ensemble, con AUC de 0.949 y F1-score de 0.8669

IX. Matriz de confusión para análisis de errores.

| Modelo                  |  TP  |  TN  |  FP  |  FN  | 
| ----------------------- | -----| -----| -----| -----| 
| **XGBoost**             | 2384 | 3202 | 169  | 562  | 
| **Decision Tree**       | 3182 | 2376 | 570  | 189  | 
| **Random Forest**       | 2254 | 3296 | 75   | 692  |
| **Logistic Regression** | 2102 | 3064 | 307  | 844  |
| **Naive Bayes**         | 2241 | 1815 | 1556 | 705  | 

X. FPR (False Positive Rate)

Formula: FPR = FP / FP + TN 

| Modelo                  |   FPR  |  TPR   |
| ----------------------- | ------ | ----- 
| **XGBoost**             | 0.0501 | 0.8092 | 
| **Decision Tree**       | 0.0560 | 0.8065 |
| **Random Forest**       | 0.0222 | 0.7651 |
| **Logistic Regression** | 0.0910 | 0.7135 |
| **Naive Bayes**         | 0.4615 | 0.7607 |

XI. Análisis de errores

Formula: 

Error global = 1 − Accuracy
Clasificaciones incorrectas = FP + FN

| Modelo               | Clasificaciones incorrectas  | Error global | Clasificaciones correctas |
| -------------------- | ---------------------------: | -----------: | --------------------------
| XGBoost              |                         731  |       11.57% |                     5586 |
| Decision Tree        |                         759  |       12.02% |                     5558 |
| Random Forest        |                         767  |       12.14% |                     5550 |
| Logistic Regression  |                         1151 |       18.22% |                     5166 |
| Naive Bayes          |                         2261 |       35.79% |                     4056 |

XII. Interpretabilidad y análisis global

12.1 Permutation Feature Importance (PFI)


| Rank | Feature            | Mean Accuracy Diff (10 Perm) | Std. Dev. Accuracy Diff (10 Perm) | Mean Accuracy Diff (30 Perm) | Std. Dev. Accuracy Diff (30 Perm) |
| ---: | ------------------ | --------------------------:  | -------------------------------:  | --------------------------:  | -------------------------------:  |
|    1 |   URL_of_Anchor    |                    0.16810   |                         0.00352   |                    0.16777   |                         0.00351   |
|    2 |   SSLFinal_State   |                    0.11988   |                         0.00359   |                    0.12049   |                         0.00282   |
|    3 |   URL_Length       |                    0.11492   |                         0.00489   |                    0.11580   |                         0.00454   |
|    4 |   Iframe           |                    0.07560   |                         0.00388   |                    0.07607   |                         0.00378   |
|    5 |   Web_Traffic      |                    0.03902   |                         0.00238   |                    0.03914   |                         0.00223   |
|    6 |   Mouse_Over       |                    0.03696   |                         0.00297   |                    0.03772   |                         0.00276   |
|    7 |   Favicon          |                    0.00098   |                         0.00068   |                    0.00080   |                         0.00069   |
|    8 |   Redirect         |                    0.00045   |                         0.00020   |                    0.00040   |                         0.00034   | 
|    9 |   PopupWindow      |                   -0.00044   |                         0.00050   |                   -0.00052   |                         0.00064   |
|   10 |   Right_Click      |                  -0.000015   |                         0.00005   |                  -0.000015   |                         0.00006   |


Interpretación: La diferencia media de precisión representa la disminución promedio en la precisión del modelo tras permutar aleatoriamente una característica. Valores más altos indican una mayor contribución al rendimiento predictivo. La desviación estándar refleja la variabilidad de la estimación de importancia entre las permutaciones.

El PFI se calculó utilizando la precisión como métrica de evaluación con 10 y 30 permutaciones. La diferencia media de precisión representa el cambio promedio en la precisión del modelo después de la permutación de características, mientras que la desviación estándar refleja la variabilidad de la estimación entre permutaciones. La configuración de 30 permutaciones se utilizó como estimación final.

12.2. Surrogate Models

Surrogate GLM 

Formula: GLM_Absolute_Importance = abs(GLM Coefficient)

GLM Coefficient → indica dirección y magnitud del efecto.
GLM_Absolute_Importance → elimina el signo y conserva la magnitud.

| Feature                    | GLM Coefficient | GLM_Absolute_Importance |
| ------------------------:  | --------------: | ----------------------: |
| Redirect                   |           7.148 |                   7.148  |
| Iframe                     |           5.009 |                   5.009  |
| Favicon                    |           4.353 |                   4.353  |
| Shortining_Service         |           2.656 |                   2.656  |
| Prefix_Suffix              |           1.482 |                   1.482  |
| double_slash_redirecting   |           1.225 |                   1.225  |
| Have_At                    |           1.163 |                   1.163  |
| Abnormal_URL               |           0.792 |                   0.792  |
| Submitting_to_email        |           0.483 |                   0.483  |
| Page_Rank                  |           0.408 |                   0.408  |

Surrogate Random Forest

| Rank | Variable       | Importance |
| ---: | -------------- | ---------: |
|    1 | SSLFinal_State |     2.3372 |
|    2 | Web_Traffic    |     1.9044 |
|    3 | URL_of_Anchor  |     1.8930 |
|    4 | URL_Length     |     1.2200 |
|    5 | Redirect       |        0.4 |
|    6 | Iframe         |     0.3239 |
|    7 | popUpWidnow    |     0.2406 |
|    8 | Mouse_over     |     0.1934 |
|    9 | Favicon        |     0.1069 |
|   10 | Right_Click    |     0.0769 |

12.3. Global Feature Importance

XGBoost Feature Importance

| Rank | Variable       | Importance |
| ---: | -------------- | ---------: |
|    1 | URL_Length     |     56.013 |
|    2 | SSLFinal_State |     49.365 |
|    3 | Prefix_Suffix  |     20.744 |
|    4 | URL_of_Anchor  |     19.981 |
|    5 | Have_At        |     13.856 |
|    6 | SFH            |      3.422 |
|    7 | Web_Traffic    |      3.268 |
|    8 | Mouse_over     |      3.070 |
|    9 | Links_in_tags  |      2.131 |
|   10 | Iframe         |      2.042 |


12.4 Consistencia de variables
Identificación de las variables con mayor influencia global.

| Feature        | XGBoost Rank | PFI Rank | GLM Rank | RF Rank | Appearances |
| -------------- | -----------: | -------: | -------: | ------: | ----------: |
| URL_Length     |            1 |        3 |        3 |       4 |         4/4 |
| SSLFinal_State |            2 |        2 |        4 |       1 |         4/4 |
| Prefix_Suffix  |            3 |       NA |        1 |       3 |         4/4 |
| URL_of_Anchor  |            4 |        1 |        5 |       6 |         4/4 |
| Have_At        |            5 |        5 |        9 |       2 |         4/4 |
| SFH            |            6 |        5 |        9 |       2 |         4/4 |
| Web_Traffic    |            7 |        5 |        9 |       2 |         4/4 |
| Mouse_over     |            8 |        6 |        9 |       2 |         4/4 |
| Links_in_tags  |            9 |        11|        9 |       2 |         4/4 |
| Iframe         |           10 |        4 |        9 |       2 |         4/4 |
| Favicon        |           26 |        7 |        9 |       2 |         4/4 |
| Redirect       |           23 |        8 |        9 |       2 |         4/4 |
| popUpWidnow    |           19 |        9 |        9 |       2 |         4/4 |
| Right_Click    |           24 |       10 |        9 |       2 |         4/4 |

Para evaluar la consistencia de la importancia global de las características, se compararon las variables identificadas entre las 10 principales según los métodos de interpretabilidad aplicados al modelo. El análisis considera la importancia de las características de XGBoost, la importancia de las características de permutación (PFI), el modelo GLM sustituto y el modelo Random Forest sustituto. Dado que cada método utiliza una escala de importancia diferente, la comparación se basa en la presencia y la clasificación de las variables, en lugar de en los valores de importancia absolutos.

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
