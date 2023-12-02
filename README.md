# Descripción del proyecto

## Integrantes
- Cristian Jaramillo Herrera - CC:1036680346
- Danilo Giraldo Lopez - CC:1007240582
- Juan Felipe Usuga Villegas - CC:1035922312 
- Maria Camila Durango Muñoz - CC:1035234476 


## Reporte tecnico como entrada de blog


## Notebooks

Te encontraras con dos notebooks el primero se llama **diasFestivosColombia.ipynb** es donde se generó el listado de días festivos en Colombia.

El segundo notebook se llama **modeloPredictivo.ipynb** allí se realizaron los entrenamientos, las predicciones y las pruebas.

## Data
Encontraras un archivo **dias_festivos_colombia_2011_2018.csv** con el listado de dias festivos.
El segundo archivo es **predicciones_periodo_2012-2016.csv** con las predicciones del periodo 01/01/2012 y el 31/12/2016
El tercer archivo es **predicciones_periodo_2018.csv** con las predicciones del periodo 01/01/2018 y el 30/06/2018.
El ultimo archivo es **registros_autos_entrenamiento.xlsx** que contiene el dataset inicial con las del numero de autos con su fecha correspondiente



# Reporte Técnico del Modelo

## Introducción
En el actual panorama donde el tiempo equivale a dinero y la rapidez en la toma de decisiones determina el logro de rendimientos deseados, la capacidad de prever y deducir resultados se erige como una ventaja competitiva crucial. Por lo tanto, las técnicas de predicción desempeñan un papel esencial en diversas aplicaciones, como la formulación de estrategias, análisis de riesgos, transacciones comerciales, análisis de patrones, entre otros.
Este trabajo tiene como objetivo crear un modelo predictivo para el número diario de vehículos registrados en el Registro Único Nacional de Tránsito (RUNT), lo que proporciona una ventaja organizativa para el sistema de tránsito nacional al permitir la preparación previa de toda la logística necesaria para cada registro. 

### Objetivo del proyecto:
El objetivo principal de este proyecto es desarrollar un modelo predictivo eficiente, capaz de predecir con precisión el número diario de vehículos registrados, proporcionando así una herramienta de utilidad en la planificación estratégica. Para ello se deben identificar las variables explicativas más influyentes en el proceso de registro de vehículos.

## Desarrollo del Modelo.
### Exploración de Datos 
#### Origen de los datos: 
Se ha cargado un conjunto de datos desde un archivo Excel, mostrando las primeras filas del DataFrame y proporcionando estadísticas descriptivas, lo que nos permite obtener una visión general de la distribución de los registros de vehículos.

