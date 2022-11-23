# La Desigualdad en Educación

## Descripción y Motivación

La educación es una de las herramientas más poderosas para disminuir la desigualdad y promover la mobilidad social, con el potencial de romper el cíclo  de pobreza y marginalización intergeneracional. Sin embargo, diferencias en el acceso a la educación y la calidad de esta, plantean un desafío enorme para la igualdad de oportunidad. Por lo tanto, identificar las barreras a la educación y los factores que impactan la calidad de la enseñanza, además de la capacidad de aprendizaje por parte de los estudiantes, es un importante primer paso. 

Yo pretendo hacer esto a través de una análisis de las diferencias socioeconómicos que existen entre los estudiantes a los niveles de la famila y entre colegios, utilizando los resultados (microdatos) del examen _Saber 11_ del año 2021. Es importante tener en cuenta que en este año, la mayoría de las instituciones educativas habían sido cerradas desde el brote de la pandemia del COVID-19 en marzo de 2020 y las clases se desarrollaron si acaso de manera virtual o en lo absoluto.

Este examen se presenta por estudiantes del 11 grado en Colombia y es necesario para poder acceder a la educación superior ('_leaving exam_') y consiste en cinco partes: Matemáticas, Inglés, Lectura Criticia, Ciencias Naturales y Ciencias Sociales. El total de estas da una nota sobre 500, la cual es conocida como el 'Puntaje Global'. Antes de empezar el examen, los estudiantes deben rellenar una encuesta sobre las condiciones socioeconómicas del hogar, y en adición, las características del colegio son guardadas, ofreciendo una riqueza de datos a nivel individual. Junto con datos relacionados a la educación y la economía al nivel departamental, se desarrolla este análisis en estas dimensiones también.

### Preguntas de investigación:

¿Cómo los recursos económicos de la familia afectan el rendimiento escolar?

¿Cómo el estatus del colegio afecta la calidad del aprendizaje?

¿Cómo son las características socioeconómicas del municipio o departamento relacionadas con el desempeño promedio de estudiantes?


El Puntaje Global será la variable principal de interés, como es el desempeño general de los estudiantes al graduarse de bachiller, y se considera un 'proxy' para evaluar la calidad de la ensenañza de los colegios.

---
## Méotodos Utilizados

### Descarga de las bases de datos

"**Resultados Individuals de Saber 11**" -  Las bases de datos principales están disponibles en la página de ICFES: https://www2.icfes.gov.co/web/guest/resultados-individuales-saber-11. (Hay que crear una cuenta para poder accederlas). 

Como hay dos opciones de fecha para presentar el examan, dependiendo del calendario del colegio, hay dos archivos de texto por cada año. Los descargué para el año 2021.

También accedé a la base de datos del Ministerio de Educación, _Estadísticas en Educación_ ,a través del protocolo Socrata Open Data API (SODA). Disponible en el sitio de Datos Abiertos: https://www.datos.gov.co/Educaci-n/MEN_ESTADISTICAS_EN_EDUCACION_EN_PREESCOLAR-B-SICA/nudc-7mev.

Por útlimo, descargué la base de datos de Cuentas Nacionales del DANE, para  https://www.dane.gov.co/index.php/estadisticas-por-tema/cuentas-nacionales/cuentas-nacionales-departamentales, que ya estaba disponible en formato csv. 

### Depuración de los datos

Utilicé _pandas_ en _Python_ para crear y manejar las bases de datos: 
- Convertí los archivos .txt a _Data Frames_ y los uní para crear una base grande. El código está disponible [aquí].
- Eliminé las columnas innecesarias.
- Eliminé todos los datos nulos.
- Creé variables dummies a partir de las categóricas.


El código está disponible [aquí].

### EDA en Python

- Creé diccionarios y otros _Data Frames_ más pequeños a partir de los grandes para poder analizar grupos de variables al nivel individual. 
- Utilice _pandas_ y _numpy_ para sacar estadísticas descriptivas sobre los estudiantes.
- Utilicé _seaborn_ , _matplotlib_ and _plotly_ para hacer gráficos bivariados.

El código está disponible [aquí].

### Análisis multivariada

#### Regresiones

- Creé un modelo de regresión multivariable, con el puntaje global como variable dependiente y variables socioeconómicas del hogar y colegio (principalmente variables dummies) como variables explicativas, para entender la influenica de cada una en el rendimiento de los estudiantes. Todas resultaron ser significativas, pero el R^2 fue bajo.


<img width="724" alt="Captura de Pantalla 2022-11-23 a la(s) 11 12 48 a m" src="https://user-images.githubusercontent.com/103537621/203595066-0fa16ec8-15aa-4189-b17f-7aad3e07cdb2.png">




- El código está disponible [aquí].

#### Análisis de multicapas

- Colapsé la base de datos grandes en diferentes nivels: escolar, de municipio y de departamento para desarrollar análisis a distintas dimensiones. 
- Fusioné la base de datos de los resultados al nivel del departamento con las otras dos bases de datos que contienen otras variables al nivel departamental. 

El código está disponible [aquí].

### Generación de gráficos en Power BI

- Utilicé _Power BI_ para hacer algunos gráficos de tres o cuatro dimensiones.

### Generación de mapas en QGIS

- Utilicé QGIS para visualizar las relaciones entre variables al nivel del departamento. 

---
## Resultados

### Resultados Preliminares 


<img width="477" alt="Captura de Pantalla 2022-11-23 a la(s) 11 05 36 a m" src="https://user-images.githubusercontent.com/103537621/203593495-f5ccabe3-997b-41b5-bc15-becbe7b8f1d6.png">





### Al Nivel Familiar


<img width="443" alt="fam_situacion" src="https://user-images.githubusercontent.com/103537621/203604853-01b0e01c-939f-4ddd-b915-0c57e28f18d2.png">


<img width="443" alt="fam_estrato" src="https://user-images.githubusercontent.com/103537621/203604884-2714fa10-d79c-4e8f-8f5d-5317628b4b50.png">

<img width="682" alt="fam_comp_int" src="https://user-images.githubusercontent.com/103537621/203604906-789e5189-b199-43ca-9629-36b993cd114c.png">

<img width="622" alt="fam" src="https://user-images.githubusercontent.com/103537621/203604927-780bb352-74ad-4f8f-bec9-94f54aef2a93.png">





### Al Nivel Escolar 


<img width="622" alt="colegio" src="https://user-images.githubusercontent.com/103537621/203604960-0c816d6b-3f6b-450b-a20d-2adac8308967.png">


![newplot (2)](https://user-images.githubusercontent.com/103537621/203619721-59f0ec03-f3ec-4af1-ba8f-e07f3fb4ade6.png)



![newplot (3)](https://user-images.githubusercontent.com/103537621/203619981-1b2c6567-f987-4b52-97f0-e87afbce4821.png)




### Al Nivel del Municipio 




### Al Nivel del Departamento 




