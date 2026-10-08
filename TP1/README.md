# UP TP1

####
Requerido de la letra del problema

 Un archivo README.md con:
o Objetivo del trabajo
o Contexto del dataset
o Diccionario de datos
o Metodología aplicada
o Conclusiones y hallazgos relevantes



####




***   Contexto del Dataset   ***

Fuente del Dataset: https://www.kaggle.com/datasets/zeyadmohamed26/netflix-customer-churn-and-engagement-analytics


La pérdida de clientes (pérdida de suscripctores), es uno de los desafíos mas críticos a los que se enfrentan las plataformas globales de streaming.
Adquirir un nuevo cliente suele costar entre 5 y 7 veces mas que retener uno existente.

Este conjunto de datos rastrea la participacón del usuario, la utilización del hardware, los mecanismos de facturación y la inactividad de las cuentas, cuyo objetivo es descubrir:

- INDICADORES DE DESGASTE TEMPRANO: - ¿Qué señales de comportamiento (inactividad de inicio de sesión, disminución de horas de visualización), predicen la pérdida antes de que ocurra.

- VISIBILIDAD POR NIVEL DE SUSCRIPCION: ¿En qué se diferencian las tarifas de abandono entre los planes Básico (U$S 8,99), Standard (U$S 13,99), Premium (U$S 17,99)

- DINAMICAS REGIONALES y DEMOGRAFICAS: ¿Qué mercados geográficos y conjunto de edades, representam el mayor riesgo de retención ó deserción?

- FRICCION EN GATEWAYS DE PAGO: ¿El método de pago (pe.: criptomonedas, tarjeta de regalo vs crédito/débito), afecta al tiempo de retención del cliente?



*** Diccionario de Datos ***
El Dataset consta de 5000 registros únicos de suscriptores, con 14 atributos.

| First Header  | Second Header |
| ------------- | ------------- |
| Content Cell  | Content Cell  |
| Content Cell  | Content Cell  |


| Nombre columna | Tipo de dato | Rango ó valores distintivos | Descripción |
| c------------d | s----------g | U-------------------------D | I---------. |
age 	                  integer 	    18 to 70 years                Edad en años cumplidos.
gender                  string        Female, Male, Other           Género
subscription_type 	    string        Basic, Standard, Premium      Nivel de suscripción activa.
watch_hours 	          float         0.10 to 110.40 hrs            Total de horas acumuladas por mes en srteaming.
last_login_days     	  integer       0 to 60 days                  Cantidad de días transcurridos desde el último login.
region               	  string        Africa, Asia, Europe,         Mercado primario operativo regional.
                                      North America, Oceania,
                                      South America
device                  string        Desktop, Laptop, Mobile, TV,  Tipo de dispositivo de visualización.
                                      Tablet
monthly_fee             float         8.99, 13.99, 17.99 (USD)      Regular monthly recurring fee billed to account.
churned                 integer       0 (Active), 1 (Churned)       Target variable: whether subscriber cancelled service.
payment_method          string        Credit Card, Crypto,          Payment method registered on the billing profile.
                                      Debit Card, Gift Card, PayPal
number_of_profiles      integer       1 to 5                        Active viewer sub-profiles on account.
avg_watch_time_per_day  float         0.01 to 4.97 hrs              Calculated daily streaming engagement average.
favorite_genre          string        Action, Comedy, Drama, Horror,
                                      Romance, Sci-Fi, Thriller     Most frequently streamed content genre.
