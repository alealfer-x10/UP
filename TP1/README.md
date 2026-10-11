# UP TP1

## Objetivo del trabajo
A partir de una muestra de datos de 5000 clientes de Netflix, realizar un análisis exploratorio de datos (EDA), para identificar los factores que afectan las "cancelaciones" de servicios.
Para esto, se plantean 5 hipótesis iniciales que guiarán el análisis, con el fin de validar ó rechazar.

### Hipótesis:
1. Los suscritores que tiene baja cantidad de horas mensuales de visualización se cancelan mas.
2. Los suscriptores con mas días sin loguearse, cancelan mas. OK
3. Los suscriptores que NO pagan con tarjetas de Credito|Debito|Paypal, cancelan mas. OK
4. Los suscriptores con mas perfiles, cancelan menos. OK
5. Los suscriptores con mayor edad, cancelan menos.



## Contexto del Dataset

Fuente del Dataset: https://www.kaggle.com/datasets/zeyadmohamed26/netflix-customer-churn-and-engagement-analytics


La pérdida de clientes (pérdida de suscripctores), es uno de los desafíos mas críticos a los que se enfrentan las plataformas globales de streaming.
Adquirir un nuevo cliente suele costar entre 5 y 7 veces mas que retener uno existente.

Este conjunto de datos rastrea la participacón del usuario, la utilización del hardware, los mecanismos de facturación y la inactividad de las cuentas, cuyo objetivo es descubrir:

- INDICADORES DE DESGASTE TEMPRANO: - ¿Qué señales de comportamiento (inactividad de inicio de sesión, disminución de horas de visualización), predicen la pérdida antes de que ocurra.

- VISIBILIDAD POR NIVEL DE SUSCRIPCION: ¿En qué se diferencian las tarifas de abandono entre los planes Básico (U$S 8,99), Standard (U$S 13,99), Premium (U$S 17,99)

- DINAMICAS REGIONALES y DEMOGRAFICAS: ¿Qué mercados geográficos y conjunto de edades, representam el mayor riesgo de retención ó deserción?

- FRICCION EN GATEWAYS DE PAGO: ¿El método de pago (pe.: criptomonedas, tarjeta de regalo vs crédito/débito), afecta al tiempo de retención del cliente?

## Diccionario de Datos
El Dataset consta de 5000 registros únicos de suscriptores, con 14 atributos.

| Nombre columna | Tipo de dato | Rango o valores distintivos | Descripción |
|:---|:---|:---|:---|
|customer_id|string|UUID format (pe.:a9b75100..)|Identificador único de suscriptor anónimo|
|age|integer|18 to 70 years|Edad en años cumplidos|
|gender|string|Female, Male, Other|Autoidentificación demográfica del cliente|
|subscription_type|string|Basic, Standard, Premium|Nivel de suscripción activa|
|watch_hours|float|0.10 to 110.40 hrs|Total de horas acumuladas por mes en streaming|
|last_login_days|integer|0 to 60 days|Cantidad de días transcurridos desde el último login|
|region|string|Africa, Asia, Europe, North America, Oceania, South America|Mercado primario operativo regional|                                    
|device|string|Desktop, Laptop, Mobile, TV, Tablet|Tipo de dispositivo de visualización|
|monthly_fee|float|8.99, 13.99, 17.99 (USD)|Importe facturado mensualmente a la cuenta|
|churned|integer|0 (Active), 1 (Churned)|Si el suscriptor canceló el servicio|
|payment_method|string|Credit Card, Crypto, Debit Card, Gift Card, PayPal|Método de pago registrado en el perfil de facturación|                                
|number_of_profiles|integer|1 to 5|Subperfiles de visualización activos en la cuenta|
|avg_watch_time_per_day|float|0.01 to 4.97 hrs|Tiempo promedio calculado de actividad en streaming|
|favorite_genre|string|Action, Comedy, Drama, Horror, Romance, Sci-Fi, Thriller|Género mas frecuentemente consumido|


