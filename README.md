# Actividad 4 : Pruebas de particionamiento de bases de datos NoSQL
## Casos de Prueba de Replicación de Bases de Datos NoSQL
|Requisitos|Prueba|Resultado Esperado|
|--|--|--|
|Escalamiento horizontal de datos.|Escalamiento horizontal de datos.|Muestra la distribución de documentos en los shards implementados.|
|Fragmentación de bases de datos.|Consulta sobre distribución con el comando getShardDsitribution()|Indica el espacio en memoria asignado a cada shard y el peso que contienen.|
|La escritura se deben realizar desde un solo servidor.|Se intenta escribir sobre un nodo no primario al azar, luego se comprueba desde el primario.|No es posible escribir desde un nodo secundarios, solo el nodo primario tiene permiso de escritura.|
|El grupo de partición debe estar compuesto por servidores de configuración, enrutadores de consultas y shards.|Se verifica que los puertos asignados a los servidores de confirguración, enrutador y shards, se encuentren activos usando el comanto netstat -a|Se verifica que los puertos asignados a los servidores de confirguración, enrutador y shards, se encuentren activos usando el comanto netstat -a|
|El sistema debe emplear particionamiento basado en hash.|Con getShardDsitribution() se revisan los pesos de los chunks, se adicionan 3 documentos de forma sucesiva y se verifica posteriormente los pesos de los chunks.|En la segunda prueba debe aumentar los pesos de los chunk uniformemente.|

## Nota
La evidencia de la ejecución del código esta registrada en el documento pdf llamado "Actividad 6 - Pruebas de Particionamiento de Bases de Datos NoSQL - Holman Cruz.pdf"
Siguiendo el paso a paso del capítulo VIII Sharding, del libro introducción a las bases de datos nosql usando mongodb, logré llegar solo hasta el script que inicia el enrutador, probé con varios ajustes sobre la sintaxis, sin embargo, obtuve la misma respuesta “las conexiones del servidor de configuración reflejado no son compatibles”.

## Conclusiones
- El particionamiento en bases de datos no relacionales permite que las consultas puedan ser gestionadas por rango o por hash.
- La capacidad de los shards puede ser asignada editando los espacios dedicados a cada chunk.
- Al particionar bases de datos se reducen costos en recursos de máquinas, puesto que su escalamiento es horizontal e ilimitado.
- El almacenamiento de datos en particionamiento basado en rango es mejor organizado que el basado en hash, sin embargo, el basado en hash proporciona un mejor balanceo sobre el conjunto de shards.


## Referencias Bibliográficas
Sarasa, A. (2016). *Introducción a las bases de datos NoSQL usando MongoDB*.. Editorial UOC. [https://elibro.net/es/lc/biblioibero/titulos/58524]

MongoDB. (2008). *MongoDB Sharding*. Shardign [https://www.mongodb.com/docs/v4.0/sharding/]
