# FoodDeliveryML — Análisis exploratorio de tiempos de entrega

**Diplomatura en Inteligencia Artificial — Universidad de Palermo**  
**Trabajo Práctico N.º 1 — Análisis Exploratorio de Datos (EDA)**

## 1. Descripción del proyecto

FoodDeliveryML es un proyecto de análisis exploratorio de datos orientado al estudio de los tiempos de entrega de pedidos de comida.

Se utiliza un dataset de **50.000 registros y 24 variables** para analizar la calidad de los datos, describir sus distribuciones e identificar asociaciones entre el tiempo de entrega y diferentes factores logísticos y operativos.

El análisis se desarrolla con Python, pandas, NumPy, Matplotlib y Seaborn.

**Alcance:** análisis estadístico descriptivo y exploratorio. El desarrollo de modelos predictivos queda fuera del alcance de esta entrega.

## 2. Objetivos

### Objetivo general

Analizar los factores asociados con el tiempo de entrega de pedidos de comida mediante técnicas de estadística descriptiva y visualización de datos.

### Objetivos específicos

- Examinar la estructura, los tipos de datos y la calidad del dataset.
- Identificar valores faltantes, registros duplicados, inconsistencias y valores atípicos.
- Caracterizar las distribuciones de las principales variables numéricas.
- Estudiar asociaciones entre variables numéricas y categóricas.
- Evaluar cinco hipótesis de investigación.
- Documentar los resultados, las limitaciones y las conclusiones.

## 3. Fuente y características del dataset

