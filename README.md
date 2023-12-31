<p align="center"><img src="./images/OIG.Lo7.dES.jpeg"></p>

# Proyecto Individual N°2

## Telecomunicaciones (Data Analytics)

### Bruno Zenobio, DATAFT16

---

## **Tabla de Contenidos**

- [Introducción](#introducción)
- [Desarrollo](#desarrollo)
    - [ETL](#exploración-transformación-y-carga-etl)
    - [EDA](#análisis-exploratorio-eda)
    - [Estudio](#hilo-de-estudio)
- [Conclusión](#conclusión)
- [Bibliografias](#bibliografias)
- [Contacto](#contacto)

## **Tecnolgías usadas**

![](https://img.shields.io/static/v1?label=Python&message=3.11.6&color=brightgreen)
![](https://img.shields.io/static/v1?label=Pandas&message=2.0.3&color=brightgreen)
![](https://img.shields.io/static/v1?label=Matplotlib&message=3.7.2&color=brightgreen)
![](https://img.shields.io/static/v1?label=Seaborn&message=0.12.2&color=brightgreen)
![](https://img.shields.io/static/v1?label=Power+BI&message=Desktop&color=brightgreen)







- ## **Links**
    - [Carpeta con los dataset](./datasets/)
    - [Proceso de ETL y EDA](./EDA.ipynb)
    - [Dashboard Power BI](./Dashboard/.)

---

# Introducción

A continuación se presentará un estudio realizado sobre las telecomunicaciones en Argentina, principalmente el acceso a internet, comprendido entre los años 2014 y 2022, abordando tasas de conexiones, velocidades y su relación en ambas para un estudio más profundo en algunas provincias.

1. **Extracción, transformación y carga (ETL):** A partir de la página de ENACOM se realizará la extracción de los datos referentes a los accesos a internet, también a partir de la página, además a partir del Instituto Geográfico Nacional (IGN) se extraerán datos referentes a la superficie y población de distintas provincias. Luego se realizará un breve proceso de transformación, ya que los datos de fuente ya venían limpios. Por último, se llevará a cabo la carga a una base de datos MySQL.

2. **Análisis de Datos:** Con los datos ya preparados, se procederá a realizar un análisis sobre estos, siguiendo un hilo específico, basado en KPI definidos propiamente para el contexto.

---

# Desarrollo

### Exploración, Transformación y Carga (ETL)

Se obtuvieron 16 tablas guardando información a nivel provincial y nacional, de las cuales estaban divididas en:


- **`Penetración de internet`**: Referente a los accesos a internet cada 100 hogares y 100 habitantes.
- **`Internet Banda ancha fija y Dial Up`**: Accesos a través de banda ancha y dial-up.
- **`Accesos por tecnología`**: Accesos en función de las distintas tecnologías **ADSL, Cablemódem, Fibra Óptica, Wireless, Otros**.
- **`Histórico de velocidad`**: Velocidad media de bajada, desde 2014 a 2022.
- **`Accesos por velocidad`**: Cantidad de accesos para distintas velocidades o rangos de estas.
- **`Ingresos`**: Ingresos solo a nivel nacional.
- **`Accesos por localidad`**: Accesos por localidad para distintas velocidades y otra tabla pero para distintas tecnologías.
- **`Mapa de conectividad`**: Tabla con información sobre la presencia de distintas tecnologías, y datos como población para distintas localidades en el año 2023.
- **`Población y area de cada provincia`**: Datos extraidos del IGN, con información sobre cada provincia, su area y su población.

#### En cuanto al proceso de ETL, se realizó una leve limpieza de los datos, realizando tareas como: explicación de algunos outliers, valores nulos y normalización.

### Análisis Exploratorio (EDA)

A partir de los datos se hizo un proceso de EDA, para comprender la distribución de estos y analizar tendencias y patrones para el estudio. Dentro de este se realizaron análisis como:

- ## **`Penetración por cada 100 hogares y 100 habitantes Anual`**:

<img  src='./images/Graficos EDA/Pentracion_por años.png'  width="1000" height="500"></img>


En este gráfico, se pueden observar los accesos cada 100 hogares representados por la línea azul y los accesos cada 100 habitantes representados por la línea naranja. Se aprecia un aumento progresivo a lo largo de los años, con un pico significativo entre julio y diciembre de 2020. Este aumento podría deberse a la creciente demanda de servicios de internet durante el período de confinamiento durante la pandemia.


- ## **`Distribución de accesos por provincias`**:

<img  src='./images/Graficos EDA/outlieres_.png' width="700" height="500"></img>

En el gráfico se muestra la distribución de los accesos por cada 100 hogares en diferentes provincias, con algunos valores atípicos en Mendoza y Neuquén. Al analizar estos valores, se nota que corresponden al año 2020, cuando se registró un pico nacional de accesos. Este aumento se atribuye al Plan Nacional de Conectividad (Conectar), que impulsó el desarrollo de tecnologías para mejorar el acceso a internet.


- ## **`Accesos anuales por tecnologías`**:

<img  src='./images/Graficos EDA/anual_por_tecnologia.png' width="700" height="500"></img>

Desde el año 2014 hasta el 2022, se observa un crecimiento general en diversas tecnologías y las variaciones entre ellas. El ADSL (conexión por cable telefónico) dominó desde el 2014 hasta el 2017. Sin embargo, con la llegada de nuevas tecnologías como el Cablemódem, comenzó a ser reemplazado debido a su mayor eficiencia. La Fibra Óptica, considerada una de las mejores tecnologías en la actualidad, empezó a expandirse a partir del 2018. A pesar de su elevado costo en comparación con el cablemódem, su adopción se aceleró a principios de 2021. Aunque aún es superada en número de accesos por el cablemódem, se estima que en unos años se convertirá en la tecnología de elección.

Según el ENACOM, a partir del 2019 se registró un aumento significativo del 220% en el uso de la fibra óptica ([Noticia ENACOM](https://www.baenegocios.com/negocios/El-desafio-de-la-Argentina-en-el-camino-de-la-fibra-optica-20200610-0092.html)).


- ## **`Tecnologías en 2020 y 2022`**:

<img  src='./images/Graficos EDA/tecnologia_2020y2022.png' width="900" height="500"></img>


Como se mencionó anteriormente desde el año 2021 la fibra óptica comenzó a esparcirse de manera más acelerada, puede ver esto en el siguiente gráfico donde vemos a la derecha los porcentajes de accesos para el año 2020 y a la izquierda el año 2022, donde vemos que la fibra óptica tuvo un aumento de casi el 9% mientras que el cablemódem disminuyó en un 2% y ADSL que ya venía en decrecimiento un 6%.

- ## **`Accesos con más de 30 Mbps`**:

<img  src='./images/Graficos EDA/accesos_mas30mbps.png' width="700" height="500"></img>

Como antes se había mencionado a partir del año 2018 donde la fibra óptica comenzó a aumentar junto a cablemódem y el ADSL comenzó a caer bruscamente se puede observar para este año un aumento significativo de los accesos con más de 30 Mbps, velocidad que ya se empezaba a esparcir de forma común y no tan selectiva en sectores de alta conectividad.

- ## **`Relación por provincia de los accesos por tecnologías`**:

<img  src='./images/Graficos EDA/relacion_acceso_velocidad.png'></img>

Se puede observar en el gráfico de arriba la velocidad media de bajada en cada provincia a partir del año 2021, donde podemos observar provincias con una velocidad por debajo de la mitad de la media, tales como Chubut, La Pampa, San Juan, Santa Cruz, Tierra del Fuego y Santiago del Estero. Observando estas provincias en el gráfico de abajo (tasa de acceso por 100 hogares) se observa que Chubut, La Pampa, San Luis y Tierra del Fuego tienen una tasa de accesos superior a la media nacional. Esto podría traducirse como una demanda insatisfecha, debido a que estamos en un contexto social donde los accesos a internet y de alta calidad son esenciales, por ejemplo: servicios de streaming, trabajos remotos, videojuegos, etc. Por esto tener una calidad alta en el acceso a internet es fundamental, y más teniendo en cuenta si la tasa de acceso es elevada.

- ## **`Análisis de las provincias con alta tasa de acceso y velocidad baja`**:

<img  src='./images/Graficos EDA/tecnologias_provincias_destacadas.png'></img>

En vista de lo anterior mencionado, un estudio más profundo sobre estas provincias nos indica que tecnologías como la fibra óptica no están siendo muy fructíferas en los últimos años, y en algunas de estas el internet por Wireless fue elevado, lo cual podría deberse a que es la tecnología más óptica alcanzada. Por esto, para cumplir esta demanda podrían proponerse mejoras en las accesibilidades para estas zonas.

- ## **`Densidad poblacional`**:

<img  src='./images/Graficos EDA/densidad_poblacional.png'></img>

Estudiando la densidad poblacional en cada provincia, podemos decir que las mencionadas e importantes para este último análisis, tienen una densidad media de 3 personas por km². Demás está decir que este número no es tan catastrófico ya que no solemos considerar una distribución uniforme, sino agrupaciones por ciudades. Aun así estamos ante una baja población y una alta tasa de accesos. Esto se traducirá que aplicar tecnologías como Fibra Óptica generaría un costo en infraestructura y mantenimiento muy elevado, ya que esta requiere alcanzar con los cables cada lugar de acceso, por ende ante estas densidades poblacionales no sería muy conveniente. Es por esto que podría analizarse el caso de usar alternativas como Wireless, ya que utiliza ondas de radio para llevar que luego son captadas por los dispositivos, lo cual ya no requiere extender un cable por cada hogar, esto reduce los costos considerablemente, y si bien es verdad que el Wireless no es tan estable o rápido como la fibra óptica, sí podría lograrse aumentar eficiencia considerablemente y llegar a pertenecer a la media nacional.

### Hilo de estudio

En el contexto de todo lo mencionado, el análisis estará orientado a los accesos a internet y la relación con la velocidad media de bajada, proponiendo tecnologías alternativas en los casos que sea requerido. Para esto se propusieron los siguientes **KPI** (indicadores clave de rendimiento) elegidos en función de lo anteriormente presentado, considerando cada punto clave que puede impulsar a los servicios de telecomunicaciones.


## **`KPI:`**

- **`Aumento de Accesos:`** Aumentar en un 2% la tasa de acceso por cada 100 hogares trimestralmente.

- **`Optimización de Conectividad:`** Basándome en lo observado en las gráficas [Accesos anuales por tecnologías](#accesos-anuales-por-tecnologías) y [Porcentaje tecnologías años 2020 y 2022](#tecnologías-en-2020-y-2022), se busca no solo incrementar el acceso a Internet, sino también mejorar la eficiencia mediante el aumento del uso de fibra óptica en lugar de cablemódem. El objetivo es que el porcentaje de fibra óptica con respecto al total de conexiones (fibra óptica y cablemódem) crezca anualmente en un 10%.

- **`Mejora de Velocidad:`** Observando el crecimiento de accesos con 30 Mbps ( [Accesos con mas de 30 Mbps](#accesos-con-más-de-30-mbps)) o más a partir de 2018, y considerando la velocidad media de bajada que supera los 40 Mbps desde 2021 ([Comparación velocidad media tasa de accesos](#relación-por-provincia-de-los-accesos-por-tecnologías)), se espera un aumento considerable debido a la eficiencia de las nuevas tecnologías. Por lo tanto, se propone incrementar la velocidad media de descarga en un 30% anualmente.

- **`Ampliación de Accesos Inalámbricos:`** En ciertas provincias se observa una tasa de penetración por encima de la media, pero una velocidad media de bajada significativamente baja, como se muestra en la figura [Comparación velocidad media tasa de accesos](#relación-por-provincia-de-los-accesos-por-tecnologías). Además, considerando la información proporcionada en la figura [Densidad poblacional](#densidad-poblacional), tecnologías como la fibra óptica podrían no ser la mejor opción para estas zonas rurales. Por tanto, se establece como objetivo aumentar los accesos a través de tecnología inalámbrica en un 3% por trimestre para estas provincias.



El análisis en cuestión se llevó a cabo utilizando un dashboard en Power BI. Puedes acceder a la carpeta que contiene el dashboard completo [aquí](./Dashboard):

- **`Hoja 1: Presentación del Informe`**: Esta sección proporciona una introducción al informe.

- **`Hoja 2: Estudio General de Accesos`**: En esta hoja, se realiza un análisis general de los accesos a lo largo de los años y por provincias. Se utilizan los KPIs de Aumento de Accesos y Cambio de Cablemódem a Fibra Óptica.

- **`Hoja 3: Comparativa de Accesos y Velocidad Media de Bajada`**: Esta hoja presenta una comparación entre los accesos y la velocidad media de bajada. Se identifican provincias para un estudio más detallado en la Hoja 4. Además, se utiliza el KPI de Cambio en la Velocidad Media de Bajada.

- **`Hoja 4: Estudio Detallado para Provincias Destacadas`**: Se analizan en profundidad algunas provincias que muestran una tasa de acceso por encima de la media nacional pero una velocidad media de bajada considerablemente baja. Se propone el KPI de Aumento a través de Tecnología Inalámbrica debido a la baja densidad poblacional en estas áreas.


### Conclusión

Como conclusión, se puede observar que en los últimos años ha habido un crecimiento significativo en el acceso a Internet, impulsado por una alta demanda. Esta creciente demanda implica la necesidad de velocidades de acceso cada vez más elevadas para adaptarse a las implicancias actuales del mundo moderno. En este contexto, optar por tecnologías que contribuyan a este desarrollo, como la fibra óptica, no solo es evidente en su crecimiento, sino que también se presenta como una opción viable debido a su alta efectividad. La fibra óptica es especialmente adecuada para zonas urbanas o densamente pobladas, mientras que las conexiones inalámbricas son ideales para áreas rurales que también experimentan una demanda creciente de estos servicios.

Es crucial tener en cuenta un dato muy importante: este análisis debe complementarse necesariamente con un estudio sobre los ingresos y costos asociados a este desarrollo para poder cuantificar el retorno de la inversión al aplicar estas tecnologías. Este enfoque integral permitirá evaluar adecuadamente la viabilidad y sostenibilidad de implementar estas soluciones, asegurando así un acceso a Internet rápido y confiable para diferentes tipos de áreas y comunidades.


## Bibliografias
- [Instituto geografico nacional](https://www.ign.gob.ar/)
- [ENACOM](https://www.baenegocios.com/negocios/El-desafio-de-la-Argentina-en-el-camino-de-la-fibra-optica-20200610-0092.html)

## Contacto

<div style="display: flex; align-items: center;">
  <a href="https://www.linkedin.com/in/brunozenobio/" style="margin-right: 10px;">
    <img src="./images/in_linked_linkedin_media_social_icon_124259.png" alt="LinkedIn" width="40" height="40">
  </a>
  <a href="mailto:brunozenobio4@gmail.com" style="margin-right: 10px;">
    <img src="./images/gmail_new_logo_icon_159149.png" alt="Gmail" width="40" height="40">
  </a>
</div>