#### Análisis temporal: 
Se visualizó la relación temporal entre las variables utilizando un gráfico de líneas, destacando la evolución de los registros diarios a lo largo del tiempo.
![image](https://github.com/crjahe26/prediccion_numero_de_vehiculos/assets/45887686/40f7f8d2-c933-4534-8746-0c55fec99c1b)


#### Construcción del Modelo de Regresión:
Se implementó un modelo de regresión utilizando Random Forest, utilizando variables como la presencia de días festivos, el día de la semana, el día del mes y el mes como predictores.

#### Selección y Preprocesamiento de Variables: Consideraciones Temporales y Días Festivos:

La selección de variables en el desarrollo de nuestro modelo para la predicción del número de vehículos registrados se centra en la incorporación de información temporal y específicamente en la distinción entre días festivos y laborables.

**Variables Temporales:** Se han creado variables temporales adicionales, como 'DiaSemana', 'DiaMes', y 'Mes', con el propósito de capturar patrones estacionales y variaciones mensuales en la cantidad de vehículos registrados. Estas variables permiten al modelo adaptarse a las posibles fluctuaciones que pueden ocurrir en diferentes días de la semana o meses del año.

**Días Festivos como Variable Discernible:** La introducción de la variable 'EsFestivo' proporciona al modelo la capacidad de distinguir entre días festivos y no festivos. Esto es esencial para entender y prever posibles desviaciones en el registro de vehículos en días festivos en comparación con días regulares. La variable binaria actúa como un indicador claro de la presencia o ausencia de eventos festivos, permitiendo al modelo ajustarse a comportamientos específicos asociados con estos días especiales.

**Importancia de Días Festivos:** Al considerar la creación del archivo CSV en un notebook por separado, se garantiza una exploración más detallada y un control refinado sobre la información relacionada con días festivos. Este enfoque no solo añade un componente binario al modelo sino que también destaca la importancia de entender cómo la presencia de días festivos puede influir en la cantidad de vehículos registrados. El modelo aprende y adapta sus predicciones en función de estos eventos, mejorando su capacidad predictiva en contextos diversos.

**Enriquecimiento Contextual:** La inclusión de variables temporales y días festivos no solo amplía la complejidad del modelo, sino que también enriquece su capacidad para contextualizar las predicciones. Al comprender las variaciones a lo largo del tiempo y la presencia de días festivos, el modelo puede ajustarse de manera más precisa a patrones específicos, mejorando la calidad general de las predicciones.

Este enfoque en la selección y preprocesamiento de variables se alinea con la naturaleza temporal de los datos y responde a la necesidad de capturar las variaciones en los registros de vehículos en función del tiempo y eventos específicos. La consideración cuidadosa de estas variables enriquecedoras mejora la robustez y la adaptabilidad del modelo para ofrecer predicciones más precisas y contextualmente relevantes.

## Arquitectura del modelo
La arquitectura del modelo desarrollado para predecir el número de vehículos registrados en el sistema de tránsito nacional sigue un enfoque estructurado y comprensible.


### División de Datos:
   - Se implementa la división de datos en conjuntos de entrenamiento y prueba utilizando la función `train_test_split` de scikit-learn. Esto asegura una evaluación objetiva del rendimiento del modelo.

### Selección y Normalización de Variables:
   - Se seleccionan cuidadosamente las variables explicativas ('EsFestivo', 'DiaSemana', 'DiaMes', 'Mes') para entrenar el modelo.
   - Las variables explicativas se normalizan utilizando `StandardScaler` para garantizar que todas las características tengan la misma escala, evitando sesgos en el proceso de entrenamiento.

### Modelo de Regresión RandomForest:
   - Se opta por un modelo de regresión RandomForest, conocido por su capacidad para manejar relaciones no lineales y gestionar conjuntos de datos complejos.
   - Se realiza una búsqueda de cuadrícula (`GridSearchCV`) para explorar diferentes combinaciones de hiperparámetros del modelo, como el número de estimadores, la profundidad máxima del árbol y otros.

## Entrenamiento del modelo y Evaluación
El modelo se entrena con el conjunto de datos de entrenamiento utilizando los mejores hiperparámetros identificados durante la búsqueda de cuadrícula.

Se realizan predicciones en el conjunto de prueba, y se evalúa el rendimiento del modelo utilizando métricas estándar de regresión, como el Error Absoluto Medio (MAE), el Error Cuadrático Medio (MSE), la Raíz del Error Cuadrático Medio (RMSE), R cuadrado (R2) y el puntaje de varianza explicado.
![image](https://github.com/crjahe26/prediccion_numero_de_vehiculos/assets/45887686/65f589ac-61d6-4403-8a0c-fc7387bb835d)


Mean Absolute Error (MAE): 140.50475958598673
Mean Squared Error (MSE): 39388.22540617718
Root Mean Squared Error (RMSE): 198.46467042316922
R-squared (R2): 0.8653971746780202
Explained Variance Score: 0.8660011340373022
### Importancia de las variables:
| Variable | Importancia |
|----------|----------|
| EsFestivo   | 0.193437   |
| DiaSemana    | 0.606012   |
| DiaMes   |  0.127641   |
| Mes   |  0.072910   |

## Predicción vs Observado
La visualización de las predicciones frente a los valores observados mediante un gráfico de dispersión y líneas conectadas ofrece una representación clara y comprensible de cómo el modelo se ajusta a los datos. Este enfoque facilita la identificación de patrones, tendencias y posibles discrepancias entre las predicciones y los registros reales. 

El gráfico se enfoca en el periodo del 1 de enero de 2012 al 31 de diciembre de 2016. Este enfoque temporal específico permite evaluar el rendimiento del modelo en un conjunto de datos reservado para la validación, proporcionando información crucial sobre su capacidad para generalizar a datos no vistos.
![image](https://github.com/crjahe26/prediccion_numero_de_vehiculos/assets/45887686/774b36c9-342c-47c4-92c7-027485650bad)


### Predicción Periodo 01/01/2018 - 30/06/2018
![image](https://github.com/crjahe26/prediccion_numero_de_vehiculos/assets/45887686/308e5816-a324-4867-a915-2f5da53030ba)


## Resultados 
Los resultados muestran un modelo robusto que puede predecir con precisión los registros de vehículos. El R2 para el conjunto de entrenamiento es del 92.06%, indicando una excelente capacidad de explicar la variabilidad en los datos.

En cuanto a las predicciones para el periodo 2018, no fue posible calcular el R2 debido a la falta de datos suficientes.
## Análisis y Conclusiones

Este análisis proporciona una visión completa de los registros de vehículos en el RUNT de Colombia, destacando la eficacia de un modelo de regresión para predecir el número de unidades registradas diariamente. Sin embargo, es crucial contar con datos suficientes para evaluar y validar adecuadamente el rendimiento del modelo.

Se recomienda la recopilación continua de datos y la evaluación periódica del modelo para mantener su precisión a lo largo del tiempo. Además, se puede explorar la inclusión de más variables o técnicas avanzadas de modelado para mejorar aún más las predicciones.

Este informe proporciona una base para futuros análisis y ajustes en el modelo, contribuyendo así a la toma de decisiones informada en el ámbito de la gestión de registros vehiculares.

