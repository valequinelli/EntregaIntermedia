# Cómo tener mayor alcance en Youtube

## Introducción y Resumen

Partiendo de los datos de varios canales de Youtube, se realiza un análisis que busca responder preguntas como: ¿Cuáles son los canales con mayor cantidad de seguidores?, ¿Cuál es su temática?, ¿De qué país es la mayor parte de la audiencia?, ¿Cuál es la relación entre la cantidad de suscriptores y de me gusta o comentarios? 
Con esto se busca entender el comportamiento de los usuarios para poder tener mayor alcance. 

## Contexto

YouTube es un sitio web de origen estadounidense dedicado a compartir videos como películas, vídeos musicales y videoblogs, entre otros. 
Actualmente se emplea el término Youtuber para referir un productor y gestor de contenido audiovisual que usa YouTube como su plataforma de comunicación. Algunos youtubers son parte las estrategias de marketing que utilizan actualmente las empresas, quienes les pagan por colocar anuncios en sus videos o promocionar sus productos. 

## Datos

Los datos para el análisis se obtienen de la página del curso.

A continuación se presenta un resumen de los mismos: 

|             | Youtuber Name       | Channel Name     | Category                                                    | Subscribers              | Audience Country                         | Average Views                        | Average Likes                   | Average Comments                 |
|-------------|---------------------|------------------|-------------------------------------------------------------|--------------------------|------------------------------------------|--------------------------------------|---------------------------------|----------------------------------|
| Description | Nombre del Youtuber | Nombre del canal | Categoria a la que corresponde el contenido subido al canal | Cantidad de suscriptores | Pais principal de la audiencia del canal | Cantidad promedio de visualizaciones | Cantidad promedio de 'Me gusta' | Cantidad promedio de comentarios |
| Type        |                 str |              str |                                                         str |                      int |                                      str |                                  int |                             int |                              int |
| Count       |                1000 |             1000 |                                                        1000 |                     1000 |                                     1000 |                                 1000 |                            1000 |                             1000 |
| Unique      |                 998 |              998 |                                                          24 |                No Aplica |                                       28 |                            No Aplica |                       No Aplica |                        No Aplica |
| Min         |           No Aplica |        No Aplica |                                                   No Aplica |                  9200000 |                                No Aplica |                                    0 |                               5 |                                1 |
| Max         |           No Aplica |        No Aplica |                                                   No Aplica |                212100000 |                                No Aplica |                             80500000 |                         5600000 |                           313600 |


## Metodología

Previo al análisis se realiza una limpieza inicial de datos:
<ul>
<li>Se renombran las columnas para cumplir con el estilo snake_case.</li>
<li>Se reemplaza NaN por "No Data" en todas las columnas.</li>
<li>Para las columnas con datos numéricos, se acomoda el formato para que sea un número (Ej: 1M se convierte en 1000000)</li>
<li>Luego para las columnas de likes promedio y comentarios promedio, se decide cambiar "No data" por el valor promedio del resto de los datos de esa columna. Se entiende suficientemente representativo.</li>
<li>Ambas columnas se formatean a int.</li>
</ul>

Como primer paso se busca identificar los 5 canales con mayor número de visualizaciones, suscriptores, me gusta y comentarios.

Luego se crea un nuevo dataframe llamado "Ratios" que busca calcular el ratio entre la cantidad de visualizaciones, suscriptores, me gusta y comentarios. Esto con el fin de determinar si existe una correlación directa entre ellos.

Finalmente se analiza la distribución por país y por categoría del contenido del canal, con el objetivo de identificar aquellos países con mayor audiencia y aquellas categorías de mayor interés para los usuarios.


## Resultados

### Top 5
A continuación se presentan los Top 5.

Por número de suscriptores:

|    | youtuber_name   | channel_name               | category      |   subscribers | audience_country   |   average_views |   average_likes |   average_comments |\n|---|----------------|---------------------------|--------------|--------------|-------------------|----------------|----------------|-------------------|\n|  0 | tseries         | T-Series                   | Music & Dance |     212100000 | India              |          323700 |      9800       |                290 |\n|  1 | checkgate       | Cocomelon - Nursery Rhymes | Education     |     132100000 | No Data            |        13800000 |     80900       |               3349 |\n|  2 | setindia        | SET India                  | No Data       |     130400000 | India              |           23600 |       314       |                 21 |\n|  3 | PewDiePie       | PewDiePie                  | Animation     |     111400000 | United States      |         1400000 |     80800       |               4600 |\n|  4 | MrBeast6000     | MrBeast                    | Video games   |      92500000 | United States      |        30600000 |         1.7e+06 |              67700 |

Por número de visualizaciones:

|     | youtuber_name   | channel_name   | category        |   subscribers | audience_country   |   average_views |   average_likes |   average_comments |\n|----:|:----------------|:---------------|:----------------|--------------:|:-------------------|----------------:|----------------:|-------------------:|\n| 503 | Bizarrap        | Bizarrap       | Music & Dance   |      13100000 | Argentina          |        80500000 |         5.6e+06 |             313600 |\n|   4 | MrBeast6000     | MrBeast        | Video games     |      92500000 | United States      |        30600000 |         1.7e+06 |              67700 |\n| 862 | whoisjimmy      | How Ridiculous | Sports          |       9900000 | United States      |        25500000 |    750300       |               5200 |\n| 118 | MrBeast Gaming  | MrBeast Gaming | Animation       |      26500000 | United States      |        23300000 |    732000       |              44000 |\n| 844 | вДудь           | вДудь          | News & Politics |      10100000 | Russia             |        16800000 |    615500       |              89400 |

Por cantidad de me gusta:

|     | youtuber_name    | channel_name     | category      |   subscribers | audience_country   |   average_views |   average_likes |   average_comments |\n|----:|:-----------------|:-----------------|:--------------|--------------:|:-------------------|----------------:|----------------:|-------------------:|\n| 503 | Bizarrap         | Bizarrap         | Music & Dance |      13100000 | Argentina          |        80500000 |         5.6e+06 |             313600 |\n|   4 | MrBeast6000      | MrBeast          | Video games   |      92500000 | United States      |        30600000 |         1.7e+06 |              67700 |\n| 423 | Harsh Beniwal    | Harsh Beniwal    | Movies        |      14300000 | India              |        11600000 |         1.3e+06 |              55400 |\n| 363 | Triggered Insaan | Triggered Insaan | Humor         |      15400000 | India              |         6400000 |    800900       |              26500 |\n| 628 | MORGENSHTERN     | MORGENSHTERN     | Humor         |      11700000 | Russia             |        11000000 |    789900       |              54800 |

Por cantidad de comentarios:

|     | youtuber_name        | channel_name         | category        |   subscribers | audience_country   |   average_views |   average_likes |   average_comments |\n|----:|:---------------------|:---------------------|:----------------|--------------:|:-------------------|----------------:|----------------:|-------------------:|\n| 503 | Bizarrap             | Bizarrap             | Music & Dance   |      13100000 | Argentina          |        80500000 |         5.6e+06 |             313600 |\n|  76 | Desi Music Factory   | Desi Music Factory   | Music & Dance   |      32100000 | India              |        10800000 |    396400       |             143600 |\n| 924 | Bispo Bruno Leonardo | Bispo Bruno Leonardo | Music & Dance   |       9600000 | Brazil             |          577900 |    208700       |             139800 |\n| 703 | Jaiden Animations    | Jaiden Animations    | No Data         |      11100000 | United States      |         5600000 |    602700       |              94300 |\n| 844 | вДудь                | вДудь                | News & Politics |      10100000 | Russia             |        16800000 |    615500       |              89400 |




## Conclusiones

Como se puede observar,
