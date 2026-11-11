# UP TP2

## Descripción del proyecto y objetivo
A partir de la modelización con Machine Learning de los conjuntos de datos entregados, lograr predecir si un individuo es ó no fumador (smoking = 0 - no fumador, smoking = 1 - fumador).


Dichos datos contienen características físicas del individuo, a destacar: género, edad, altura, peso, diámetro de cintura; complementando con información clínica respecto de valores en sangre, valores cardíacos, orina, etc..

Para lograrlo se implemetará un flujo de trabajo según las siguientes etapas:

1. Discovery: carga de los datos a analizar, reconocimiento de las estructuras (tamaño, recuentos, distribuciones), calidad de los datos, recorrido de las variables, tipo de las mismas.
2. EDA (Análisis Exploratorio de Datos): Representación de la variable objetivo, analisis de distribuciones y outliers, correlaciones,impacto sobre la variable objetivo; insumos para el pre procesamiento al entrenamiento.
3. Pre-procesamiento: limpieza de variables y transformaciones sobre las variables.
4. Entrenamiento optimización y validación: entrenamiento de modelos y optimización de parámetros para lograr un objetivo del proyecto que es contar con la métrica F1-score para target=1, maximizada.
5. Generación de predicciones: a partir del modelo optimizado y parametrizado, aplicar el mismo a un juego de datos adicional, generando una nueva variable: "smoking_prediction", con los valores predichos.
## Instrucciones para reproducir el entorno y ejecutar el código



Para implantar el entorno de rerpoducción es necesario:

1. Contar con Python 3.1 ó superior instalado
2. Instalar las librería detalladas en "requirements.txt" con: pip install <path>/requiremenst.txt

Para ejecutar el código, una vez ubicada la estructura de archivos entregada, deben ejecutarse los notebooks entregados en el orden indicado al inicio de cada archivo:

***Orden:***

01_lectura_y_discovery.ipyn


02_eda.ipynb


03_preprocesamiento.ipynb


04_entrenamiento_y_optimizacion.ipynb


05_validacion.ipynb


06_prediccion.ipynb

## Explicación de la estructura de archivos

***Estructura de archivos***

```
Trabajo_practico_2/
├──README.MD: este documento
├──requirements.txt: librería y versionado para crear el entorno de ejecución
├──data-/
|   ├──external/
|   ├──processed/
|   |   ├──preproccesed_smoking_prediction_etiquetado.csv ### Respaldo pre procesado
|   |   ├──smoking_prediciones.csv ### Prediciones a partir de modelo optimizado
|   |   ├──test.joblib ### Conjuntos para validar entrenamiento
|   |   └──train.joblib ### Conjuntos para entrenar modelos
|   ├──raw/ ### Datasets entregados para el proyecto
|   |   ├──smoking_prediction_etiquetado.csv
|   |   └──smoking_prediction_sin_etiquetar.csv
|-models-/ ### Features, umbral de predicciones y molelos entrenados
|   ├──features_XGB_optimizado.joblib
|   ├──features_XGB.joblib
|   ├──mejor_umbral.joblib
|   ├──mod_XGB_optimizado.joblib
|   └──mod_XGB.joblib
|notebooks-/ ### Código del entorno
|   ├──01_lectura_y_discovery.ipynb
|   ├──02_eda.ipynb
|   ├──03_preprocesamiento.ipynb
|   ├──04_entrenamiento_y_optmizacion.ipynb
|   ├──05_validacion.ipynb
|   └──06_prediccion.ipynb
```

En la estructura están todas las piezas componentes del proyecto.
En cada path existe un comentario con el significado del componente ó del conjunto, correspondiente.


## Experimentos, pruebas y cambios

***Entrenamiento***

El entrenamiento está enfocado a entrenar un modelo XGBoost.
Como conjuntos de datos se realiza un split del datasets segùn 70% para train y 30% para test.
Como primer conjunto de Hiperparámetros se utilizaron los siguientes:

n_estimators =300,
learning_rate=0.02,
max_depth=3,
random_state=42

Una situación que se evidencia es que en la importancia relativa de atributos, "gender" es muy dominante (situación que se prevía).
Parte de los ensayos de hiperparámetros utilizados estan mas abajo.

En el intento de disminuir la importancia relativa, se incorporan los hiperparámetros "subsample", "colsample_bylevel", "colsample_bytree", logrando aumentar la importancia de variables como: height(cm), Gtp, weight(kg), serum creatinine, etc.
Con esto se logra que en el proceso de clasificación de las estructura de árboles, tengan peso relativo otras variables.

