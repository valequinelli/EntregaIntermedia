
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

#### Por número de suscriptores

|   | youtuber_name |               channel_name |      category | subscribers | audience_country | average_views | average_likes | average_comments |
|---|--------------:|---------------------------:|--------------:|------------:|-----------------:|--------------:|--------------:|-----------------:|
| 0 | tseries       | T-Series                   | Music & Dance | 212100000   | India            | 323700        | 9800          | 290              |
| 1 | checkgate     | Cocomelon - Nursery Rhymes | Education     | 132100000   | No Data          | 13800000      | 80900         | 3349             |
| 2 | setindia      | SET India                  | No Data       | 130400000   | India            | 23600         | 314           | 21               |
| 3 | PewDiePie     | PewDiePie                  | Animation     | 111400000   | United States    | 1400000       | 80800         | 4600             |
| 4 | MrBeast6000   | MrBeast                    | Video games   | 92500000    | United States    | 30600000      | 1700000       | 67700            |

#### Por número de visualizaciones

|     |  youtuber_name |   channel_name |        category | subscribers | audience_country | average_views | average_likes | average_comments |
|-----|---------------:|---------------:|----------------:|------------:|-----------------:|--------------:|--------------:|-----------------:|
| 503 | Bizarrap       | Bizarrap       | Music & Dance   | 13100000    | Argentina        | 80500000      | 5600000       | 313600           |
| 4   | MrBeast6000    | MrBeast        | Video games     | 92500000    | United States    | 30600000      | 1700000       | 67700            |
| 862 | whoisjimmy     | How Ridiculous | Sports          | 9900000     | United States    | 25500000      | 750300        | 5200             |
| 118 | MrBeast Gaming | MrBeast Gaming | Animation       | 26500000    | United States    | 23300000      | 732000        | 44000            |
| 844 | вДудь          | вДудь          | News & Politics | 10100000    | Russia           | 16800000      | 615500        | 89400            |

#### Por cantidad de me gusta

|     |    youtuber_name |     channel_name |      category | subscribers | audience_country | average_views | average_likes | average_comments |
|-----|-----------------:|-----------------:|--------------:|------------:|-----------------:|--------------:|--------------:|-----------------:|
| 503 | Bizarrap         | Bizarrap         | Music & Dance | 13100000    | Argentina        | 80500000      | 5600000       | 313600           |
| 4   | MrBeast6000      | MrBeast          | Video games   | 92500000    | United States    | 30600000      | 1700000       | 67700            |
| 423 | Harsh Beniwal    | Harsh Beniwal    | Movies        | 14300000    | India            | 11600000      | 1300000       | 55400            |
| 363 | Triggered Insaan | Triggered Insaan | Humor         | 15400000    | India            | 6400000       | 800900        | 26500            |
| 628 | MORGENSHTERN     | MORGENSHTERN     | Humor         | 11700000    | Russia           | 11000000      | 789900        | 54800            |

#### Por cantidad de comentarios

| | youtuber_name | channel_name         | category             | subscribers     | audience_country | average_views | average_likes | average_comments |        
|---------------|----------------------|----------------------|-----------------|------------------|---------------|---------------|------------------|--------|
| 503           | Bizarrap             | Bizarrap             | Music & Dance   | 13100000         | Argentina     | 80500000      | 5600000          | 313600 |
| 76            | Desi Music Factory   | Desi Music Factory   | Music & Dance   | 32100000         | India         | 10800000      | 396400           | 143600 |
| 924           | Bispo Bruno Leonardo | Bispo Bruno Leonardo | Music & Dance   | 9600000          | Brazil        | 577900        | 208700           | 139800 |
| 703           | Jaiden Animations    | Jaiden Animations    | No Data         | 11100000         | United States | 5600000       | 602700           | 94300  |
| 844           | вДудь                | вДудь                | News & Politics | 10100000         | Russia        | 16800000      | 615500           | 89400  |

