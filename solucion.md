### Solución ejercicio

* Obtener todos los autores
```diff
+db.libros.find({},{autor:1,_id:0}).pretty()
```
* Obtener los autores cuyo apellido sea DATE
```diff
+db.libros.find({"autor.apellidos": "DATE"})
```
* Obtener los libros editados en 1998 o en 2005
```diff
-db.libros.find({$or: {"anyo": {$eq: "1998"},{"anyo": {$eq: "2005"}}}})
```
* Obtener el número de libros de la editorial Addison‐Wesley
```diff

```
* Obtener el libro que ocupa la tercera posición
```diff
```
* Obtener la lista de autores de cada libro junto con el título
```diff
```
* Obtener los títulos de libro publicados con posterioridad a 2004.
* Obtener los libros editados desde 2001 y precio mayor que 50
* Obtener los libros publicados por la editorial Addison‐Wesley después de 2005.
* Obtener el título de libro y editorial para aquellos libros que tengan un precio superior a 50€.
* Obtener los libros publicados en 1998 o a partir de 2005.
