# NoSQL

by Andrew Brust Pluralsight
by Nuri Halperin Pluralsight

![image](https://github.com/johanalex566/NoSQL/assets/40399697/9efb343d-c8ec-496a-9b85-5b80ccc4c08f)


The big picture of NoSQL

Las bases de datos están en el corazón de la mayoría de las aplicaciones empresariales y de internet.
La de manda de escala, velocidad y rápido desarrollo de aplicaciones ha generado una nueva generación de base de datos,
denomidas NoSQL.

Introducicón mongoDB una de las bases de datos mas populares y de mayor crecimiento.


Las bases de datos relacionales guardan datos en tablas y filas. Lenguaje de consulta estructurado (SQL)
![image](https://github.com/johanalex566/NoSQL/assets/40399697/df7ae18a-f056-4f02-a7ba-84062f7a9292)

![image](https://github.com/johanalex566/NoSQL/assets/40399697/e70cbfd9-c997-480d-8938-182bc3cc51af)

Por lo tanto, cuando alguien usa el término de bases de datos "NoSQL" se refiere a bases de datos no relacionales.

En Mongo, no hay esquema para definir, no hay tablas ni relaciones entre las colecciones de objetos.
Cada documento que guarde en Mongo puede ser tan plano y simple, o tan complejo como su aplicación requiera,
Además, dos documentos en la misma colección puedn ser diferentes entre sí, ya que no hay ningún esquema que rija la colección.

![image](https://github.com/johanalex566/NoSQL/assets/40399697/74b9f398-2080-429f-952a-2580b79d7753)

El propio modelo relacional requiere un motor de base de datos relacional, para administrar los derechos de una manera muy especial.
para garantizar la coherencia y la atomicidad, debe bloquear filas y tablas y permitir solo el acceso de un escritor a la vez.
La protecicón de integridad referencial en varias tablas y filas aumenta el tiempo que el bloqueo debe estar en efecto.
Un mayor tiempo de bloqueo significa menos derechos o actualizaciones por segundo, significa una mayor latencia de las transacciones,
significa una apliacaión mas lenta.

¿Cómo almacena el motor los datos?

Mongo utiliza archivos asignados a la memoria.
El servidor no puede almacenar toda su información en la memoria, 
pero le gustaría pensar que la información solo existe y que está disponible para él en cualquier momento, lo que hace
es crear una matriz enorme y mapearla utilizando archivos mapeados en memoria.
Cada vez que llama a jugar a una parte de ese arreglo el sistema operativo se encarga de cargarlo o guardalo en el disco.

Cuando desea almacenar un poco de información la entega en el servidor, el servidor la escribe en la memoria y esa memoria se 
administra y serializa en el disco.

El mismo proceso a la inversa sucede cuando desea leer datos, el servidor intentará acceder a una parte de la matriz de bytes grande,
que se cargará según sea necesario desde el sistema operativo.

Es una muy buena idea aprovechar esta funcionalidad del sistema operativo, debido a que es una función central del sistema operativo,
ha sido altamente optimizado, es realmente rápido y estable, por lo que el servido de mongoD no tiene que ocuparse de eso.

![image](https://github.com/johanalex566/NoSQL/assets/40399697/e1037dde-00ca-46c6-b987-d24e269c2b46)