## Medología aplicadada
1. Plantéo de las hipótesis que guían el análisis (entre 4 y 5)

2. Carga del dataset y primera interpretación
- Dimensión
- Exploración en distintos segmentos del conjunto de datos
- Tipo de variables y recorrido
- Identificación de variable objetivo (target)
- Identificación de posibles variables que intervengan en las hipótesis planteadas

3. Limpieza e integridad de los datos
- Variables con datos válidos
- Tratamiento de valores duplicados
- Tratamiento de valores nulos
- Valores que toman variables categóricas
 
4. Análisis exploratorio (EDA)
- Representatividad de la variable objetivo (justifiación para el EDA)
- Búsqueda de outliers (valores atípicos)
- Correlación entre las variables
- Visualizaciones

5. Conclusiones
- Corresponder los resultados del análisis con las hipótesis planteadas
- Describir hallazgos relevantes surgidos del análisis
- Elaborar una conclusión final


## Conclusiones y hallazgos relevantes

La tasa de clientes Activos y Cancelados se reparten en un 50% aproximadamente, condición que demanda el análisis para entender los factores y casuísticas que intervienen en los mismos.

De las hipótesis planteadas resulta:
### Hipótesis:
1. Los suscritores que tiene baja cantidad de horas mensuales de visualización se cancelan mas.
Se compueba la hipótesis.
Además se observa que, a partir de 8 horas de acumulado mensual se logra tener una proporción mejor de suscripciones activas. En este sentido, estimular al suscriptor al uso del servicio debería bajar las cancelaciones.

2. Los suscriptores con mas días sin loguearse, cancelan mas.
Se comprueba la hipótesis
En particular se observa que a partir de los 30 días (aproximadamente), del último login, las suscripciones canceladas se incrementan significativamente.

3. Los suscriptores que NO pagan con tarjetas de Credito|Debito|Paypal, cancelan mas.
Se comprueba la hipótesis.
Se observa que el uso de medios de pago mas tradicionales y de facil acceso relativo, logran mejores tasas de activos. En particular, los métodos como Gift Card y Crypto tienen peor retención de suscripciones.

4. Los suscriptores con mas perfiles, cancelan menos.
Se comprueba la hipótesis.
En particular se comprueba un diferencial importante a favor de los activos, con mas de 3 perfiles.

5. Los suscriptores con mayor edad, cancelan menos.
No se comprueba la hipótesis.
No hay una afectación mayor de cancelaciones respecto de la edad. La distribuciòn de Activos y Cancelados es bastante uniforme y coincidente. Sin embargo se encuentra mayor cantidad de activos entre los 32 y 45 años, contra la mayor cantidad de cancelados entre 45 y 55 años.

### Adicionalmente se observan los siguientes:
- Los paquetes de suscripciones superiores, a mencionar, Standard y Premium, tiene mejor relación de activos sobre cancelados. Si consideramos esta observación y la de la hipótesis 4, podríamos considera que las propuestas multi-perfiles, tiene mejor receptividad en los clientes.
- No se evidencian afectaciones sobre las cancelaciones de servicios según: tipo de dispositivos de reproducción de streaming, género de las personas, edad (mencionado en hipótesis 5), regiones geográficas de mercados primarios, género de las propuestas.


### Hallazgos relevantes
#### INSIGHT 1 :
30 dìas del último login representa un cambio abrupto respecto de la retención de las suscripciones activas. Estimular el ingreso a la plataforma dentro de los 30 días representa un diferencial a favor de retener los activos

#### INSIGHT 2 :
Se observa en un grupo de clientes que en contra de lo expuesto anteriormente, con valores elevados de last_login y con acumulado en mensula en horas, entre relativamente bajo a alto, la fidelidad con el servicio es mut grande (95% ACTIVOS, 5% CANCELADOS).
A vista de Netflix podrían considerarse los Super Clientes.
