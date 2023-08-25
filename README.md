# NoSQL

by Andrew Brust Pluralsight
by Nuri Halperin Pluralsight

![image](https://github.com/johanalex566/NoSQL/assets/40399697/9efb343d-c8ec-496a-9b85-5b80ccc4c08f)


The big picture of NoSQL

Las bases de datos están en el corazón de la mayoría de las aplicaciones empresariales y de internet.
La de manda de escala, velocidad y rápido desarrollo de aplicaciones ha generado una nueva generación de base de datos,
denomidas NoSQL.

Introducicón mongoDB una de las bases de datos mas populares y de mayor crecimiento.


Las bases de datos relacionales guardan datos en tablas y filas
![image](https://github.com/johanalex566/NoSQL/assets/40399697/df7ae18a-f056-4f02-a7ba-84062f7a9292)

![image](https://github.com/johanalex566/NoSQL/assets/40399697/e70cbfd9-c997-480d-8938-182bc3cc51af)

En Mongo, no hay esquema para definir, no hay tablas ni relaciones entre las colecciones de objetos.
Cada documento que guarde en Mongo puede ser tan plano y simple, o tan complejo como su aplicación requiera,
Además, dos documentos en la misma colecicón puedn ser diferentes entre sí, ya que no hay ning+un esquema e rija la colección.

![image](https://github.com/johanalex566/NoSQL/assets/40399697/74b9f398-2080-429f-952a-2580b79d7753)

El propio modelo relacional requiere un motor de base de datos relacional, para administrar los derechos de una manera muy especial.
para garantizar la coherencia y la atomicidad, debe bloquear filas y tablas y permitir solo el acceso de un escritor a la vez.
La protecicón de integridad referencial en varias tablas y filas aumenta el tiempo que el bloqueo debe estar en efecto.
Un mayor tiempo de bloqueo significa menos derechos o actualizaciones por segundo, significa una mayor latencia de las transacciones,
significa una apliacaión mas lenta.