**Dataset:** Food Delivery Time Prediction Dataset  
**Fuente:** [Kaggle — Food Delivery Time Prediction Dataset](https://www.kaggle.com/datasets/dharmendrapandit12/food-delivery-time-prediction-dataset)

El conjunto de datos contiene 50.000 pedidos correspondientes al año 2025 y 24 variables de naturaleza numérica, categórica y temporal.

La variable principal del estudio es `Time_taken_min`, que representa el tiempo total de entrega expresado en minutos.

El dataset original se utiliza como punto de partida para las verificaciones de calidad y la preparación de los datos.

## 4. Diccionario de datos

La siguiente tabla describe las 24 variables y los tipos identificados durante la inspección inicial.

| Variable | Tipo original | Descripción |
|---|---|---|
| `Order_ID` | str | Identificador del pedido. |
| `Order_Date` | str | Fecha del pedido; se convierte a formato de fecha durante la preparación. |
| `Order_Hour` | int64 | Hora del día en que se realizó el pedido. |
| `Day_of_Week` | str | Día de la semana correspondiente al pedido. |
| `Is_Weekend` | int64 | Indicador binario de fin de semana. |
| `Is_Festival` | int64 | Indicador binario de festividad. |
| `Weather` | str | Condición climática asociada al pedido. |
| `Pickup_Zone` | str | Zona de recogida del pedido. |
| `Dropoff_Zone` | str | Zona de destino de la entrega. |
| `Vehicle_Type` | str | Tipo de vehículo utilizado por el repartidor. |
| `Rider_Experience_Years` | float64 | Experiencia del repartidor, expresada en años. |
| `Rider_Rating` | float64 | Calificación del repartidor. |
| `Restaurant_Rating` | float64 | Calificación del restaurante. |
| `Cuisine_Type` | str | Tipo de cocina del restaurante. |
| `Order_Items` | int64 | Cantidad de artículos incluidos en el pedido. |
| `Restaurant_Load` | str | Nivel de carga operativa del restaurante. |
| `Preparation_Time_Min` | int64 | Tiempo de preparación del pedido, en minutos. |
| `Road_Distance_km` | float64 | Distancia del recorrido por carretera, en kilómetros. |
| `Delivery_Distance_Category` | str | Categoría de distancia de entrega. |
| `Traffic_Level` | str | Nivel de congestión del tráfico. |
| `Number_of_Signals` | int64 | Cantidad de señales de tránsito consideradas en el recorrido. |
| `Average_Speed_kmph` | float64 | Velocidad promedio de desplazamiento, en km/h. |
| `Delivery_Priority` | str | Categoría de prioridad del pedido. |
| `Time_taken_min` | int64 | Tiempo total de entrega, en minutos. Variable objetivo. |

**Nota:** los tipos corresponden a la inspección inicial. Los indicadores `Is_Weekend` e `Is_Festival`, aunque se almacenan como enteros, representan categorías binarias. Las descripciones funcionales se basan en los nombres de las variables y su utilización en el análisis.

## 5. Hipótesis de investigación

Se formularon cinco hipótesis antes de realizar el análisis exploratorio:

**H1 — Distancia:** los pedidos con mayor distancia recorrida tienden a presentar mayores tiempos de entrega.

**H2 — Tráfico:** los niveles superiores de congestión se asocian con mayores tiempos de entrega.

**H3 — Preparación:** los mayores tiempos de preparación se asocian con mayores tiempos totales de entrega.

**H4 — Velocidad:** las mayores velocidades promedio se asocian con menores tiempos de entrega.

**H5 — Condiciones operativas:** el clima, la carga del restaurante, la prioridad de entrega y la hora del pedido presentan asociaciones con el tiempo total de entrega.

Estas hipótesis se evalúan mediante evidencia estadística descriptiva y visualizaciones, sin atribuir causalidad.

## 6. Metodología

El trabajo se desarrolla en dos notebooks ejecutados secuencialmente.

### 6.1. Comprensión y preparación de los datos

**Archivo:** `notebooks/01_data_understanding.ipynb`

Se realizan las siguientes tareas:

1. Carga e inspección inicial del dataset.
2. Identificación de dimensiones y tipos de variables.
3. Verificación de valores faltantes y registros duplicados.
4. Evaluación de fechas, consistencia temporal y valores inválidos.
5. Conversión de `Order_Date` a formato de fecha.
6. Exportación del dataset preparado para el análisis exploratorio.

Las verificaciones realizadas no identificaron valores faltantes, registros completamente duplicados ni inconsistencias en las reglas de calidad examinadas.

Por este motivo, no fue necesario aplicar imputaciones ni eliminar observaciones por esas causas.

### 6.2. Análisis exploratorio de datos

**Archivo:** `notebooks/02_analisis_exploratorio.ipynb`

Se utilizan estadísticas descriptivas, análisis de correlaciones y once visualizaciones principales:

| Técnica | Cantidad |
|---|---:|
| Histogramas con KDE | 3 |
| Diagramas de caja (*boxplots*) | 3 |
| Gráficos de dispersión (*scatterplots*) | 2 |
| Mapa de calor de correlaciones | 1 |
| Gráfico de barras por clima | 1 |
| Gráfico de líneas por hora | 1 |
| **Total** | **11** |

El análisis se complementa con tablas descriptivas por nivel de tráfico, carga del restaurante y prioridad de entrega.

## 7. Principales resultados

### 7.1. Distribución del tiempo de entrega

| Estadística | Resultado |
|---|---:|
| Media | 83,87 minutos |
| Mediana | 78 minutos |
| Desviación estándar | 35,43 minutos |
| Mínimo | 10 minutos |
| Máximo | 180 minutos |

La distribución presenta asimetría positiva.

Se identificaron 1.661 registros con un tiempo exactamente igual a 180 minutos (3,32 % del dataset). Esta acumulación podría indicar un límite aplicado a los datos, aunque no existe evidencia suficiente para confirmar su origen.

### 7.2. Distancia y tiempo de entrega

La distancia recorrida presenta una correlación lineal positiva fuerte con el tiempo de entrega:

**Coeficiente de Pearson: r = 0,703.**

Los pedidos de mayor distancia tienden a presentar tiempos de entrega superiores.

### 7.3. Congestión del tráfico

| Nivel de tráfico | Tiempo medio |
|---|---:|
| Low | 76,44 min |
| Moderate | 92,30 min |
| High | 111,73 min |
| Severe | 134,40 min |

Los tiempos medios aumentan progresivamente con el nivel de congestión.

La diferencia entre tráfico bajo y severo es de **57,96 minutos**.

### 7.4. Tiempo de preparación

El tiempo de preparación presenta una asociación lineal positiva débil con el tiempo total de entrega:

**Coeficiente de Pearson: r = 0,228.**

### 7.5. Velocidad promedio

La velocidad promedio presenta una asociación lineal negativa considerable con el tiempo de entrega:

**Coeficiente de Pearson: r ≈ -0,60.**

Su posible utilización en futuros modelos predictivos requiere verificar si la variable estaría disponible al momento de realizar la predicción, para evitar una eventual fuga de información (*data leakage*).

### 7.6. Condiciones climáticas

| Condición | Tiempo medio |
|---|---:|
| Clear | 77,30 min |
| Cloudy | 79,02 min |
| Fog | 84,15 min |
| Rain | 98,86 min |
| Storm | 114,45 min |

Las entregas realizadas durante tormentas presentan un tiempo medio **37,15 minutos superior** al registrado con clima despejado.

### 7.7. Hora del pedido, carga del restaurante y prioridad

Se identificaron tiempos medios relativamente elevados entre las 08:00 y las 10:00 y entre las 18:00 y las 21:00.

Los restaurantes con carga alta presentan un tiempo medio 3,91 minutos superior al de aquellos con carga baja.

Los pedidos VIP registran un tiempo medio 2,07 minutos inferior al de los pedidos normales.

Estas diferencias son descriptivas y no permiten establecer relaciones causales.

## 8. Evaluación de hipótesis

| Hipótesis | Resultado descriptivo |
|---|---|
| H1 — Distancia | Respaldada: asociación positiva fuerte. |
| H2 — Tráfico | Respaldada: incremento progresivo de los tiempos medios. |
| H3 — Preparación | Respaldada parcialmente: asociación positiva débil. |
| H4 — Velocidad | Respaldada: asociación negativa considerable. |
| H5 — Condiciones operativas | Respaldada descriptivamente, con diferencias de distinta magnitud. |

Los resultados no constituyen pruebas de causalidad ni permiten afirmar significación estadística por sí solos.

## 9. Limitaciones

El análisis presenta las siguientes limitaciones:

- **Naturaleza observacional:** las asociaciones identificadas no demuestran causalidad.
- **Concentración en el valor máximo:** el 3,32 % de los registros presenta exactamente 180 minutos.
- **Desequilibrio de categorías:** el 94,48 % de los pedidos pertenece a la categoría de distancia `Long`.
- **Tamaños de grupo diferentes:** algunas categorías contienen considerablemente menos registros.
- **Disponibilidad temporal de variables:** determinadas características podrían no conocerse al momento de una predicción.
- **Alcance temporal y contextual:** los datos corresponden a 2025 y no garantizan la generalización a otros períodos o contextos.

## 10. Estructura del proyecto

```text
FoodDeliveryML/
├── data/
│   ├── raw/
│   │   └── Food_Delivery_Time_Prediction.csv
│   └── processed/
│       └── food_delivery_prepared.csv
├── notebooks/
│   ├── 01_data_understanding.ipynb
│   └── 02_analisis_exploratorio.ipynb
├── models/
├── src/
├── .gitignore
├── requirements.txt
└── README.md
```

Las carpetas `models/` y `src/` están reservadas para posibles ampliaciones posteriores.

## 11. Tecnologías utilizadas

- Python 3.12
- pandas
- NumPy
- Matplotlib
- Seaborn
- Jupyter Notebook

## 12. Instalación y ejecución

### 12.1. Clonar el repositorio

```bash
git clone https://github.com/ignacioalcaniz/FoodDeliveryML.git
cd FoodDeliveryML
```

### 12.2. Crear un entorno virtual

En Windows:

```powershell
python -m venv .venv
.venv\Scripts\activate
```

### 12.3. Instalar las dependencias

```bash
pip install -r requirements.txt
```

### 12.4. Iniciar Jupyter Notebook

```bash
jupyter notebook
```

### 12.5. Ejecutar los notebooks

Ejecutar en el siguiente orden:

1. `notebooks/01_data_understanding.ipynb`
2. `notebooks/02_analisis_exploratorio.ipynb`

El primer notebook genera el archivo preparado que utiliza el segundo.

Para reproducir el proceso desde el comienzo, el CSV original debe estar disponible en `data/raw/`, respetando el nombre y la estructura utilizados por el notebook 01.

## 13. Conclusiones

El análisis exploratorio permitió caracterizar un dataset de 50.000 pedidos, evaluar su calidad e identificar asociaciones relevantes entre el tiempo de entrega y diversas variables logísticas y operativas.

La distancia recorrida, el nivel de tráfico, las condiciones climáticas y la velocidad promedio destacan entre las variables estudiadas por sus asociaciones descriptivas con el tiempo de entrega.

Las cinco hipótesis pudieron evaluarse a partir de los resultados obtenidos, aunque la intensidad de las asociaciones varía según el factor analizado.

El trabajo proporciona una base documentada y reproducible para futuras investigaciones y posibles modelos predictivos, siempre que se consideren las limitaciones metodológicas y la disponibilidad temporal de las variables.