### Gráficos por país y por categoría

#### Por país 

A continuación se presenta un gráfico con la cantidad de canales por país de la audiencia:

<img width="384" alt="Captura de Pantalla 2022-04-11 a la(s) 00 08 31" src="https://user-images.githubusercontent.com/95255479/162659204-d4ff6ab6-2c64-437c-af5e-5b4f725cd691.png">

Total de entradas con datos de país de la audiencia: 839

#### Por categoría

El siguiente gráfico muestra la cantidad de canales según la categoría de su contenido:

<img width="384" alt="Captura de Pantalla 2022-04-11 a la(s) 00 08 22" src="https://user-images.githubusercontent.com/95255479/162659159-211d8819-f412-4cc9-9e09-59398ad38b9a.png">

Total de entradas con datos de categoría: 723

El siguiente gráfico muestra la cantidad de views promedio según la categoría de su contenido:

<img width="290" alt="Captura de Pantalla 2022-04-11 a la(s) 15 55 42" src="https://user-images.githubusercontent.com/95255479/162810135-1a0966f8-247a-40d0-aefb-37fd52f4310d.png">

Al analizar el gráfico se puede concluir que "Health & Self Help", "Sports" y "Travel" son las categorías que más visualizaciones tienen en promedio.

### Gráficos de ratios

<img width="705" alt="Captura de Pantalla 2022-04-11 a la(s) 15 11 45" src="https://user-images.githubusercontent.com/95255479/162802959-1bbd2793-0de2-4038-8eb8-900ba4e959c7.png">

A partir del análisis de estos gráficos, se pueden sacar varias conclusiones. En primer lugar, al analizar la primera gráfica nos encontramos que la gran mayoría de los canales no superan el ratio de valor 1, esto significa que estos canales no tienen más suscriptores que views. Esto llama la atención, dado que la creencia popular es que los canales tienen más views que suscriptores, es decir, mucha gente mira los videos pero pocos se apegan al canal y se convierten en un seguidor de ese creador de contenido. Por otro lado, podemos observar que algunos canales tienen ratios mayores a 1, alcanzando valores mayores a 6. Entendemos que esto puede darse en casos en los que un canal muy poco popular sube un video determinado que tiene una viralización exagerada, consiguiendo muchas views, pero si el canal no es activo o no es consistente con ese tipo de contenido, no va a tener un despegue en suscriptores. 

En la siguiente gráfica, que presenta el ratio_subscribers_likes, sucede una situación similar a la anterior, se puede ver algunos canales con ratios despegados al resto, y la explicación que se le encuentra a esto es la misma que para el caso anterior, videos con una viralización inesperada. Pasando a analizar estas dos gráficas en conjunto, se puede apreciar que el ratio de la relación entre los suscriptores y las views se encuentra en su mayoría entre 0 y 1, mientras que el ratio de suscriptores y likes raramente supera 0,1. Esto se explica a partir de que para un creador de contenido es mucho más difícil obtener likes que views, dado que si un usuario mira un video ya contabiliza como view, pero para obtener un like se requiere un esfuerzo extra del usuario que consume el contenido. Además, sólo se puede likear una vez, pero mirar el video muchas veces y cada una de estas se traduce en una view.

Pasando a la siguiente gráfica, se analiza la variación del ratio_views_likes respecto a cada canal de YouTube. Como era de esperarse, la gran mayoría de los valores son muy cercanos a 0, ya que como se explicó anteriormente, es mucho más fácil para un canal de YouTube obtener views que likes. Sin embargo, se aprecian determinados canales con este ratio adoptando valores mayores a 1. Basándose en la lógica del funcionamiento de YouTube, esto es imposible, ya que para que un usuario likee un video, primero tiene que sí o sí entrar al video, y esto ya contabiliza como view. En base a esto, se concluye que estos valores deben tratarse de un error.

