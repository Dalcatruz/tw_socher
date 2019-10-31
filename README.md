# tw_socher


## Análisis de redes sociales: Extracción de datos de Twitter con R



Instructores: - Daniel Alcatruz,  Administrador Público UDEC.
              - Gonzalo Barría, Magíster en Ciencia Política UC

El objetivo de este workshop es introducir los conceptos y funciones básicas en el lenguaje de programación R para la extracción y posterior análisis de datos obtenidos de la red social Twitter. Para esto se utilizará la interfaz de usuario llamda RStudio. Procuramos brindar también las habilidades básicas para realizar tareas estadpisticas en el uso del software de R.


## Contenido del Workshop - Análisis de Twitter:


Unidad 1: Conceptos fundamentales
 -Obtener datos de twitter.
 -Librerías más utilizadas 
 -¿Que podemos buscar?
 -Usuarios, keywords, límites.
 
Unidad 2: Análisis de texto en Twitter

 -El texto de un tweet.
 -Cleaning data
 -Análisis cuantitativo
 
Unidad 3: Funcionalidades
-Difusión de fenómenos politicos y sociales y como obtener información de ellos
-Tweets y Retweets
-Favoritos
-Algoritmos para detectar comunidades
-Cámaras de eco

Unidad 4: Aplicación en un caso práctico


## Referencias sugeridas

-Calvo, E. (2015). Anatomía política de Twitter en Argentina. Tuiteando #Nisman. Buenos Aires: Capital Intelectual.
-Calvo, E., Dunford, E., & Lund, N. (2016). Hashtags that Matter: Measuring the propagation of Tweets in the Dilma Crisis. Working Paper.
-Calvo, E., & Aruguete, N. (2018). #Tarifazo. Medios tradicionales y fusión de agenda en redes sociales. En Inmediaciones de la Comunicación, 13(1), 189–213.
-Jelani Ince, Fabio Rojas & Clayton A. Davis (2017). The social media response to Black Lives Matter: how Twitter users interact with Black Lives Matter through hashtag use.* Ethnic and Racial Studies, 40*:11, 1814-1830.
- JohnHarrison (2016). RSelenium: R Bindings for Selenium WebDriver. R package version 1.4.0. https://cran.rstudio.com/package=RSelenium 
-Kearney MW (2019). rtweet: Collecting Twitter Data. R package version 0.6.9, https://cran.r-project.org/package=rtweet. 
- Steinert-Threlkeld, Z. (2018). Twitter as Data (Elements in Quantitative and Computational Methods for the Social Sciences). Cambridge: Cambridge University Press. doi:10.1017/9781108529327
-Wickham, H. (2019). ggplot2: Elegant Graphics for Data Analysis. https://ggplot2-book.org





## Unidad 1: Conceptos Fundamentales

Twitter es una red social fundada en 2006 que permite a los usuarios interactuar entre sí enviando mensajes de no más de 280 caracteres. Es ampliamente usada por servicios públicos y por políticos especialmente en las épocas de campaña electoral. Con las nuevas técnicas de análisis de datos el estudio de la interacción de los usuarios en twitter se ha vuelto muy importante por ejemplo para medir los temas sobre los que está hablando la gente (*trending topics*) y sobre si las opiniones sobre una persona o tema son positivas o negativas. Por ejemplo Ernesto Calvo en su libro *Anatomía Política de Twitter en Argentina: Tuiteando #NISMAN* pudo detectar claramente a través de esta red social comunidades que correspondían tanto como a opositores al gobierno como gente con simpatías oficialistas así como la polarización política que se produjo producto de la muerte del ex fiscal Alberto Nisman. *"Las diferencias de clase y de consumos entre los votantes peronistas y no peronistas se ven en los celulares: Android tiene mayor presencia entre los oficialistas, iPhone entre los opositores. A partir del caso Nisman, Ernesto Calvo analiza los tuits de los usuarios argentinos y muestra que la polarización mezcla política, algoritmos y smartphones"*

Los paquetes de R utilizados en está parte para ordenar y dar estética a los datos ya son conocidos.Para hacer la extracción de datos de Twitter la mejor opción que consiste en el paquete que tiene un soporte continuo es `Rtweet` permite ingresar de manera gratuita al API de Twitter para descargar información por usuarios, fechas y hashtags. Para extraer datos de Twitter con R se recomienda consultar *Twitter as Data*, que contiene algunas rutinas estandarizadas para descargar datos de esta plataforma.


## Algunos antecedentes

La interfaz de programación de aplicaciones *Application Program Interfaces* (APIs en inglés) son un set de protocolos y funciones que gobiernan ciertas interacciones entre aplicaciones web y usuarios.

las APIs son similares a los navegadores web pero cumplen diferentes propósitos:

    Navegadores web reproducen contenido browsers 
    Las APIs permiten manipular y organizador datos

Para que las APIs públicas sean utilizadas muchos sitios solo permiten a usuarios autorizados (por ejemplo aquellos que tienen una cuenta en la plataforma)

    Twitter, Facebook, Instagram, Github, etc.
    

Si bien estas APIs son ampliamente conocidas no está demás mencionar algunas creadas por la misma comunidad de R especializada en datos políticos. Por ejemplo el paquete `lobbyR` creado por Daniel Alcatruz (https://github.com/Dalcatruz/lobbyR) que permite cargar y estructurar datos desde la API lobby que se encuentra en la plataforma de Ley de Lobby (https://www.leylobby.gob.cl/) implementada para el Gobierno de Chile, que permite realizar consultas por ejemplo sobre audiencias en determinados servicios públicos y organismos del estado como el congreso y los municipios. Otro paquete que es necesario mencionar es `inegiR` creado por Eduardo Flores que permite interactuar con la API del INEGI (Instituto Nacional de Estadística y Geografía de México) para realizarse consultas específicas. http://enelmargen.org/ds/inegiR/vignette_spa.html



# Extraer los datos

Lo primero para partir utilizando la API oficial de Twitter es tener una cuenta de twitter que podemos crearla en (https://twitter.com/i/flow/signup. 
Luego procedemos a cargar el paquete `rtweet` que nos permitirá extraer datos de Twitter. Ahora vamos a extraer los datos de distintos usuarios y hashtags. Para asegurarnos que todo está bien vamos a postear un tweet desde R con la siguiente función
