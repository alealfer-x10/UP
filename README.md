# UP TP1

Objetivo del trabajo:

*** DATASET ***
CONTEXTO:
  La pérdida de clientes (abandono de suscriptores) es uno de los desafíos más críticos que enfrentan 
las plataformas de streaming globales. 
  Adquirir un nuevo cliente suele costar entre 5 y 7 veces más que retener a uno existente.

Fuente: https://www.kaggle.com/datasets/zeyadmohamed26/netflix-customer-churn-and-engagement-analytics

El dataset contiene 5000 registros únicos de suscriptores y ningún valor perdido.

DICCIONARIO DE DATOS

Nombre columna          Tipo de dato          Rango ó valores distintivos        Descripción 
**********************  ************          ********************************   ************************************************************
customer_id 	          string                UUID                               Identificador único de suscriptor, anónimo.
age 	                  integer 	            18 to 70 years                     Edad en años cumplidos.
gender                  string                Female, Male, Other                Género.
subscription_type 	    string               	Basic, Standard, Premium           Nivel de suscripción activa.
watch_hours 	          float               	0.10 to 110.40 hrs                 Total de horas acumuladas por mes en srteaming.
last_login_days     	  integer             	0 to 60 days                       Cantidad de días transcurridos desde el último login.
region               	  string                Africa, Asia, Europe,              Mercado primario operativo regional.
                                              North America, Oceania,
                                              South America
device                  string                Desktop, Laptop, Mobile, TV,       Tipo de dispositivo de visualización.
                                              Tablet
monthly_fee             float                 8.99, 13.99, 17.99 (USD)           Regular monthly recurring fee billed to account.
churned                 integer               0 (Active), 1 (Churned)            Target variable: whether subscriber cancelled service.
payment_method          string                Credit Card, Crypto, Debit Card,   Payment method registered on the billing profile.
                                              Gift Card, PayPal
number_of_profiles      integer               1 to 5                             Active viewer sub-profiles on account.
avg_watch_time_per_day  float                 0.01 to 4.97 hrs                   Calculated daily streaming engagement average.
favorite_genre          string                Action, Comedy, Drama, Horror,
                                              Romance, Sci-Fi, Thriller          Most frequently streamed content genre.