Una prueba que se ensaya es aumentar el conjunto de entrenamiento, cambiando la distribución a 80% train, 20% test. Esto permitió obtener mejores resultados en el modelo.
Para comprobar la consitencia de esta decisión, se realizó el split con dichas proporciones, pero cambiando varios valores de semillas de aleatoriedad. Lo resultados fueron consistente dejando esta distribución final.


***Ensayos de hiperparáramentros***

XGBoost

clf = XGBClassifier(
    n_estimators = 250,
    learning_rate = 0.03,
    subsample = 0.8,
    colsample_bylevel=0.4,
    colsample_bytree=0.6,
    max_depth=4,
    random_state=42
)


OPTIMIZACION

param_dist = {
    "n_estimators": [50, 100, 150, 200, 250],
    "max_depth": [2,3,4,5],
    "learning_rate": [0.01, 0.02, 0.03, 0.04],
    "subsample": [0.6, 0.7, 0.8],
    "colsample_bylevel": [0.3, 0.4, 0.5],
    "colsample_bytree": [0.5, 0.6, 0.7],
}
"""


param_dist = {
    "n_estimators": [50, 100, 150, 200, 300],
    "max_depth": [4,5,6,7],
    "learning_rate": [0.02, 0.03, 0.04, 0.05],
    "subsample": [0.5, 0.6, 0.7],
    "colsample_bylevel": [0.4, 0.5, 0.6],
    "colsample_bytree": [0.5, 0.6, 0.7],
}

param_dist = {
    "n_estimators": [50, 100, 150, 200, 300],
    "max_depth": [3,4,5,6],
    "learning_rate": [0.02, 0.03, 0.04, 0.05],
    "subsample": [0.7, 0.8, 0.9],
    "colsample_bytree": [0.5, 0.6, 0.7],
    "colsample_bynode": [0.5, 0.6, 0.7],
}



param_dist = {
    "n_estimators": [100, 200, 300, 400],
    "max_depth": [1,3,5],
    "learning_rate": [0.03, 0.04, 0.05],
    "subsample": [0.7, 0.8, 0.9]
}


param_dist = {
    "n_estimators": [400, 450, 500, 550],
    "max_depth": [1,3,5],
    "learning_rate": [0.02, 0.03, 0.05],
    "subsample": [0.7, 0.8, 0.9]
}


param_dist = {
    "n_estimators": [50, 100, 200, 500],
    "max_depth": [3,5,7],
    "learning_rate": [0.01, 0.05, 0.001],
    "subsample": [0.6, 0.8, 1]
}


***

***Umbral de predicción***

1. Obtención de los valores precision, recall, threshold para cada fila: precision, recall, thresholds = precision_recall_curve(y_test, test_pred_proba)
2. Cálculo de F1-score: f1_score = 2 * (precision * recall) / (precision + recall)
3. Obtención del mejor umbral: 
indice_mejor = np.argmax(f1_score[:-1])
mejor_umbral = thresholds[indice_mejor]



## Conclusiones y hallazgos relevantes

***Hallazgos relevantes***
1. La variable "oral", tiene un valor único (constante).
2. Existen 2 variables (hearing(left), hearing(right)) con 2 valores asignados (0.004, 0.008) con mas del 97% con un valor único (0.004), y otra (Urine protein) com mas del 94% de los valores en 0.04.
3. Existen variables discretas, con valores clínicos en 0. Por mas que los valores están transformados, no parecen ser válidos para lo que representa.
    A destacar: eyesight(left), eyesight(right), serum creatinine
4. La variable "serum creatinine" los 2422 valores en cero corresponde al género femenino
5. La eliminación del ID dejó 5448 filas duplicadas.
6. El aumento del conjunto de entrenamiento de 70% a 80% mejoró sustancialmente los valores de entrenamiento.
7. El cambio del umbral de decisión para las predicciones aportó una mejora en el F1-score para smoking=1 de 0.69 a 0.72


***Conclusiones***
La variable 'gender' es la variable mas determinante, especialmente cuando toma el valor 'F', en donde aproximadamente el 96% es no fumador. Determina la variable target en gran medida.

Los experimentos realizados sobre los hiperparámetros del modelo no obtuvieron mejoras significativas, una vez logrado mejorar la importancia relativa de otras variables respecto a 'gender'. Consistente con la conclusión anterior, confirma lo determinante de dicha variable.

El modelo final tiene un F1-score para smoking=1 de 0.72, una vez optimizado el umbral. Dicho umbral representó una mejora de 0.003.
La mejora de este umbral aportó mejoras mas significativas que la experimentación con hiperparámetros.

El aumento de el conjunto de train de 70% a 80% aportó una mejora real de F1-score.