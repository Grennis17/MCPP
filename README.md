# La Desigualdad en la Educación

![Colombia](https://user-images.githubusercontent.com/103537621/204023094-f6e1bfd9-33a4-431f-a376-69af95eda993.jpeg)



## Descripción y Motivación

La educación es una de las herramientas más poderosas para disminuir la desigualdad y promover la mobilidad social, con el potencial de romper el cíclo  de pobreza y marginalización intergeneracional. Sin embargo, diferencias en el acceso a la educación y la calidad de esta, plantean un desafío enorme para la igualdad de oportunidad. Por lo tanto, identificar las barreras a la educación y los factores que impactan la calidad de la enseñanza, además de la capacidad de aprendizaje por parte de los estudiantes, es un importante primer paso. 

Yo pretendo hacer esto a través de una análisis de las diferencias socioeconómicos que existen entre los estudiantes a los niveles de la famila y entre colegios, utilizando los resultados (microdatos) del examen _Saber 11_ del año 2021. Es importante tener en cuenta que en este año, la mayoría de las instituciones educativas habían sido cerradas desde el brote de la pandemia del COVID-19 en marzo de 2020 y las clases se desarrollaron si acaso de manera virtual o en lo absoluto.

Este examen se presenta por estudiantes del 11 grado en Colombia y es necesario para poder acceder a la educación superior ('_leaving exam_') y consiste en cinco partes: Matemáticas, Inglés, Lectura Criticia, Ciencias Naturales y Ciencias Sociales. El total de estas da una nota sobre 500, la cual es conocida como el 'Puntaje Global'. Antes de empezar el examen, los estudiantes deben rellenar una encuesta sobre las condiciones socioeconómicas del hogar, y en adición, las características del colegio son guardadas, ofreciendo una riqueza de datos a nivel individual. Junto con datos relacionados a la educación y la economía al nivel departamental, se desarrolla este análisis en estas dimensiones también.

### Preguntas de investigación:

¿Cómo los recursos económicos de la familia afectan el rendimiento escolar?

¿Cómo el estatus del colegio afecta la calidad del aprendizaje?

¿Cómo son las características socioeconómicas del municipio o departamento relacionadas con el desempeño promedio de estudiantes?


El Puntaje Global será la variable principal de interés, dado que indica el desempeño general de los estudiantes al graduarse de bachiller, y se considera un 'proxy' para evaluar la calidad de la ensenañza de los colegios.

---
## Méotodos Utilizados

### Descarga de las bases de datos

"**Resultados Individuals de Saber 11**" -  Las bases de datos principales están disponibles en la página de ICFES: https://www2.icfes.gov.co/web/guest/resultados-individuales-saber-11. (Hay que crear una cuenta para poder accederlas). 

Como hay dos opciones de fecha para presentar el examan dependiendo del calendario del colegio, hay dos archivos de texto por cada año. Los descargué para el año 2021.

También accedé a la base de datos del Ministerio de Educación, _Estadísticas en Educación_ ,a través del protocolo Socrata Open Data API (SODA). Disponible en el sitio de Datos Abiertos: https://www.datos.gov.co/Educaci-n/MEN_ESTADISTICAS_EN_EDUCACION_EN_PREESCOLAR-B-SICA/nudc-7mev.

Por útlimo, descargué la base de datos de Cuentas Nacionales del DANE, para  https://www.dane.gov.co/index.php/estadisticas-por-tema/cuentas-nacionales/cuentas-nacionales-departamentales.  

### Depuración de los datos

Utilicé _pandas_ en _Python_ para crear y manejar las bases de datos: 
- Convertí los archivos .txt a _Data Frames_ y los uní para crear una base grande. El código está disponible [aquí].
- Eliminé las columnas innecesarias.
- Eliminé todos los datos nulos.
- Creé variables dummies a partir de las categóricas.


El código está disponible [aquí].

### EDA en Python

- Creé diccionarios y otros _Data Frames_ más pequeños a partir de los grandes para poder analizar grupos de variables al nivel individual y escolar.
- Utilice _pandas_ y _numpy_ para sacar estadísticas descriptivas sobre los estudiantes.
- Utilicé _seaborn_ , _matplotlib_ and _plotly_ para hacer gráficos bivariados.

El código está disponible [aquí].

### Análisis multivariado

#### Regresiones

- Creé un modelo de regresión multivariable, con el puntaje global como variable dependiente y variables socioeconómicas del hogar y colegio (principalmente variables dummies) como variables explicativas, para entender la influenica de cada una en el rendimiento de los estudiantes. Todas resultaron ser significativas, pero el R^2 fue bajo.


<img width="400" alt="Captura de Pantalla 2022-11-23 a la(s) 11 12 48 a m" src="https://user-images.githubusercontent.com/103537621/203595066-0fa16ec8-15aa-4189-b17f-7aad3e07cdb2.png">




- El código está disponible [aquí].

#### Análisis de multiples dimensiones

- Colapsé la base de datos grandes en diferentes nivels: escolar, municipal y departamental para desarrollar análisis con distintos enfoques. 
- Fusioné la base de datos de los resultados al nivel del departamento con las otras dos bases de datos que contenían otras variables al nivel departamental. 

El código está disponible [aquí].

### Generación de gráficos en Power BI y Tableau

- Utilicé _Power BI_ para hacer los gráficos de proporciones (stacked bar charts).
- Utilicé _Tableau_ para hacer algunos gráficos de tres dimensiones.


### Generación de mapas en QGIS

- Utilicé QGIS para visualizar la distribución de ciertas variables al nivel departamental. 

---
## Resultados

### Estadísticas Descriptivas

En total, hubo 411491 estudiantes que presentaron el _Saber 11_ examen en el 2021, procedentes de 7513 colegios.

La gran mayoría de los estudiantes no identificarse como étnia minoría; hay más femininos que masculinos; la mayoría tiene un computador y hay aún más estudiantes que cuentan con una conexión de internet en la casa. Más del 60% trabajan. Esto varía entre 1 y 'más de 30 horas' a la semana.

<img width="975" alt="Individuo" src="https://user-images.githubusercontent.com/103537621/203924078-27003cbb-29af-4417-886e-38b95a376938.png">

Hay diversidad entre los colegios de Colombia también. Tres cuartos se ubican en zonas urbanas (en contraste a zonas rurales). Una proporción muy pequeña de los colegios son bilingues o de Calendario B (este siendo, en general, el calendario que los colegios más 'élites' siguen). Casi un tercio de los colegios son privados. La mayoría de los colegios son académicos; los otros se clasifican como técnicos, académico- técnico u 'otro'.

<img width="975" alt="Colegio" src="https://user-images.githubusercontent.com/103537621/203925119-7feaf198-6d72-4959-bad8-f4064ddde8a5.png">

Hay representación de cada municipio en Colombia (1103 en total) y de cada departamento. La Capital, Bogotá D.C., se define como un departamento independiente en estas bases de datos, por lo cual dan un total de 33 departamentos.

### Al nivel Individual

Podemos evidenciar una distribución normal de los resultados:

<img width="400" alt="Captura de Pantalla 2022-11-23 a la(s) 11 05 36 a m" src="https://user-images.githubusercontent.com/103537621/203593495-f5ccabe3-997b-41b5-bc15-becbe7b8f1d6.png">

Sin embargo, al explorar las características individuales de los estudiantes, podemos ver mucha heterogeneity entre ellos y su rendimiento :

![factoresfamiliares](https://user-images.githubusercontent.com/103537621/203930196-b01edd45-52e0-4a05-8106-ef2f4cd18749.png)

Más impactante es la diferencia en rendimiento entre los que se indentifican como étnia minoría y los que no. Pero también, hay una brecha considerable entre los que tienen o no tienen un computador o una conexión de internet en la casa.


Al investigar este tema de conectividad un poco más al profundo, es claro que no contrar con estos representaron un desventaje - las medias son más bajas y la distribución es más positivamente sesgada, indicando que la mayoría de ellos se encuentran por debajo de esta.


<img width="682" alt="fam_comp_int" src="https://user-images.githubusercontent.com/103537621/203931307-0c8fdf5f-3cf4-4d44-8960-1a0f31e591de.png">



### Al Nivel Familiar

Al considerar el estato social de la vivienda de la familia, se nota que el puntaje promedio aumenta ligeramente con el estrato. Sin embargo, también aumentan los rangos intercuartiles, sugiriendo que hay más estudiantes más lejos de la media en los estratos más altos que en los más bajos, donde se concentran más alrededor de la media. Estudiantes de todos estratos pudieron lograr puntajes altos, y de hecho el estudiante con la mayor nota proviene del estrato 1. 

<img width="443" alt="fam_estrato" src="https://user-images.githubusercontent.com/103537621/203604884-2714fa10-d79c-4e8f-8f5d-5317628b4b50.png">

Como respuesta a la pregunta: 'Con respecto al año inmediatamente anterior, la situación económica de su hogar es:' los estudiantes pueden eligir Mejor, Peor o Igual. Podemos ver en el siguiente gráfico que la mayoría optó por igual. Más interesantemente, los que respondieron que 'mejor' tiene una distribución ligeramente positivamente sesgada, indicando que su desempeño fue por debajo de los estudiantes que se encontraron en una peor situación económica.

<img width="443" alt="fam_situacion" src="https://user-images.githubusercontent.com/103537621/203604853-01b0e01c-939f-4ddd-b915-0c57e28f18d2.png">


### Al Nivel Escolar 

La características del colegio también tuvieron una gran influencia sobre los resultados.

![factoresescolares](https://user-images.githubusercontent.com/103537621/203931591-b907528b-2ac7-46bd-a731-dd3570219028.png)

La diferencia entre colegios de Calendario A y de Calendario B siendo la brecha más grande. Profundizando un poco más, al considerar qué porcentaje de cada tipo de colegios se encuentran en los percentiles, vemos que colegios de Calendario A siguen una distribución normal, mientras que para los de Calendario B, la distribución es muy anormal. La mayoría de estos colegios se encuentran en la mitad superior de los percentiles:

![Calendario](https://user-images.githubusercontent.com/103537621/203932545-53c3df56-84c5-4c16-bea3-81693baca85b.png)

La distribución de los percentiles para colegios privados y públicos evidencian el mayor rendimiento de colegios privados, estos tienen un sesgo negativo:

![Estatus](https://user-images.githubusercontent.com/103537621/203932601-6afb2bf2-5a9a-4da0-bbc1-e354cb8ec68c.png)



### Al Nivel del Municipio 

Cuando exploramos el tema de la conectividad, no es extrañar que haya una correlación directa y positiva entre tener un computador y tener una conexión de internet en el hogar. Pero al agregar la dimensión del estatus del colegio, vemos que los municipios con una baja proporción de colegios privados son los que también tienen bajos niveles de conectividad entre los estudiantes:
![Tableau 1](https://user-images.githubusercontent.com/103537621/203933278-821314ab-8ce2-4eb4-8641-2a70090b6103.png)


Si hacemos un zoom en los colegios privados, vemos que municipios con mayores proporciones de colegios privados, en general, se encuentran en los percentiles más altos. Sin embargo, estos son municipios en que un porcentaje muy pequeño de los estudiantes son de una étnia minoría.

![Tableau](https://user-images.githubusercontent.com/103537621/203933295-3f2e990d-2ef4-40f3-9c8a-17a6bd121ce4.png)



### Al Nivel del Departamento 

Mirando la distribución del percentil promedio del departamento, podemos ver que la capital, Bogotá D.C., tiene el mayor percentil promedio. Los departamentos a su alrededor también se encuentran en los percentiles más altos. Los departamentos del sur y de la costa pacífica se encuentran en los percentiles más bajos.

![Percentil Promedio de Puntaje](https://user-images.githubusercontent.com/103537621/204020213-bbabc323-3a1a-47b2-b8b8-99e0c996288e.png)

Si compraramos este mapa con el PIB per cápita, estos departamentos con los menores puntajes son también aquellos con los menores niveles de PIBpc:

<img width="777" alt="PIBpc" src="https://user-images.githubusercontent.com/103537621/204020266-3165917b-62d3-4046-9678-0025e692949e.png">

Y también, tienen tasas de deserción secundaria más altas:
![Deserción Secundaria (1)](https://user-images.githubusercontent.com/103537621/204020304-74599720-7774-43ed-9d1e-1fda7813056f.png)


Lo cual es relacionada con niveles de conectividad (como proporción de estudiantes que cuentan con una conexión de internet en casa):
![Conectividad](https://user-images.githubusercontent.com/103537621/204020334-8d973646-4e45-4d27-be67-3afc1d2aa682.png)



## Conclusiones

El año 2021 presentó una continuación de los desafíos enfrentados por los estudiantes en la coyuntura de la pandemia global. 

Factores socioeconomicos inidividuales, como si el estudiante trabaja, tiene impactos en su capacidad de aprendizaje. Lo más preocupante es la brecha entre los estudiantes que se identifican como una étnia minoria y los que no. 

Existen grandes diferencias en los niveles de conectividad al nivel nacional que están correlacionadas con el rendimiento de estudiantes.

Colegios con mayores recursos, en particular aquellos que son de Calendario B, son públicos o quedan en zonas urbana, tienen un mejor desempeño. 

La deserción escolar está relacionada con el PIB del departamento y niveles generales de conexion de internet.

La educación es una síntoma de la desigualdad en Colombia, pero también una fuente de ella.



