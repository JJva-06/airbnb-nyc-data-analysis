# Airbnb NYC 2024: Análisis de datos e insights del mercado

## Descripción general

Análisis exploratorio del mercado de Airbnb en Nueva York utilizando datos de 2024. El proyecto busca identificar patrones en precios, reviews, tipos de alojamiento y concentración de listings entre hosts.

Las visualizaciones fueron seleccionadas siguiendo principios del **framework de Cleveland & McGill**, priorizando el tipo de representación gráfica más adecuado según la tarea de análisis y comparación.

## Objetivos

* Analizar la distribución de precios de los alojamientos.
* Comparar los precios entre diferentes barrios.
* Explorar la relación entre precio y número de reviews.
* Analizar la composición de los tipos de alojamiento por barrio.
* Evaluar la concentración de listings entre los diferentes hosts.

## Datos

El dataset (`data/airbnb_nyc_2024.csv`) contiene **36,138 listings** de los 5 distritos de NYC y **16,800 hosts**. Los precios van de $15 a $608 por noche.

> **Nota:** la columna `reviews_per_month` es igual a `number_of_reviews` en ~64% de las filas, por lo que no es confiable. El análisis no la utiliza.

## Visualizaciones

### 1. Distribución de precios

![Distribución de precios](outputs/figures/viz1_distribucion_precios.png)

La distribución presenta una marcada asimetría hacia precios elevados.

* **Mediana:** $122 por noche
* **Media:** $145 por noche
* **75% de los listings:** ≤ $200 por noche

La diferencia de $23 entre la media y la mediana muestra que los alojamientos de precios elevados afectan considerablemente el promedio.

### 2. Ranking de barrios por precio

![Ranking de barrios](outputs/figures/viz2_ranking_barrios.png)

Existen diferencias importantes entre los barrios de NYC (precio mediano por noche).

* **Manhattan:** $189 por noche
* **Bronx:** $54 por noche

El precio mediano de Manhattan es aproximadamente **3.5 veces** el del Bronx.

### 3. Relación entre reviews y precio

![Reviews vs precio](outputs/figures/viz3_reviews_vs_precio.png)

Se observa una relación negativa débil entre el precio y la cantidad de reviews:

* **Correlación:** r = -0.170
* Los listings de **$50–150** acumulan el **50%** de todas las reviews.

Los alojamientos de mayor precio tienden a acumular menos reviews. Una posible explicación es una mayor rotación de huéspedes en el segmento económico, aunque esta relación no implica causalidad.

### 4. Composición por tipo de alojamiento

![Composición por tipo](outputs/figures/viz4_composicion_tipo.png)

La composición del mercado varía considerablemente según el barrio.

| Barrio        | Casa/Depto completo | Habitación privada |
| ------------- | ------------------: | -----------------: |
| Bronx         |               32.7% |              59.4% |
| Queens        |               41.8% |              52.4% |
| Staten Island |               50.1% |              46.1% |
| Brooklyn      |               51.2% |              42.9% |
| Manhattan     |               60.8% |              33.3% |

Manhattan presenta una mayor proporción de alojamientos completos, mientras que en el Bronx predominan las habitaciones privadas.

### 5. Concentración del mercado

![Concentración del mercado](outputs/figures/viz5_concentracion_mercado.png)

El mercado presenta una elevada concentración entre los hosts con mayor número de listings.

* El **1% de los hosts más grandes controla el 28%** de los listings.
* El **92% de los hosts** tiene únicamente 1–2 listings.
* El **80% de los hosts más pequeños** controla apenas el **37%** de los listings.

Esto sugiere la presencia de pocos operadores profesionales de gran escala junto con una amplia cantidad de hosts individuales.

## Conclusiones principales

El análisis muestra que el mercado de Airbnb en NYC presenta diferencias importantes tanto en precios como en la estructura de la oferta.

**1. El precio típico está por debajo del promedio.**
La fuerte asimetría de precios hace que la mediana ($122) sea una medida más representativa del alojamiento típico que la media ($145).

**2. Existe una marcada diferencia geográfica.**
Manhattan presenta precios considerablemente superiores a los del resto del mercado, alcanzando aproximadamente 3.5 veces el precio observado en el Bronx.

**3. El mercado económico concentra mayor actividad de reviews.**
La correlación negativa entre precio y reviews sugiere que los alojamientos de menor precio tienden a acumular más reviews.

**4. La oferta cambia según el barrio.**
La proporción de alojamientos completos frente a habitaciones privadas varía significativamente entre los diferentes distritos.

**5. El mercado está concentrado en pocos hosts grandes.**
Aunque la mayoría de los hosts son pequeños operadores, una proporción muy reducida concentra una parte considerable de los listings.

## Tecnologías

* Python
* Pandas
* NumPy
* Matplotlib
* Jupyter Notebook

## Estructura del proyecto

```text
airbnb-nyc-data-analysis/
│
├── data/
│   └── airbnb_nyc_2024.csv
├── notebooks/
│   └── analysis.ipynb
├── outputs/
│   └── figures/
│
├── .gitignore
├── requirements.txt
└── README.md
```

## Cómo ejecutarlo

Clona el repositorio e instala las dependencias:

```bash
git clone https://github.com/JJva-06/airbnb-nyc-data-analysis.git
cd airbnb-nyc-data-analysis
pip install -r requirements.txt
```

Inicia Jupyter:

```bash
jupyter notebook
```

Luego abre `notebooks/analysis.ipynb` y ejecuta todas las celdas. El notebook lee los datos y guarda las figuras con rutas relativas a `notebooks/`, por lo que debe ejecutarse desde esa carpeta (Jupyter lo hace por defecto).

## Metodología

El proyecto sigue un enfoque de análisis exploratorio de datos. Cada visualización se eligió según la tarea analítica que debía resolver, siguiendo los principios de **Cleveland & McGill** sobre la efectividad de las codificaciones gráficas para comparaciones cuantitativas.

Cada visualización se estructura así:

**Pregunta de negocio → Visualización → Justificación → Insight**

## Autor

José Villanueva
