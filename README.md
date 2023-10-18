# Algoritmo de recomendación de películas

### Realizado en el marco del Curso Ingenias DataScience - 2023

## Integrantes: 
Luciana Carvajal ([LucianaCarvajal](https://github.com/LucianaCarvajal)) </br>
Leila Luna Ameneiro ([L-Ameneiro](https://github.com/L-Ameneiro))

## Objetivo

Buscamos desarrollar un algoritmo de recomendación por similitud entre productos audiovisuales, utilizando elementos en común tales como el género, la trama, el elenco y el director o directora.

Para eso contamos con datasets de películas disponibles en las plataformas Amazon Prime, DisneyPlus y Netflix.

## Directorios

En /datasets se encuentran los datasets primarios utilizados así como los generados a partir de la limpieza y procesamiento de datos. 


En /notebooks se encuentran los siguientes archivos:
- **EDA inicial:** Se lleva el análisis exploratorio de datos. Se decide comenzar con un sólo dataset: correspondiente a la plataforma amazon. Se verifican cantidad de columnas y filas, tipo de estructura de datos de dataframe. Se verifica si hay filas duplicadas, tipos de columnas, primeras y ultimas 10 filas del dataset. Se indaga sobre estadísticas de la columna:release_year.</br>
  Se explora y visualizan los datos faltantes. Posteriormente se estudian las peliculas y los TV show (series) de forma separada para generar gráficos de visualización.</br>
  Se realizan cambios en la columna duration para unificar la unidad de medida.</br>
  En el dataset amazon, se observa que hay columnas con datos que están separados por comas, que requerirán un tratameinto especial.</br>
  Se importan los demás dataset, se crea la columna plataforma y concatenan los mismos. </br>
  Finalmente, del análisis exploratorio de los datos inicial, se consluye con que los datasets elegidos serán:  Amazon Prime,  DisneyPlus y Netflix. Se excluirá a Hulu, ya que no es una plataforma de uso en Argentina. Por otra parte, se determina que se tomarán como objeto de estudio en este análisis sólo a las películas, excluyéndose a las series. Se importan los demás conjuntos de datos, se crea la columna plataforma y concatenan los mismos. </br>
  
- **Análisis y procesamiento**: En esta ya está definido el dataframe final, que se formó de la concatenación de los datasets, que contiene solamente películas; denominados: amazon, disney y nexflix. Se realiza el análisis del data set peliculas, renombrando las columnas en idioma español, para facilitar su uso. Se exploran los datos nulos y se visualizan. Posteriormente se procede a la eliminación de las columnas que no serán objeto de estudio de esta análisis. Se explora y visualizan los datos faltantes. Posteriormente se estudian las películas y los programas de televisión (series) de forma separada para generar gráficos de visualización. Se realizan cambios en la columna de duración para unificar la unidad de medida.</br>
  Se procesa la columa director, permitiendo clasificar las películas según si contaron uno o más directores. </br>
  Se proceso la columna listado_en, permitiendo obtener el género principal de cada película para posterior análisis.</br>
  Se cruzan datos con otros datasets de actores que han recibidos premios Oscar y de actores que han recibido premios Golden Globe, con el objetivo de generar features útiles para el modelado.</br>
  Se calculan los puntajes promedio para cada película, asignados por un gran número de usuarios.</br>
 
  
- **Modelado**: Se busca generar un modelo de regresión lineal que prediga el puntaje promedio recibido por una película en base a las siguientes features:
  - si en el elenco hay alguna actriz o actor que haya recibido un Premio Oscar
  - si en el elenco hay alguna actriz o actor que haya recibido un Premio Golden Globe
  - si la película fue dirigida por uno o más directores/as

## Diccionario de dataset inicial: 

Este diccionario corresponde a la etapa EDA-INICIAL. </br>
- show_id: Identificador único de cada serie o película. Posterioremente se denominará "id".</br>
- type: Indica si se trata de una serie ("TV Show") o de una película ("Movie"). Posteriormente se denominará "tipo".</br>
- title: Corresponde al nombre de la serie o película. Posteriormente se denominará "titulo"</br>
- director: Hace referencia a la persona encargada de dirigir la película o serie.</br>
- cast: Enlista a los actores que forman parte de la película, El listado incluye los nombres de los actores separados por comas. Posteriormente se denominará "elenco".</br>
- country: Lugar (país) de producción. Posteriormente se denominará "pais".</br>
- date_added: fecha en que se agregó a la plataforma. Posteriormente se denominará "fecha_agregado".</br>
- release_year: Representa el año de producción. Posterioemente de denominará "anio".</br>
- rating: Clasifica a las producciones de acuerdo a la edad mínima o público recomendado.Cabe aclarar que según los medios o los países, el significado puede varias, por lo que a continuación se detalla cada código. Posteriormente de denominará "calificacion".
                                             </br>7+: No recomendada para menores de 7 años.
                                            </br> 13+: No recomendada para menores de 13 años.
                                            </br> 16+: No recomendada para menores de 16 años.
                                            </br> 18+: No recomendada para menores de 18 años.
                                            </br> ALL: Apropiado para todas las edades.         
                                           </br>  R: Restringido y para mayores de 18 años.     
                                            </br> PG-13: Guía paternal estricta, algunos materiales pueden ser inapropiados para niños menores de 13 años.      
                                            </br> PG: Guía paternal sugerida (con supervisión de los padres), algunos materiales pueden no ser adecuados para niños.
                                            </br> NR:(Sin clasificación). Películas que no fueron clasificadas por el comité (las causas varían, aunque por lo general sucede con producciones que no llegaron a salas comerciales en su momento o que se estrenaron previo a la existencia de los sistemas de clasificación).
                                           </br>  TV-14: Para mayores de 14 años. Se requiere la compañía de padres. 
                                           </br>  TV-PG: Guía paternal extricta.                                              
                                           </br>  TV-NR:(Sin clasificación). Películas que no fueron clasificadas por el comité (las causas varían, aunque por lo general sucede con producciones que no llegaron a salas comerciales en su momento o que se estrenaron previo a la existencia de los sistemas de clasificación).
                                          </br>   G: Todas las edades, aptas para todo público.
                                           </br>  TV-G: Se refiere a programación apta para todas las edades. 
                                          </br>   TV-MA: Para programas dirigidos para adultos, por lo que podrían ser inapropiados para menores de 17 años
                                          </br>   TV-Y: Programación dirigida a un público muy joven, de edades entre dos a seis años.
                                          </br>   TV-Y7: Producciones dirigidas a niños de siete años en adelante. En algunos casos se asigna al final el descriptivo FV (TV-Y7 FV) para aludir a contenido de violencia de fantasía.
                                          </br>   UNRATED: Película no clasificada o es una versión sin editar de una película ya calificada. Las versiones sin cortes o extendidas de películas que tienen esta calificación, también contienen avisos que advierten que esa versión de la película contiene imágenes que difieren del original y podrían no ser aptas para menores.
                                          </br>   NC-17: No se admiten niños menores de 17 años.
                                           </br>  AGES_18_: Para mayores de 18 años.
                                           </br>  NOT_RATE: Película no clasificada o es una versión sin editar de una película ya calificada. Las versiones sin cortes o extendidas de películas que tienen esta calificación, también contienen avisos que advierten que esa versión de la película contiene imágenes que difieren del original y podrían no ser aptas para menores.
                                           </br>  AGES_16_: Para mayores de 16 años. 
                                           </br>  16: Para mayores de 16 años.
                                          </br>   ALL_AGES: Esta clasificación es para programación que es apropiada para todas las edades.   </br>
- duration: Tiempo desde el comienzo y el fin de la película o serie. La unidad de medida del tiempo será en minutos para las películas y temporadas para series. Posteriormente se denominará "duracion".</br>
- listed_in: Géneros y denominación de la clasificación según la plataforma en la que aparece listada la serie o película. Posteriormente se denominará "listado_en".</br>
- description: Breve explicación en idioma ingles de la trama de la serie o película. Posteriormente se denominará "descripción".</br>
- plataforma: Indica a que plataforma pertenece la película.</br>