Para finalizar, se analiza la última gráfica de esta sección, la cual presenta el ratio_likes_comments. Aquí nuevamente se observa que la mayoría de los valores se acercan a 0. No obstante, se aprecian múltiples canales con valores mayores a 50 o 100, superando 400 en algunos casos. Esto sorprende, dado que normalmente un video tiene más likes que comentarios, principalmente por el esfuerzo que le implica al usuario realizar cada una de estas acciones. Se pudo observar que 889 canales tienen en promedio un ratio menor a 1, lo que parece lógico. Mientras que los restantes 111 canales, muestran tener en promedio más comentarios que likes. Esta situación podría justificarse a partir de que pueden ser canales cuyo contenido no guste mucho a los espectadores, y que consecuentemente no dejen likes en los videos pero sí publiquen comentarios criticando o simplemente expresando sus opiniones.

#### Porcentaje de likes sobre views 

En esta instancia se calcula qué porcentaje de las views a un canal son retribuidas con un like. Este porcentaje es de 3.1072%
Se puede interpretar que son muy pocos los viewers que le dan like a un video. De todas formas esta estadística puede verse perjudicada por el hecho de que un usuario puede dar like a un video una única vez, mientras que puede visualizarlo cuantas veces quiera.


<img width="705" alt="Captura de Pantalla 2022-04-11 a la(s) 15 20 59" src="https://user-images.githubusercontent.com/95255479/162804358-baaa0c99-2fa7-438e-bf5c-d37f66e4a3c8.png">

Aquí se presenta un gráfico para cada ratio calculado anteriormente, clasificados según la categoría del contenido. A partir de este análisis se puede concluir cuáles son las categorías que presentan más views o likes en relación a los suscriptores, likes en relación a los views y también comments en relación a los likes. Los resultados de estas visualizaciones se pueden traducir en que aquellos canales cuya categoría es "travel" presentan los mejores ratios relativos a los suscriptores, es decir que este tipo de contenido es al que la gente más ve y likea en relación a los suscriptores que tiene el canal. Esto puede deberse a que este tipo de contenido suele ser consumido cuando la gente planea un viaje, por lo que se suele obtener información de muchas fuentes distintas y no es común que se suscriba a todos los canales cuyo contenido utiliza.
Por otro lado, en el gráfico que representa el ratio_views_likes, se puede ver que la categoría destacada es "Autos & Vehicles". Esto quiere decir que mucha gente que ve ese tipo de videos, acaba retibuyéndolos con un like.
Finalmente, respecto al gráfico del ratio_likes_comments, se presenta la categoría "Design/art" sobreponiéndose sobre el resto. Este suceso podría explicarse a partir de que es un contenido relativamente crítico, sobre el que la gente le gusta opinar y comentar sus ideas.


## Conclusiones

De las gráficas de ratios se desprende que la relación entre la cantidad de suscriptores, visualizaciones, me gusta y comentarios es bastante similar en todos los casos. Se observa un comportamiento bastante parejo en lo general, con casos puntuales en los que la relación no es directa.
Sin embargo, es curioso

En cuanto a los países de la audiencia, se observa que Estados Unidos es el de mayor audiencia. Esto puede dar la pauta de que sería bueno enfocar los esfuerzos en apuntar a ese público, lo que podría traer mayores visualizaciones. 

Si se analizan las categorías del contenido de cada canal, se concluye que la de mayor popularidad es "Music & Dance". Se observa que en todos los Top 5 el canal que ocupa el primer puesto corresponde a esta categoría. No obstante, las categorías con mayor cantidad de visualizaciones promedio son "Health & Self Help", "Sports" y "Travel". Esto podría explicarse a partir de que estas categorías suelen gustar a más gente, dado que son temas bastante populares. Con el objetivo de responder a la pregunta inicial (cómo lograr un mayor alcance en YouTube), se le podría recomendar a los creadores de contenido que opten por inclinarse hacia estas categorías, ya que, como se ha demostrado, son las que llegan a más gente.
