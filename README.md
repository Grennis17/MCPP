# La Desigualdad en Educación

## Descripción y Motivación

La educación es una de las herramientas más poderosas para disminuir la desigualdad y promover la mobilidad social, con el potencial de romper el cíclo  de pobreza y marginalización intergeneracional. Sin embargo, el acceso a la educación y la calidad de esta, plantea un desafío enorme para la igualdad de oportunidad. Por lo tanto, identificar las barreras a la educación y los factores que impactan la calidad de la enseñanza, además de la capacidad de aprendizaje por parte de los estudiantes, es un importante primer paso. 

Yo pretendo hacer esto a través de una análisis de las diferencias socioeconómicos que existen entre los estudiantes a los niveles de la famila y entre colegios, utilizando los resultados (microdatos) del examen _Saber 11_ del año 2021. Este examen se presenta por estudiantes del 11 grado en Colombia y es necesario para poder acceder a la educación superior ('_leaving exam_') y consiste en cinco partes: Matemáticas, Inglés, Lectura Criticia, Ciencias Naturales y Ciencias Sociales. El total de estas da una nota sobre 500, la cual es conocida como el 'Puntaje Global'. Antes de empezar el examen, los estudiantes deben rellenar una encuesta sobre las condiciones socioeconómicas del hogar, y en adición, las características del colegio son guardadas, ofreciendo una riqueza de datos a nivel individual. Junto con datos relacionados a la educación y la economía al nivel departamental, se desarrolla este análisis en estas dimensiones también.

### Preguntas de investigación:

¿Cómo los recursos económicos de la familia afectan el rendimiento escolar?

¿Cómo el estatus del colegio afecta la calidad del aprendizaje?

¿Cómo son las características socioeconómicas del municipio o departamento relacionadas con el desempeño promedio de estudiantes?


El Puntaje Global será la variable principal de interés, como es el desempeño general de los estudiantes al graduarse de bachiller, y se considera un 'proxy' para evaluar la calidad de la ensenañza de los colegios.

---
## Méotodos Utilizados

### Descargar las bases de datos

Las bases de datos principales están disponibles en la página de ICFES: https://www2.icfes.gov.co/web/guest/resultados-individuales-saber-11. (Hay que crear una cuenta para poder accederlas). Los resultados son al nivel del individuo.

Como estudiantes tienen dos fechas para presentar el examan, dependiendo en general en el calendario del colegio, hay dos archivos de texto por cada año. Los descargué para el año 2021, los convertí en formato de DataFrame utilizando Pandas en Python, y los uní para crear solo una base de datos. El código está disponible [aquí].

También accedé a la base de datos del Ministerio de Educación, _Estadísticas en Educación_ ,a través del protocolo Socrata Open Data API (SODA). Disponible en el sitio de Datos Abiertos: https://www.datos.gov.co/Educaci-n/MEN_ESTADISTICAS_EN_EDUCACION_EN_PREESCOLAR-B-SICA/nudc-7mev.

Por útlimo, descargué la base de datos de Cuentas Nacionales del DANE, para  https://www.dane.gov.co/index.php/estadisticas-por-tema/cuentas-nacionales/cuentas-nacionales-departamentales, que ya estaba disponible en formato csv. 

### Depuración de los datos

Utilicé _pandas_ en _Python_ para crear y manejar las bases de datos:
- Eliminé las columnas innecesarias.
- Eliminé todos los datos nulos.
- Creé variables dummies a partir de las categóricas.

El código está disponible [aquí].

- Creé diccionarios y otros _Data Frames_ más pequeños a partir de los grandes para poder analizar grupos de variables al nivel individual. 
- Colapsé la base de datos grandes en diferentes nivels: escolar, de municipio y de departamento para desarrollar análisis a distintas dimensiones. 
- Fusioné la base de datos de los resultados al nivel del departamento con las otras dos bases de datos que contienen otras variables al nivel departamental. 

### EDA en Python

- Utilice _pandas_ y _numpy_ para sacar estadísticas descriptivas sobre los estudiantes.
- Utilicé _seaborn_ and _matplotlib_ para hacer los gráficos iniciales.

El código está disponible [aquí].


### Generación de gráficos en Power BI

- Utilicé _Power BI_ para hacer unos gráficos de tres dimensiones.

### Generación de mapas en QGIS

- Utilicé QGIS para visualizar las relaciones entre variables al nivel del departamento. 

---
## Resultados


### A Nivel Familiar

![factoresfamiliares](https://user-images.githubusercontent.com/103537621/203404522-fa5bdc92-28f7-4b90-8667-8bd6751de54c.png)


### A Nivel Escolar 





### A Nivel del Municipio 




### A Nivel del Departamento 




