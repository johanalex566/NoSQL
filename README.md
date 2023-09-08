# NoSQL



![image](https://github.com/johanalex566/NoSQL/assets/40399697/9efb343d-c8ec-496a-9b85-5b80ccc4c08f)


The big picture of NoSQL

Las bases de datos están en el corazón de la mayoría de las aplicaciones empresariales y de internet.
La de manda de escala, velocidad y rápido desarrollo de aplicaciones ha generado una nueva generación de base de datos,
denomidas NoSQL.

**Introducicón mongoDB**


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

**¿Cómo almacena el motor los datos?**

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

**En que formato se guardan los datos?**

**BSON**

BSON significa "JSON binario". La estructura binaria de BSON codifica información de tipo y longitud, lo que permite que se recorra mucho más rápidamente en comparación con JSON.

BSON agrega algunos tipos de datos no nativos de JSON, como fechas y datos binarios, sin los cuales MongoDB habría perdido un soporte valioso.
A continuación se muestran algunos objetos JSON de ejemplo y sus correspondientes representaciones BSON.

![image](https://github.com/johanalex566/NoSQL/assets/40399697/ba087095-0bba-42a0-9977-6a901dbec3e5)

A diferencia de los sistemas que almacenan JSON como valores codificados en cadena o blobs codificados en binario, MongoDB usa BSON para ofrecer potentes funciones de indexación y consulta sobre el formato de datos más popular de la web.

**Collections**

Una colección en Mongo define el alcance de la interacción con los documentos, en este la colección sería una tabla en SQL server por ejemplo y así mismo los documentos un registro.
Debido a que Mongo no es una base de datos tradicional no puedo emitir comandos a través de varias coleeciones algo que si podría hacer en SQL server con una relación de JOIN por ejemplo.

![image](https://github.com/johanalex566/NoSQL/assets/40399697/f4de80b9-2ae5-4844-9558-35b782385562)

La única restricción a la hora de guardar un documento es agregarle un _id, el cuál solo podrá ser de los siguientes tipos de datos:

En caso de no asignar el Id, Mongo lo creara por defecto
![image](https://github.com/johanalex566/NoSQL/assets/40399697/477429cc-eaea-4a04-a99b-ad7593a29fe4)

ObjectId, el cuál tiene varias propiedades una de ellas es que cada id tiene una propiedad que indica la fecha de creación, por lo que no es necesario una propieda adicional que almacene una fecha de creación.

![image](https://github.com/johanalex566/NoSQL/assets/40399697/c5b0db6a-119b-4d26-97ca-10a0acc45ba4)

**Querys**

*INSERT*

insertMany
db.animals.insertMany([{_id:1,Name:"Tigre",Age:0},{_id:2, Name:"Oso", Age:1},{_id:3, Name: "Jirafa",Age:4},{_id:4,Name:"Lobo",Age:2}])

**UPDATE**
![image](https://github.com/johanalex566/NoSQL/assets/40399697/2d1e222b-0d6b-4f8e-ae16-0bc37fb4d376)

**db.food.updateOne({_id:2},{$inc:{x:1}})**

Add new value
**db.food.updateOne({_id:2},{$set:{y:8}})**

Remove value
 **db.food.updateOne({_id:2}, {$unset:{y:''}})**

Rename column name
**db.food.updateOne({_id:4}, {$rename:{'Naem': 'Name'}})**

Update add array
*db.food.updateOne({_id:4},{$push:{things:['One','two']}})**

Update add new item only if no exists
**db.food.updateOne({_id:4},{$addToSet:{things:['One','two','three']}})**

Remove item of array
**db.food.updateOne({_id:4},{$pull: { things: ['One','two'] }})**

FindAndModifiy
**db.food.findAndModify({ "query": { "things": 1 }, "update": { "$set": {"touched": true  }}, "sort": {"_id": 1},"new": true})**
El campo "sort" específica que elemento se va actualizar 1: primer elemento de la lista o -1 el último.
El campo "new" específica si el valor será retornado con el cambio de cambio.

**FIND**

**db.animals.find()**

$get: mayor que:
**db.animals.find({Age: {$gt:2}})**

$lt: Menor que:
**db.animals.find({Age: {$lt:2}})**

$lte: Menor o igual:
**db.animals.find({Age: {$lte:1}})**

$gte: mayor o igual:
**db.animals.find({Age: {$gte:1}})**

Rango mayor y menor que:
**db.animals.find({Age: {$gt:1, $lt:4}})**

campos que coincidan con 1 o 3:
**db.animals.find({ Age: {$in:[1,3]} })**

campos que no coincidan con 1 o 3:
**db.animals.find({ Age: {$nin:[1,3]} })**

by 
 Andrew Brust Pluralsight -
 Nuri Halperin Pluralsight

https://www.mongodb.com/json-and-bson
https://app.pluralsight.com/course-player?clipId=23c8b62c-c5b1-404b-bc5d-57d5dbb5ec03
