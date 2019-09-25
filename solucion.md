### Solución ejercicio

* Obtener todos los autores
```diff
db.libros.find({},{autor:1,_id:0}).pretty()
```
* Obtener los autores cuyo apellido sea DATE
```diff
db.libros.find({"autor.apellidos": "DATE"},{"autor":1,_id:0})
```
* Obtener los libros editados en 1998 o en 2005
```diff
db.libros.find({$or: {"anyo": "1998"},{"anyo": "2005"}})
```
* Obtener el número de libros de la editorial Addison‐Wesley
```diff
db.libros.find({"editorial":"Addison‐Wesley"}).count()
```
* Obtener el libro que ocupa la tercera posición
```diff
db.libros.find().limit(1).skip(2)
```
* Obtener la lista de autores de cada libro junto con el título
```diff
db.libros.find({},{"titulo":1,"autor":1,"_id":0})
```
* Obtener los títulos de libro publicados con posterioridad a 2004.
```diff
db.libros.find("anyo":{$gt:"2004},{"titulo":1,"_id":0})
```
* Obtener los libros editados desde 2001 y precio mayor que 50
```diff
db.libros.find({$and:["anyo":{$gte:"2001"},{"precio":{$gt:50.00}}]},{"titulo":1,"_id":0})
```
* Obtener los libros publicados por la editorial Addison‐Wesley después de 2005.
```diff
db.libros.find({$and:[{"anyo":{$gt:"2005"},{"editorial": "Addison-Wesley"}}]})
```
* Obtener el título de libro y editorial para aquellos libros que tengan un precio superior a 50€.
```diff
db.libros.find({"precio":{$gt:50}},{"titulo":1,"editorial":1,"_id:0"})
```
* Obtener por cada libro, su titulo y el número de ediciones.
```diff
db.libros.aggregate([{$group:{_id:"$titulo", num_ediciones:{$sum:1}}}])
```
* Obtener los libros que tienen mas de una edición.
```diff
db.libros.aggregate([{$group:{_id:"$titulo", num_ediciones:{$sum:1}}},{$match:{"num_ediciones":{$gt:1}}}])
```
* CallBack para devolver el listado más organizado
```diff
let libros = db.libros.aggregate([{$group:{_id:"$titulo", num_ediciones:{$sum:1}}},{$match:{"num_ediciones":{$gt:1}}}])
>libros.forEach((miDoc)=>{print(`titulo:${miDoc._id} | num ediciones:$${miDoc.num_ediciones}`)})
```
