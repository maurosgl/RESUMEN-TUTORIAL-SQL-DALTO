# Resumen tutorial: SQL Desde Cero (SoyDalto)
## Contenido


## Introducción
SQL es el lenguaje fundamental que alimenta las bases de datos y facilita la transformación de simples conjuntos de datos en información valiosa. En un mundo impulsado por datos, el dominio de SQL es una habilidad imprescindible para quienes buscan tomar decisiones basadas en evidencia y construir soluciones robustas. 

Este manual te guiará paso a paso, desde los conceptos más básicos hasta las técnicas avanzadas que te permitirán dominar SQL con seguridad. Y lo haremos utilizando uno de los entornos más clásicos y completos para aprender bases de datos: Northwind, una base de datos que simula el funcionamiento de una compañía ficticia de importación y exportación.

A lo largo de esta guía, exploraremos cómo puedes utilizar SQL para consultar, analizar y manipular datos en un contexto empresarial realista. Ya seas un principiante absoluto o alguien con experiencia en SQL, este manual tiene algo para ti: Con ejemplos prácticos desarrollados paso a paso, desglosamos conceptos de manera accesible, asegurándonos de que cada lección esté conectada a un uso práctico en la vida real, ayudándote a entender cómo SQL puede potenciar tus proyectos y mejorar tu toma de decisiones.

¡Prepárate para sumergirte en el fascinante mundo del análisis y la gestión de datos con SQL!

## Desarrollo

## COMANDO AS
El comando AS en SQL se usa para asignar un alias (un nombre temporal) a una tabla o columna en una consulta. Esto hace que sea más fácil leer y referenciar los resultados.

```sql
SELECT * FirstName AS Nombre, LastName AS Apellido FROM Employees;
```

## ORDER BY ASC
El comando ORDER BY ASC en SQL se utiliza para ordenar los resultados de una consulta en orden ascendente (de menor a mayor).

```sql
SELECT * FROM Products
ORDER BY price ASC;
```

### ORDER BY DESC
El comando ORDER BY DESC en SQL se usa para ordenar los resultados de una consulta en orden descendente.

```sql
SELECT * FROM Products
ORDER BY price DESC;
```
### OPCIÓN NULL LAST
El comando NULL LAST en SQL se usa para que, al ordenar los resultados, los valores NULL aparezcan al final de la lista, independientemente de si el orden es ascendente (ASC) o descendente (DESC).

```sql
SELECT * FROM Products
ORDER BY ProductName ASC NULLS LAST;
```
### OPCIÓN NULL FIRST
El comando NULLS FIRST en SQL se utiliza para especificar que los valores NULL deben aparecer primero al ordenar los resultados de una consulta.

```sql
SELECT * FROM Products
ORDER BY ProductName DESC NULLS FIRST;
```
### ORDEN RANDOM
El comando ORDER BY RANDOM() en SQL se utiliza para ordenar los resultados de forma aleatoria. Es muy útil cuando deseas mostrar los registros en un orden no predecible, por ejemplo, al seleccionar elementos de manera aleatoria.

```sql
SELECT * FROM Products
ORDER BY RANDOM();
```

### ORDER BY TOMANDO DOS COLUMNAS
El comando ORDER BY en SQL se utiliza para ordenar los resultados de una consulta en función de una o más columnas. Cuando usas dos columnas, primero se ordenan los resultados por la primera columna y, si hay valores repetidos, se usan los valores de la segunda columna para ordenar esos registros.

```sql
SELECT * FROM Products
ORDER BY ProductName, SupplierID DESC;
```

### SELECCIONAR VALORES ÚNICOS Y ORDENADOS
El comando SELECT DISTINCT en SQL se utiliza para eliminar duplicados en los resultados de una consulta. Es decir, te permite obtener solo los valores únicos de una o más columnas.

```sql
SELECT DISTINCT ProductName FROM Products
ORDER BY ProductName ASC;
```

### WHERE
El comando WHERE en SQL se utiliza para filtrar los resultados de una consulta, especificando condiciones que deben cumplirse para que las filas sean incluidas en el resultado.

```sql
SELECT ProductName FROM Products
WHERE ProductID = 14;
```

### WHERE APLICADO A UN CRITERIO TIPO TEX
El comando WHERE en SQL se utiliza para filtrar los resultados de una consulta, especificando condiciones que deben cumplirse para que las filas sean incluidas en el resultado.

```sql
SELECT ProductName FROM Products
WHERE ProductName = "Tofu";
```

### WHERE EMPLEANDO >, <

```sql
SELECT * FROM Products
WHERE Price <= 40;
```

### BORRAR UN REGISTRO
El comando DELETE FROM en SQL se utiliza para eliminar registros de una tabla.

```sql
DELETE FROM Products
WHERE ProductID = 3;
```

### ACTUALIZAR UN REGISTRO
El comando UPDATE en SQL se emplea para modificar los registros existentes en una tabla. Permite cambiar uno o más valores de columnas en filas específicas.

```sql
UPDATE Products
SET Price = 97, ProductName = "Manzana"
WHERE ProductID = 9;
```

### AND
El operador AND en SQL se utiliza para combinar condiciones en una cláusula WHERE. Permite que una consulta devuelva resultados que cumplan todas las condiciones especificadas.

```sql
SELECT * FROM Customers
WHERE CustomerID >= 50 AND CustomerID <55;
```

### OR
El operador OR en SQL se utiliza para combinar condiciones en una cláusula WHERE. Permite que una fila cumpla al menos una de las condiciones especificadas, ampliando así el conjunto de resultados devueltos por la consulta.

```sql
SELECT * FROM Employees
WHERE FirstName = "Nancy" OR FirstName = "Anne";
```

### USAR AND Y OR SIMULTÁNEAMENTE
En SQL, los operadores OR y AND se utilizan para combinar condiciones en una consulta WHERE, permitiendo filtrar resultados basados en múltiples criterios.
Uso de AND:
•	AND se utiliza para asegurar que todas las condiciones especificadas sean verdaderas. Solo devuelve filas donde todas las condiciones se cumplen.
Uso de OR:
•	OR se usa para devolver filas donde al menos una de las condiciones es verdadera. Así, se cumplen más condiciones.

```sql
SELECT * FROM Products
WHERE (Price < 20 OR CategoryID = 6) AND SupplierID = 7;
```

### WHERE NOT
El comando WHERE NOT en SQL se utiliza para filtrar los resultados de una consulta, excluyendo aquellos registros que cumplen una determinada condición

```sql
SELECT * FROM Customers
WHERE NOT Country = 'USA';
```
